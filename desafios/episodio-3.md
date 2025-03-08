# Episodio 3: Introducción a la interfaz de usuario de n8n

## Desafío

Crea un workflow simple con dos nodos: un nodo "Manual Trigger" y un nodo "Set". Conecta ambos nodos y ejecuta el workflow manualmente. Toma una captura de pantalla del canvas con los nodos conectados y otra del panel de ejecuciones después de ejecutarlo para mostrar que funcionó.

## Instrucciones

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Haz clic en el botón "Workflows" en el menú lateral izquierdo.
3. Haz clic en el botón "+ Workflow" para crear un nuevo workflow.
4. Dale un nombre descriptivo a tu workflow, por ejemplo, "Mi Primer Workflow".

### Paso 2: Añadir un nodo "Manual Trigger"

1. En el canvas vacío, haz clic en el botón "+" para añadir un nodo.
2. En el panel de búsqueda, escribe "Manual" y selecciona el nodo "Manual Trigger".
3. Este nodo se añadirá automáticamente al canvas.

### Paso 3: Añadir un nodo "Set"

1. Haz clic en el botón "+" que aparece después del nodo "Manual Trigger".
2. En el panel de búsqueda, escribe "Set" y selecciona el nodo "Set".
3. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
4. Configura el campo con:
   - Name: `mensaje`
   - Type: `String`
   - Value: `¡Hola desde n8n!`
5. Haz clic en "Save" para guardar la configuración del nodo.

### Paso 4: Ejecutar el workflow

1. Haz clic en el botón "Execute Workflow" en la parte superior derecha del canvas.
2. Observa cómo se ejecuta el workflow y cómo los datos fluyen del nodo "Manual Trigger" al nodo "Set".
3. Una vez completada la ejecución, podrás ver los resultados haciendo clic en el nodo "Set".

## Entrega

Para completar este desafío, debes:

1. Adjuntar una captura de pantalla del canvas con los dos nodos conectados.
2. Adjuntar una captura de pantalla del panel de ejecuciones después de ejecutar el workflow.
3. Explicar brevemente qué hace cada nodo en este workflow:
   - ¿Qué función cumple el nodo "Manual Trigger"?
   - ¿Qué función cumple el nodo "Set"?
   - ¿Cómo fluyen los datos entre estos nodos?

## Recursos adicionales

- [Documentación de la interfaz de usuario de n8n](https://docs.n8n.io/workflows/editor-ui/)
- [Guía de nodos básicos en n8n](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.set/) 