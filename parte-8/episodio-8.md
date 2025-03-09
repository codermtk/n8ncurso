# Episodio 8: Nodos Core

## Desafío

Construye un workflow que use un nodo "HTTP Request" para obtener datos de una API pública como https://jsonplaceholder.typicode.com/posts. Luego, usa un nodo "Set" para extraer el título del primer post y muéstralo en un nodo "Log".

## Instrucciones

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Consumo de API".

### Paso 2: Configurar el nodo "Manual Trigger"

1. Añade un nodo "Manual Trigger" al canvas.
2. No es necesario configurar nada en este nodo, ya que simplemente iniciará el workflow manualmente.

### Paso 3: Configurar el nodo "HTTP Request"

1. Añade un nodo "HTTP Request" después del "Manual Trigger".
2. Configura el nodo con los siguientes parámetros:
   - Method: `GET`
   - URL: `https://jsonplaceholder.typicode.com/posts`
   - Authentication: `None`
   - Headers: Deja los valores predeterminados
   - Query Parameters: Deja en blanco
   - Response Format: `JSON`
3. Guarda la configuración del nodo.

### Paso 4: Configurar el nodo "Set" para extraer el título

1. Añade un nodo "Set" después del nodo "HTTP Request".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el campo con:
   - Name: `titulo_primer_post`
   - Type: `String`
   - Value: `{{$json[0].title}}`
4. Guarda la configuración del nodo.

### Paso 5: Configurar el nodo "Log"

1. Añade un nodo "Log" después del nodo "Set".
2. En la configuración del nodo "Log", configura los siguientes parámetros:
   - Log Level: `Info`
   - Log Message: `El título del primer post es: {{$json.titulo_primer_post}}`
3. Guarda la configuración del nodo.

### Paso 6: Ejecutar y verificar el workflow

1. Haz clic en "Execute Workflow" para ejecutar el workflow.
2. Una vez completada la ejecución, haz clic en cada nodo para ver cómo se transforman los datos a lo largo del workflow.
3. Verifica que el nodo "Log" muestre el título del primer post correctamente.

## Entrega

Para completar este desafío, debes:

1. Adjuntar una captura de pantalla del canvas con todos los nodos conectados.
2. Adjuntar una captura de pantalla de la respuesta del nodo "HTTP Request" mostrando los datos obtenidos.
3. Adjuntar una captura de pantalla del mensaje del nodo "Log" mostrando el título extraído.
4. Responder a las siguientes preguntas:
   - ¿Qué otros métodos HTTP podrías utilizar con el nodo "HTTP Request"?
   - ¿Cómo podrías modificar este workflow para obtener y mostrar los títulos de los primeros 5 posts?
   - ¿Qué otras APIs públicas podrías utilizar con este tipo de workflow?

## Conceptos clave

- **APIs REST**: Cómo consumir datos de APIs externas.
- **Nodo HTTP Request**: Cómo realizar solicitudes HTTP desde n8n.
- **Manipulación de respuestas JSON**: Cómo extraer y procesar datos de respuestas JSON.
- **Acceso a propiedades anidadas**: Cómo acceder a propiedades específicas dentro de objetos JSON.

## Recursos adicionales

- [Documentación del nodo HTTP Request](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/)
- [JSONPlaceholder - API de prueba gratuita](https://jsonplaceholder.typicode.com/)
- [Lista de APIs públicas](https://github.com/public-apis/public-apis)
- [Guía de expresiones en n8n](https://docs.n8n.io/code-examples/expressions/) 