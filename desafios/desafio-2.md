# Desafío 2: Primeros pasos con la interfaz de n8n

![Interfaz de n8n](https://docs.n8n.io/assets/img/workflow-ui.c5c1bc1e.png)

## Objetivo

Familiarizarte con la interfaz de usuario de n8n creando un workflow simple con dos nodos conectados y ejecutándolo manualmente.

## Contexto

La interfaz de n8n está diseñada para facilitar la creación visual de flujos de trabajo. Antes de crear automatizaciones complejas, es importante entender cómo navegar por la interfaz, añadir nodos y conectarlos entre sí. Este desafío te ayudará a dar tus primeros pasos en el entorno de n8n.

## Requisitos

- n8n instalado y funcionando en tu máquina local
- Acceso a la interfaz web de n8n

## El desafío

1. **Explorar la interfaz de n8n**
   - Accede a la interfaz web de n8n
   - Identifica los elementos principales: menú lateral, canvas, barra de herramientas
   - Crea un nuevo workflow y asígnale un nombre descriptivo

2. **Crear un workflow simple**
   - Añade un nodo "Manual Trigger" al canvas
   - Añade un nodo "Set" después del trigger
   - Configura el nodo "Set" para crear un objeto JSON con tu nombre y edad
   - Conecta ambos nodos

3. **Ejecutar el workflow**
   - Ejecuta el workflow manualmente
   - Observa cómo fluyen los datos entre los nodos
   - Examina los resultados de la ejecución

## Pistas

- El nodo "Manual Trigger" es el punto de partida para workflows que se ejecutan manualmente
- El nodo "Set" permite definir valores estáticos que se utilizarán en el workflow
- Para añadir un nodo, puedes hacer clic en el botón "+" que aparece después de un nodo existente
- Para ejecutar un workflow, utiliza el botón "Execute Workflow" en la parte superior del canvas 