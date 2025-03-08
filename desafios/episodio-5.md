# Episodio 5: Profundizando en los Triggers

## Desafío

Crea un workflow que use un trigger de "Webhook" para recibir datos de un formulario simple. Configura el webhook para aceptar datos POST y prueba enviando datos desde una herramienta como Postman o curl (por ejemplo, {"nombre": "Ana"}). Muestra cómo los datos recibidos aparecen en n8n.

## Instrucciones

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Receptor de Webhook".

### Paso 2: Configurar el nodo "Webhook"

1. Añade un nodo "Webhook" al canvas.
2. Configura el nodo con los siguientes parámetros:
   - Authentication: `None`
   - HTTP Method: `POST`
   - Path: `webhook` (o cualquier otro nombre que prefieras)
   - Response Mode: `Last Node`
   - Response Code: `200`
   - Response Data: `All Entries`
3. Haz clic en "Save" para guardar la configuración.
4. Observa la URL del webhook que se genera (algo como `http://localhost:5678/webhook/[ID]`). Cópiala, la necesitarás para enviar datos al webhook.

### Paso 3: Añadir un nodo "Set" para procesar los datos

1. Añade un nodo "Set" después del nodo "Webhook".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el campo con:
   - Name: `respuesta`
   - Type: `String`
   - Value: `Hola, {{$json.body.nombre}}! Hemos recibido tu solicitud.`
4. Guarda la configuración del nodo.

### Paso 4: Probar el webhook con curl o Postman

#### Opción 1: Usando curl

Abre una terminal y ejecuta el siguiente comando, reemplazando la URL con la de tu webhook:

```bash
curl -X POST -H "Content-Type: application/json" -d '{"nombre":"Ana"}' http://localhost:5678/webhook/[ID]
```

#### Opción 2: Usando Postman

1. Abre Postman y crea una nueva solicitud.
2. Configura la solicitud:
   - Método: `POST`
   - URL: La URL de tu webhook
   - Headers: Añade `Content-Type: application/json`
   - Body: Selecciona "raw" y "JSON", luego ingresa `{"nombre":"Ana"}`
3. Haz clic en "Send" para enviar la solicitud.

### Paso 5: Verificar los resultados

1. Después de enviar la solicitud, verás que el workflow se activa automáticamente.
2. Haz clic en el nodo "Webhook" para ver los datos recibidos.
3. Haz clic en el nodo "Set" para ver cómo se procesaron los datos.
4. En la respuesta de tu solicitud (en curl o Postman), deberías ver el mensaje personalizado: `Hola, Ana! Hemos recibido tu solicitud.`

## Entrega

Para completar este desafío, debes:

1. Adjuntar una captura de pantalla del canvas con los nodos conectados.
2. Adjuntar una captura de pantalla de los datos recibidos en el nodo "Webhook".
3. Adjuntar una captura de pantalla de la respuesta recibida en curl o Postman.
4. Responder a las siguientes preguntas:
   - ¿Qué ventajas ofrece usar webhooks como triggers en comparación con triggers manuales?
   - ¿Qué tipos de aplicaciones podrías construir utilizando webhooks?
   - ¿Cómo podrías mejorar la seguridad de tu webhook?

## Conceptos clave

- **Webhook**: Un método para que una aplicación proporcione información en tiempo real a otras aplicaciones cuando ocurre un evento.
- **Trigger automático**: Cómo los workflows pueden iniciarse automáticamente en respuesta a eventos externos.
- **Procesamiento de datos JSON**: Cómo acceder y manipular datos JSON recibidos a través de un webhook.
- **Respuestas personalizadas**: Cómo configurar respuestas personalizadas para las solicitudes recibidas.

## Recursos adicionales

- [Documentación del nodo Webhook](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.webhook/)
- [Guía de Postman](https://learning.postman.com/docs/getting-started/introduction/)
- [Guía de curl](https://curl.se/docs/manpage.html) 