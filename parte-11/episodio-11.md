# Episodio 11: Nodos de IA 2: Agentes, Intro Memoria, Intro Herramientas

## Desafío

Configura un agente que use una herramienta de cálculo para resolver un problema matemático simple, como "cuánto es 15% de 200". Muestra cómo el agente procesa la solicitud y devuelve la respuesta correcta (30).

## Instrucciones

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Agente Matemático".

### Paso 2: Configurar el nodo "Manual Trigger"

1. Añade un nodo "Manual Trigger" al canvas.
2. No es necesario configurar nada en este nodo, ya que simplemente iniciará el workflow manualmente.

### Paso 3: Configurar el nodo "Set" para la pregunta

1. Añade un nodo "Set" después del "Manual Trigger".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el campo con:
   - Name: `pregunta`
   - Type: `String`
   - Value: `¿Cuánto es el 15% de 200?`
4. Guarda la configuración del nodo.

### Paso 4: Configurar el nodo "Agent"

1. Añade un nodo "Agent" después del nodo "Set".
2. Configura el nodo con los siguientes parámetros:
   - LLM Provider: `OpenAI` (o el proveedor que tengas disponible)
   - API Key: Ingresa tu API key para el proveedor seleccionado
   - Model: Selecciona un modelo adecuado (por ejemplo, `gpt-3.5-turbo`)
   - Agent Type: `Structured Chat`
   - System Message: `Eres un asistente matemático que ayuda a resolver problemas de cálculo. Utiliza la herramienta de calculadora cuando sea necesario para realizar operaciones matemáticas.`
   - Human Message: `{{$json.pregunta}}`
   - Output Field Name: `respuesta`
3. En la sección "Tools", habilita la herramienta "Calculator" para que el agente pueda realizar cálculos.
4. Guarda la configuración del nodo.

### Paso 5: Configurar el nodo "Log" para mostrar la respuesta

1. Añade un nodo "Log" después del nodo "Agent".
2. En la configuración del nodo "Log", configura los siguientes parámetros:
   - Log Level: `Info`
   - Log Message: `Respuesta del agente: {{$json.respuesta}}`
3. Guarda la configuración del nodo.

### Paso 6: Ejecutar y verificar el workflow

1. Haz clic en "Execute Workflow" para ejecutar el workflow.
2. Una vez completada la ejecución, haz clic en el nodo "Agent" para ver cómo el agente procesó la solicitud y utilizó la herramienta de calculadora.
3. Verifica que el nodo "Log" muestre la respuesta correcta (30).

## Entrega

Para completar este desafío, debes:

1. Adjuntar una captura de pantalla del canvas con todos los nodos conectados.
2. Adjuntar una captura de pantalla de la salida del nodo "Agent" mostrando el proceso de razonamiento y el uso de la herramienta de calculadora.
3. Adjuntar una captura de pantalla del mensaje del nodo "Log" mostrando la respuesta final.
4. Responder a las siguientes preguntas:
   - ¿Qué otras herramientas podrías habilitar para el agente?
   - ¿Cómo podrías modificar este workflow para resolver problemas matemáticos más complejos?
   - ¿Qué ventajas ofrece usar un agente en comparación con un simple LLM Chain?

## Conceptos clave

- **Agentes de IA**: Qué son y cómo funcionan los agentes autónomos basados en IA.
- **Herramientas para agentes**: Cómo los agentes pueden utilizar herramientas para realizar tareas específicas.
- **Razonamiento paso a paso**: Cómo los agentes descomponen problemas complejos en pasos más simples.
- **Integración de capacidades de cálculo**: Cómo incorporar funcionalidades matemáticas en tus agentes.

## Recursos adicionales

- [Documentación de n8n sobre nodos de Agente](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/)
- [Guía de herramientas para agentes en LangChain](https://js.langchain.com/docs/modules/agents/tools/)
- [Patrones de diseño para agentes de IA](https://www.langchain.com/blog/agent-patterns)
- [Mejores prácticas para trabajar con agentes](https://docs.n8n.io/integrations/ai/agents/) 