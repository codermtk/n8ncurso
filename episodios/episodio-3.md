# Episodio 3: Introducción a la interfaz de usuario de n8n

![Interfaz de n8n](https://docs.n8n.io/assets/img/workflow-ui.c5c1bc1e.png)

## Elementos principales de la interfaz de n8n

La interfaz de usuario de n8n está diseñada para facilitar la creación visual de flujos de trabajo. Está compuesta por varios elementos clave:

### 1. Menú lateral izquierdo

Proporciona acceso a las principales secciones de n8n:
- **Workflows**: Lista de todos tus flujos de trabajo
- **Credentials**: Gestión de credenciales para conectar con servicios externos
- **Executions**: Historial de ejecuciones de tus workflows
- **Settings**: Configuración general de n8n

### 2. Canvas central

Área principal donde se diseñan los workflows arrastrando y conectando nodos. Aquí es donde pasarás la mayor parte del tiempo construyendo tus automatizaciones.

### 3. Barra de herramientas superior

Contiene herramientas esenciales para trabajar con tu workflow:
- **Botón de guardar**: Para guardar los cambios en tu workflow
- **Botón de ejecutar workflow**: Para iniciar manualmente la ejecución
- **Opciones de zoom**: Para acercar o alejar la vista del canvas
- **Acceso a la configuración del workflow**: Para cambiar el nombre, descripción y otras opciones

### 4. Panel de nodos

Aparece al hacer clic en el botón "+" para añadir un nodo. Muestra todos los nodos disponibles organizados por categorías:
- **Triggers**: Nodos que inician un workflow
- **Actions**: Nodos que realizan acciones específicas
- **Core**: Nodos básicos de n8n
- Y muchas otras categorías según las integraciones disponibles

## Tipos de nodos básicos

En n8n, los nodos se clasifican en diferentes tipos según su función:

### Trigger Nodes

Inician un workflow cuando ocurre un evento específico:
- **Manual Trigger**: Inicia el workflow manualmente
- **Schedule Trigger**: Inicia el workflow según un horario programado
- **Webhook**: Inicia el workflow cuando se recibe una solicitud HTTP
- **Cron**: Inicia el workflow según una expresión cron

### Regular Nodes

Procesan datos y realizan acciones:
- **HTTP Request**: Realiza solicitudes HTTP a APIs externas
- **Set**: Define valores estáticos o dinámicos
- **Function**: Ejecuta código JavaScript personalizado
- **IF**: Implementa lógica condicional

### Core Nodes

Proporcionan funcionalidades básicas para manipular datos:
- **Merge**: Combina datos de múltiples fuentes
- **Split In Batches**: Divide grandes conjuntos de datos en lotes más pequeños
- **Aggregate**: Realiza operaciones de agregación en conjuntos de datos
- **Filter**: Filtra datos según criterios específicos

## Conexión de nodos

Para conectar dos nodos en el canvas:

1. Haz clic en el punto de salida de un nodo (generalmente a la derecha)
2. Arrastra hasta el punto de entrada del siguiente nodo (generalmente a la izquierda)
3. Suelta para crear la conexión

También puedes hacer clic en el botón "+" que aparece después de un nodo para añadir y conectar automáticamente un nuevo nodo.

## Ejecución de workflows

Para ejecutar un workflow:

1. Haz clic en el botón "Execute Workflow" en la parte superior del canvas
2. Observa cómo los nodos cambian de color a medida que se ejecutan
3. Haz clic en cualquier nodo para ver los datos que pasan por él
4. Revisa la pestaña "Executions" para ver el historial de ejecuciones

## Recursos

- [Documentación de la interfaz de usuario de n8n](https://docs.n8n.io/workflows/editor-ui/)
- [Guía de nodos básicos en n8n](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.set/)
- [Tutorial de primeros pasos con n8n](https://docs.n8n.io/getting-started/quickstart/) 