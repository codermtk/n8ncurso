# Desafío del Episodio 4

## Desafío

Construye un workflow que use un "Manual Trigger" y un nodo "Set" para crear un objeto JSON con tu nombre y edad (por ejemplo, {"nombre": "Juan", "edad": 25}). Luego, añade un nodo "HTTP Request" que envíe este objeto a una URL de prueba como https://httpbin.org/post. Ejecuta el workflow y muestra el resultado en la vista JSON.

## Instrucciones

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Envío de Datos HTTP".

### Paso 2: Configurar el nodo "Manual Trigger"

1. Añade un nodo "Manual Trigger" al canvas.
2. No es necesario configurar nada en este nodo, ya que simplemente iniciará el workflow manualmente.

### Paso 3: Configurar el nodo "Set"

1. Añade un nodo "Set" después del "Manual Trigger".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el primer campo con:
   - Name: `nombre`
   - Type: `String`
   - Value: `[Tu nombre]` (reemplaza con tu nombre real)
4. Haz clic en "Add Value" nuevamente para añadir otro campo.
5. Configura el segundo campo con:
   - Name: `edad`
   - Type: `Number`
   - Value: `[Tu edad]` (reemplaza con tu edad real)
6. Guarda la configuración del nodo.

### Paso 4: Configurar el nodo "HTTP Request"

1. Añade un nodo "HTTP Request" después del nodo "Set".
2. Configura el nodo con los siguientes parámetros:
   - Method: `POST`
   - URL: `https://httpbin.org/post`
   - Authentication: `None`
   - Headers: Deja los valores predeterminados
   - Query Parameters: Deja en blanco
   - Body Content Type: `JSON`
   - Specify Body: `Automatically`
   - Send Binary Data: Desactivado
   - Response Format: `JSON`
3. Guarda la configuración del nodo.

### Paso 5: Ejecutar y verificar el workflow

1. Haz clic en "Execute Workflow" para ejecutar el workflow.
2. Una vez completada la ejecución, haz clic en el nodo "HTTP Request" para ver la respuesta.
3. En la pestaña "Output", podrás ver la respuesta del servidor, que incluirá los datos que enviaste en el campo "json".

## Entrega

Para completar este desafío, debes:

1. Adjuntar una captura de pantalla del canvas con los tres nodos conectados.
2. Adjuntar una captura de pantalla de la salida JSON del nodo "HTTP Request" después de ejecutar el workflow.
3. Responder a las siguientes preguntas:
   - ¿Qué información devuelve el servidor httpbin.org en su respuesta?
   - ¿Cómo se transmiten los datos del nodo "Set" al nodo "HTTP Request"?
   - ¿Qué sucedería si cambiaras el método HTTP de POST a GET?

## Conceptos clave

- **JSON (JavaScript Object Notation)**: Un formato ligero de intercambio de datos.
- **HTTP Request**: Una solicitud enviada a un servidor web utilizando el protocolo HTTP.
- **Métodos HTTP**: Diferentes tipos de solicitudes HTTP (GET, POST, PUT, DELETE, etc.) que indican la acción que se desea realizar.
- **Flujo de datos en n8n**: Cómo los datos se pasan de un nodo a otro en un workflow.

## Recursos adicionales

- [Documentación del nodo HTTP Request](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/)
- [Introducción a las API REST](https://www.redhat.com/es/topics/api/what-is-a-rest-api)
- [Guía de JSON](https://www.json.org/json-es.html) 
