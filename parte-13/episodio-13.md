# Episodio 13: Nodos In App

## Desafío

Crea un workflow que use el nodo de Google Sheets para leer datos de una hoja de cálculo con una lista de tareas (por ejemplo, columnas "Tarea" y "Completada"). Usa un nodo "If" para filtrar las tareas completadas y envía un resumen por correo electrónico con el nodo "Email" (por ejemplo, "Tareas completadas: 3").

## Instrucciones

### Paso 1: Preparar la hoja de cálculo de Google

1. Accede a [Google Sheets](https://sheets.google.com/) y crea una nueva hoja de cálculo.
2. Nombra la hoja de cálculo "Lista de Tareas".
3. Configura las siguientes columnas:
   - Columna A: "Tarea"
   - Columna B: "Completada" (usa "Sí" o "No" como valores)
4. Añade al menos 5 tareas, con algunas marcadas como completadas y otras como no completadas.
5. Anota el ID de la hoja de cálculo (lo encontrarás en la URL, es una cadena larga de caracteres).

### Paso 2: Crear un nuevo workflow en n8n

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Gestor de Tareas".

### Paso 3: Configurar el nodo "Manual Trigger"

1. Añade un nodo "Manual Trigger" al canvas.
2. No es necesario configurar nada en este nodo, ya que simplemente iniciará el workflow manualmente.

### Paso 4: Configurar el nodo "Google Sheets"

1. Añade un nodo "Google Sheets" después del "Manual Trigger".
2. Configura una nueva credencial de Google Sheets siguiendo el asistente de autenticación.
3. Configura el nodo con los siguientes parámetros:
   - Operation: `Read`
   - Resource: `Sheet`
   - Spreadsheet ID: Ingresa el ID de tu hoja de cálculo
   - Range: `A:B` (para leer las columnas A y B)
   - Has Header Row: Activa esta opción
4. Guarda la configuración del nodo.

### Paso 5: Configurar el nodo "Split In Batches"

1. Añade un nodo "Split In Batches" después del nodo "Google Sheets".
2. Configura el nodo para procesar cada fila individualmente:
   - Batch Size: `1`
   - Options: Deja las opciones predeterminadas
3. Guarda la configuración del nodo.

### Paso 6: Configurar el nodo "If" para filtrar tareas completadas

1. Añade un nodo "If" después del nodo "Split In Batches".
2. Configura el nodo con los siguientes parámetros:
   - Value 1: `{{$json["Completada"]}}`
   - Operation: `Equal`
   - Value 2: `Sí`
3. Guarda la configuración del nodo.

### Paso 7: Configurar el nodo "Aggregate" para contar tareas completadas

1. Añade un nodo "Aggregate" conectado a la salida "true" del nodo "If".
2. Configura el nodo con los siguientes parámetros:
   - Aggregate: `Count`
   - Field to Aggregate: `Tarea`
   - Output Field Name: `tareas_completadas`
3. Guarda la configuración del nodo.

### Paso 8: Configurar el nodo "Email" para enviar el resumen

1. Añade un nodo "Email" después del nodo "Aggregate".
2. Configura una nueva credencial de SMTP siguiendo el asistente (puedes usar servicios como Gmail, Outlook, etc.).
3. Configura el nodo con los siguientes parámetros:
   - From Email: Tu dirección de correo electrónico
   - To Email: La dirección donde quieres recibir el resumen
   - Subject: `Resumen de Tareas Completadas`
   - Text: `Se han completado {{$json.tareas_completadas}} tareas de la lista.`
4. Guarda la configuración del nodo.

### Paso 9: Ejecutar y verificar el workflow

1. Haz clic en "Execute Workflow" para ejecutar el workflow.
2. Una vez completada la ejecución, verifica que el correo electrónico se haya enviado correctamente.
3. Comprueba que el contenido del correo refleje correctamente el número de tareas completadas.

## Entrega

Para completar este desafío, debes:

1. Adjuntar una captura de pantalla del canvas con todos los nodos conectados.
2. Adjuntar una captura de pantalla de la hoja de cálculo de Google con tus tareas.
3. Adjuntar una captura de pantalla del correo electrónico recibido con el resumen.
4. Responder a las siguientes preguntas:
   - ¿Qué otras operaciones podrías realizar con el nodo de Google Sheets?
   - ¿Cómo podrías modificar este workflow para que se ejecute automáticamente cada día?
   - ¿Qué otras aplicaciones podrías integrar en este workflow para mejorar la gestión de tareas?

## Conceptos clave

- **Integración con aplicaciones externas**: Cómo conectar n8n con servicios populares como Google Sheets.
- **Procesamiento de datos tabulares**: Cómo leer y procesar datos de hojas de cálculo.
- **Filtrado y agregación**: Cómo filtrar datos y realizar operaciones de agregación.
- **Notificaciones por correo**: Cómo enviar correos electrónicos automatizados con información procesada.

## Recursos adicionales

- [Documentación del nodo Google Sheets](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.googlesheets/)
- [Documentación del nodo Email](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.email/)
- [Guía de autenticación con Google](https://docs.n8n.io/integrations/builtin/credentials/google/)
- [Patrones de integración con aplicaciones](https://docs.n8n.io/workflows/integrations/) 