# Desafío del Episodio 5

## Desafío

Crea un workflow que use un trigger de "Form" para recibir datos de un formulario simple. Configura el formulario para recoger información de nombre, apellido y correo electrónico. 

Luego, utiliza un nodo Set para combinar el nombre y apellido en un nuevo valor llamado "nombre_y_apellido". Personaliza el formulario como desees para hacerlo más atractivo.

![Desafío 5](../images/parte5/desafio5.png)

## Instrucciones de la Solución

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Formulario de Contacto".

### Paso 2: Configurar el nodo "Form Trigger"

1. Añade un nodo "Form Trigger" al canvas.
2. Configura el formulario con los siguientes campos:
   - Un campo de tipo "Text" con label "Nombre" y nombre de variable "nombre"
   - Un campo de tipo "Text" con label "Apellido" y nombre de variable "apellido"
   - Un campo de tipo "Email" con label "Correo electrónico" y nombre de variable "correo"
   - Un botón de envío con el texto "Enviar información"
3. Personaliza el formulario según tus preferencias:
   - Añade un título atractivo
   - Cambia los colores si lo deseas
   - Añade un mensaje de descripción
4. Haz clic en "Save" para guardar la configuración.
5. Observa la URL del formulario que se genera. Puedes acceder a ella para probar tu formulario.

### Paso 3: Añadir un nodo "Set" para procesar los datos

1. Añade un nodo "Set" después del nodo "Form Trigger".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el primer campo con:
   - Name: `nombre_y_apellido`
   - Type: `String`
   - Value: `{{$json.nombre}} {{$json.apellido}}`
4. Añade un segundo campo haciendo clic en "Add Value" nuevamente:
   - Name: `mensaje_confirmacion`
   - Type: `String`
   - Value: `Gracias {{$json.nombre}} {{$json.apellido}} por contactarnos. Te responderemos pronto en {{$json.correo}}.`
5. Guarda la configuración del nodo.

### Paso 4: Añadir un nodo "Respond to Webhook" para mostrar una confirmación

1. Añade un nodo "Respond to Webhook" después del nodo "Set".
2. Configura el nodo para mostrar un mensaje de confirmación:
   - Response Code: `200`
   - Response Mode: `Last Node`
   - Response Data: `First Entry`
3. En la sección "Response Body", selecciona "Expression" y usa:
   ```
   {{$node["Set"].json.mensaje_confirmacion}}
   ```
4. Guarda la configuración del nodo.

### Paso 5: Probar el formulario

1. Activa el workflow haciendo clic en el botón "Toggle Active".
2. Abre la URL del formulario en una nueva pestaña del navegador.
3. Completa el formulario con datos de prueba:
   - Nombre: "Ana"
   - Apellido: "García"
   - Correo: "ana.garcia@ejemplo.com"
4. Haz clic en el botón "Enviar información".
5. Deberías ver el mensaje de confirmación personalizado.

### Paso 6: Verificar los resultados

1. Vuelve a la interfaz de n8n y observa que el workflow se ha ejecutado.
2. Haz clic en el nodo "Form Trigger" para ver los datos recibidos.
3. Haz clic en el nodo "Set" para ver cómo se procesaron los datos y cómo se ha creado el nuevo campo `nombre_y_apellido`.
4. Verifica que el mensaje de confirmación se muestra correctamente al usuario.

## Conceptos clave

- **Form Trigger**: Un método para crear formularios web directamente desde n8n sin necesidad de código HTML.
- **Trigger automático**: Cómo los workflows pueden iniciarse automáticamente cuando un usuario envía un formulario.
- **Procesamiento de datos de formulario**: Cómo acceder y manipular datos recibidos a través de un formulario.
- **Transformación de datos**: Cómo combinar y transformar datos utilizando el nodo Set.
- **Respuestas personalizadas**: Cómo configurar mensajes de confirmación personalizados para los usuarios.

## Recursos adicionales

- [Documentación del nodo Form Trigger](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.formtrigger/)
- [Documentación del nodo Set](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.set/)
- [Documentación del nodo Respond to Webhook](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.respondtowebhook/) 
