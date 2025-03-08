# Episodio 10: Nodos de IA 1: Intro y Chains

## Desafío

Crea una chain simple usando un nodo "LLM Chain" con un modelo de lenguaje para generar un resumen de un texto corto que tú proporciones. Por ejemplo, usa un párrafo sobre "el cambio climático" y pide al modelo que lo resuma en una frase.

## Instrucciones

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Resumen con IA".

### Paso 2: Configurar el nodo "Manual Trigger"

1. Añade un nodo "Manual Trigger" al canvas.
2. No es necesario configurar nada en este nodo, ya que simplemente iniciará el workflow manualmente.

### Paso 3: Configurar el nodo "Set" para el texto a resumir

1. Añade un nodo "Set" después del "Manual Trigger".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el campo con:
   - Name: `texto`
   - Type: `String`
   - Value: `El cambio climático es uno de los mayores desafíos que enfrenta la humanidad en el siglo XXI. Se refiere a la variación global del clima de la Tierra debido a causas naturales y principalmente a la acción humana. Este fenómeno se manifiesta en un aumento de la temperatura media del planeta, lo que provoca alteraciones en los patrones climáticos, como el aumento del nivel del mar, la intensificación de fenómenos meteorológicos extremos, y cambios en los ecosistemas. Las principales causas del cambio climático antropogénico son la emisión de gases de efecto invernadero, la deforestación y la industrialización.`
4. Guarda la configuración del nodo.

### Paso 4: Configurar el nodo "LLM Chain"

1. Añade un nodo "LLM Chain" después del nodo "Set".
2. Configura el nodo con los siguientes parámetros:
   - LLM Provider: `OpenAI` (o el proveedor que tengas disponible)
   - API Key: Ingresa tu API key para el proveedor seleccionado
   - Model: Selecciona un modelo adecuado (por ejemplo, `gpt-3.5-turbo`)
   - Prompt: `Resumir el siguiente texto en una sola frase: {{$json.texto}}`
   - Output Field Name: `resumen`
3. Guarda la configuración del nodo.

### Paso 5: Configurar el nodo "Log" para mostrar el resumen

1. Añade un nodo "Log" después del nodo "LLM Chain".
2. En la configuración del nodo "Log", configura los siguientes parámetros:
   - Log Level: `Info`
   - Log Message: `Resumen: {{$json.resumen}}`
3. Guarda la configuración del nodo.

### Paso 6: Ejecutar y verificar el workflow

1. Haz clic en "Execute Workflow" para ejecutar el workflow.
2. Una vez completada la ejecución, haz clic en el nodo "LLM Chain" para ver la respuesta generada por el modelo.
3. Verifica que el nodo "Log" muestre el resumen generado.

## Entrega

Para completar este desafío, debes:

1. Adjuntar una captura de pantalla del canvas con todos los nodos conectados.
2. Adjuntar una captura de pantalla de la salida del nodo "LLM Chain" mostrando el resumen generado.
3. Responder a las siguientes preguntas:
   - ¿Qué otros proveedores de LLM podrías utilizar en n8n?
   - ¿Cómo podrías modificar este workflow para generar resúmenes de diferentes longitudes?
   - ¿Qué otras tareas de procesamiento de lenguaje natural podrías realizar con un nodo "LLM Chain"?

## Conceptos clave

- **Modelos de Lenguaje (LLM)**: Qué son y cómo funcionan los modelos de lenguaje de gran escala.
- **Chains**: Cómo crear secuencias de operaciones con modelos de IA.
- **Prompts**: Cómo diseñar instrucciones efectivas para los modelos de lenguaje.
- **Integración de IA en workflows**: Cómo incorporar capacidades de IA en tus automatizaciones.

## Recursos adicionales

- [Documentación de n8n sobre nodos de IA](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.llmchain/)
- [Guía de prompting para modelos de lenguaje](https://www.promptingguide.ai/)
- [Documentación de OpenAI](https://platform.openai.com/docs/introduction)
- [Introducción a LangChain](https://docs.langchain.com/docs/) 