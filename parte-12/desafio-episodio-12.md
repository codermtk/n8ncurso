# Desafío del Episodio 12

## Desafío

Implementa un sistema RAG simple donde cargues un pequeño conjunto de documentos de texto (por ejemplo, dos o tres párrafos sobre "energía renovable") en una Vector Store. Luego, usa un nodo de consulta para hacer una pregunta como "¿Qué es la energía solar?" y muestra la respuesta generada.

## Instrucciones

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Sistema RAG de Energía Renovable".

### Paso 2: Configurar el nodo "Manual Trigger"

1. Añade un nodo "Manual Trigger" al canvas.
2. No es necesario configurar nada en este nodo, ya que simplemente iniciará el workflow manualmente.

### Paso 3: Configurar el nodo "Set" para los documentos

1. Añade un nodo "Set" después del "Manual Trigger".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el campo con:
   - Name: `documentos`
   - Type: `Array`
   - Value: 
   ```json
   [
     {
       "texto": "La energía solar es una fuente de energía renovable que se obtiene del sol. Esta energía se puede aprovechar de dos formas principales: la energía solar fotovoltaica, que convierte directamente la luz solar en electricidad mediante paneles solares, y la energía solar térmica, que utiliza el calor del sol para calentar un fluido que posteriormente se utiliza para generar electricidad o para aplicaciones de calefacción. La energía solar es abundante, inagotable y no contamina, lo que la convierte en una alternativa sostenible a los combustibles fósiles."
     },
     {
       "texto": "La energía eólica es una forma de energía renovable que aprovecha la fuerza del viento para generar electricidad. Utiliza aerogeneradores o turbinas eólicas que convierten la energía cinética del viento en energía mecánica y, posteriormente, en energía eléctrica. Los parques eólicos pueden instalarse tanto en tierra firme como en el mar (offshore). La energía eólica es limpia, no produce emisiones durante su operación y ha experimentado un gran desarrollo tecnológico en las últimas décadas, lo que ha reducido significativamente sus costos."
     },
     {
       "texto": "La energía hidroeléctrica es una fuente de energía renovable que aprovecha la energía del agua en movimiento para generar electricidad. Las centrales hidroeléctricas utilizan la fuerza del agua que cae desde cierta altura para mover turbinas conectadas a generadores eléctricos. Esta forma de energía es una de las más antiguas y desarrolladas entre las renovables, y proporciona una parte significativa de la electricidad mundial. Aunque no emite contaminantes durante su operación, la construcción de grandes presas puede tener impactos ambientales y sociales importantes."
     }
   ]
   ```
4. Guarda la configuración del nodo.

### Paso 4: Configurar el nodo "Document Loader"

1. Añade un nodo "Document Loader" después del nodo "Set".
2. Configura el nodo con los siguientes parámetros:
   - Loader Type: `JSON`
   - JSON: `{{$json.documentos}}`
   - JSON Pointer: `texto`
   - Metadata: Deja en blanco
   - Output Field Name: `documentos_cargados`
3. Guarda la configuración del nodo.

### Paso 5: Configurar el nodo "Text Splitter"

1. Añade un nodo "Text Splitter" después del nodo "Document Loader".
2. Configura el nodo con los siguientes parámetros:
   - Documents: `{{$json.documentos_cargados}}`
   - Splitter Type: `Character`
   - Chunk Size: `1000`
   - Chunk Overlap: `200`
   - Output Field Name: `documentos_divididos`
3. Guarda la configuración del nodo.

### Paso 6: Configurar el nodo "Vector Store"

1. Añade un nodo "Vector Store" después del nodo "Text Splitter".
2. Configura el nodo con los siguientes parámetros:
   - Operation: `Create and Store`
   - Vector Store Type: `In-Memory` (para este ejemplo simple)
   - Documents: `{{$json.documentos_divididos}}`
   - Embeddings Provider: `OpenAI` (o el proveedor que tengas disponible)
   - API Key: Ingresa tu API key para el proveedor seleccionado
   - Output Field Name: `vector_store`
3. Guarda la configuración del nodo.

### Paso 7: Configurar el nodo "Set" para la pregunta

1. Añade un nodo "Set" después del nodo "Vector Store".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el campo con:
   - Name: `pregunta`
   - Type: `String`
   - Value: `¿Qué es la energía solar?`
4. Guarda la configuración del nodo.

### Paso 8: Configurar el nodo "Retrieval QA Chain"

1. Añade un nodo "Retrieval QA Chain" después del nodo "Set" para la pregunta.
2. Configura el nodo con los siguientes parámetros:
   - LLM Provider: `OpenAI` (o el proveedor que tengas disponible)
   - API Key: Ingresa tu API key para el proveedor seleccionado
   - Model: Selecciona un modelo adecuado (por ejemplo, `gpt-3.5-turbo`)
   - Vector Store: `{{$json.vector_store}}`
   - Question: `{{$json.pregunta}}`
   - Chain Type: `Stuff`
   - Output Field Name: `respuesta`
3. Guarda la configuración del nodo.

### Paso 9: Configurar el nodo "Log" para mostrar la respuesta

1. Añade un nodo "Log" después del nodo "Retrieval QA Chain".
2. En la configuración del nodo "Log", configura los siguientes parámetros:
   - Log Level: `Info`
