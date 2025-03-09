# Episodio 6: Profundizando en nodos de Data

## Desafío

Diseña un workflow que use un nodo "Set" para crear un array de números del 1 al 10 (por ejemplo, [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]). Luego, usa un nodo "Summarize" para calcular la suma de estos números. Añade un nodo "Log" para mostrar el resultado en la consola.

## Instrucciones

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Procesamiento de Datos".

### Paso 2: Configurar el nodo "Manual Trigger"

1. Añade un nodo "Manual Trigger" al canvas.
2. No es necesario configurar nada en este nodo, ya que simplemente iniciará el workflow manualmente.

### Paso 3: Configurar el nodo "Set" para crear el array

1. Añade un nodo "Set" después del "Manual Trigger".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el campo con:
   - Name: `numeros`
   - Type: `Array`
   - Value: `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`
4. Guarda la configuración del nodo.

### Paso 4: Configurar el nodo "Summarize"

1. Añade un nodo "Summarize" después del nodo "Set".
2. En la configuración del nodo "Summarize", configura los siguientes parámetros:
   - Field to Summarize: `numeros`
   - Operations: Selecciona `Sum`
   - Output Field Name: `suma`
3. Guarda la configuración del nodo.

### Paso 5: Configurar el nodo "Log"

1. Añade un nodo "Log" después del nodo "Summarize".
2. En la configuración del nodo "Log", configura los siguientes parámetros:
   - Log Level: `Info`
   - Log Message: `La suma de los números del 1 al 10 es: {{$json.suma}}`
3. Guarda la configuración del nodo.

### Paso 6: Ejecutar y verificar el workflow

1. Haz clic en "Execute Workflow" para ejecutar el workflow.
2. Una vez completada la ejecución, haz clic en cada nodo para ver cómo se transforman los datos a lo largo del workflow.
3. Verifica que el nodo "Log" muestre el mensaje con la suma correcta (55).

## Entrega

Para completar este desafío, debes:

1. Adjuntar una captura de pantalla del canvas con todos los nodos conectados.
2. Adjuntar una captura de pantalla de la salida del nodo "Summarize".
3. Adjuntar una captura de pantalla del mensaje del nodo "Log".
4. Responder a las siguientes preguntas:
   - ¿Qué otras operaciones puedes realizar con el nodo "Summarize"?
   - ¿Cómo podrías modificar este workflow para calcular también el promedio de los números?
   - ¿Qué otros nodos de procesamiento de datos ofrece n8n que podrían ser útiles para manipular arrays?

## Conceptos clave

- **Arrays en n8n**: Cómo crear y manipular arrays de datos.
- **Nodo Summarize**: Cómo realizar operaciones de resumen en conjuntos de datos.
- **Nodo Log**: Cómo registrar información durante la ejecución de un workflow.
- **Transformación de datos**: Cómo los datos se transforman a medida que pasan por diferentes nodos.

## Recursos adicionales

- [Documentación del nodo Summarize](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.summarize/)
- [Documentación del nodo Log](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.log/)
- [Guía de manipulación de datos en n8n](https://docs.n8n.io/data/) 