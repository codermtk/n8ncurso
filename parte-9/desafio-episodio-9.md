# Desafío del Episodio 9

## Desafío

Desarrolla un workflow que combine varios conceptos aprendidos: usa un trigger de "Schedule" para ejecutarse cada hora, obtén datos de una API pública (como el clima actual en https://wttr.in/?format=j1), procesa los datos para extraer la temperatura y usa un nodo "If" para mostrar un mensaje en un nodo "Log" si la temperatura es mayor a 30 grados (por ejemplo, "¡Hace calor!").

## Instrucciones

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Monitor de Temperatura".

### Paso 2: Configurar el nodo "Schedule Trigger"

1. Añade un nodo "Schedule Trigger" al canvas.
2. Configura el nodo para que se ejecute cada hora:
   - Mode: `Basic`
   - Interval: `Every Hour`
3. Guarda la configuración del nodo.

### Paso 3: Configurar el nodo "HTTP Request" para obtener datos del clima

1. Añade un nodo "HTTP Request" después del "Schedule Trigger".
2. Configura el nodo con los siguientes parámetros:
   - Method: `GET`
   - URL: `https://wttr.in/?format=j1`
   - Authentication: `None`
   - Headers: Deja los valores predeterminados
   - Query Parameters: Deja en blanco
   - Response Format: `JSON`
3. Guarda la configuración del nodo.

### Paso 4: Configurar el nodo "Set" para extraer la temperatura

1. Añade un nodo "Set" después del nodo "HTTP Request".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el campo con:
   - Name: `temperatura`
   - Type: `Number`
   - Value: `{{$json.current_condition[0].temp_C}}`
4. Guarda la configuración del nodo.

### Paso 5: Configurar el nodo "If" para evaluar la temperatura

1. Añade un nodo "If" después del nodo "Set".
2. En la configuración del nodo "If", configura los siguientes parámetros:
   - Value 1: `{{$json.temperatura}}`
   - Operation: `Larger`
   - Value 2: `30`
3. Guarda la configuración del nodo.

### Paso 6: Configurar los nodos "Log" para las respuestas

1. Añade un nodo "Log" conectado a la salida "true" del nodo "If".
2. Configura este nodo con:
   - Log Level: `Info`
   - Log Message: `¡Hace calor! La temperatura actual es de {{$json.temperatura}}°C.`
3. Guarda la configuración del nodo.

4. Añade otro nodo "Log" conectado a la salida "false" del nodo "If".
5. Configura este nodo con:
   - Log Level: `Info`
   - Log Message: `Temperatura agradable. Actualmente hace {{$json.temperatura}}°C.`
6. Guarda la configuración del nodo.

### Paso 7: Ejecutar y verificar el workflow

1. Haz clic en "Execute Workflow" para ejecutar el workflow manualmente (sin esperar a la programación).
2. Una vez completada la ejecución, verifica qué camino ha tomado el flujo de datos según la temperatura actual.
3. Observa el mensaje en el nodo "Log" correspondiente.

## Entrega

Para completar este desafío, debes:

1. Adjuntar una captura de pantalla del canvas con todos los nodos conectados.
2. Adjuntar una captura de pantalla de la respuesta del nodo "HTTP Request" mostrando los datos del clima.
3. Adjuntar una captura de pantalla del mensaje del nodo "Log" que se activó según la temperatura.
4. Responder a las siguientes preguntas:
   - ¿Qué otras programaciones podrías configurar con el nodo "Schedule Trigger"?
   - ¿Cómo podrías modificar este workflow para enviar una notificación por correo electrónico cuando la temperatura supere los 30 grados?
   - ¿Qué otros datos del clima podrías extraer y utilizar en este workflow?

## Conceptos clave

- **Automatización programada**: Cómo ejecutar workflows automáticamente según un horario.
- **Integración de múltiples nodos**: Cómo combinar diferentes tipos de nodos para crear workflows complejos.
- **Procesamiento condicional**: Cómo tomar decisiones basadas en datos externos.
- **Monitoreo de datos**: Cómo crear sistemas de monitoreo automatizados.

## Recursos adicionales

- [Documentación del nodo Schedule](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.schedule/)
- [API de clima wttr.in](https://github.com/chubin/wttr.in)
- [Guía de expresiones en n8n](https://docs.n8n.io/code-examples/expressions/)
- [Patrones de automatización comunes](https://docs.n8n.io/workflows/best-practices/) 
