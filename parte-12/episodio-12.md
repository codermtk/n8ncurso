# Episodio 12: Nodos In App

## Contenido del episodio
- [Introducción a los nodos In App](#introducción-a-los-nodos-in-app)
- [Tipos de nodos In App](#tipos-de-nodos-in-app)
  - [Nodos Trigger](#nodos-trigger)
  - [Nodos de Acción](#nodos-de-acción)
  - [Nodos de Datos](#nodos-de-datos)
- [Principales proveedores e integraciones](#principales-proveedores-e-integraciones)
  - [Gmail y Google Workspace](#gmail-y-google-workspace)
  - [Airtable](#airtable)
  - [Telegram](#telegram)
  - [Slack](#slack)
  - [Notion](#notion)
- [Integraciones para herramientas de IA](#integraciones-para-herramientas-de-ia)
- [Similaridad entre nodos In App y herramientas para agentes](#similaridad-entre-nodos-in-app-y-herramientas-para-agentes)
- [Caso práctico 1: Automatización sin IA](#caso-práctico-1-automatización-sin-ia)
- [Caso práctico 2: Combinando IA con integraciones](#caso-práctico-2-combinando-ia-con-integraciones)
- [Estructura de contenido para integraciones](#estructura-de-contenido-para-integraciones)
- [Desafío del episodio 12](#desafío-del-episodio-12)

## Introducción a los nodos In App

Hasta ahora, hemos explorado principalmente los nodos core de n8n y los nodos relacionados con IA. En este episodio, nos adentraremos en otro componente fundamental de n8n: los nodos In App, que nos permiten conectar nuestra automatización con servicios y aplicaciones externas.

Los nodos In App son integraciones predefinidas con aplicaciones y servicios populares como Gmail, Google Sheets, Airtable, Telegram, Slack y muchos más. Estas integraciones nos permiten:

- Recibir datos y eventos de aplicaciones externas
- Enviar datos y realizar acciones en estas aplicaciones
- Procesar y transformar información entre diferentes servicios

La combinación de estos nodos con las capacidades de IA que hemos aprendido abre un mundo de posibilidades para crear automatizaciones inteligentes y potentes.

## Tipos de nodos In App

Los nodos In App se pueden clasificar en tres categorías principales según su función:

### Nodos Trigger

Los nodos Trigger inician un workflow cuando ocurre un evento específico en la aplicación externa:

- **Ejemplos**:
  - Gmail: Cuando se recibe un nuevo correo
  - Telegram: Cuando llega un nuevo mensaje
  - Google Calendar: Cuando se crea un nuevo evento
  - Airtable: Cuando se añade un nuevo registro

- **Características**:
  - Funcionan como puntos de entrada para el workflow
  - Pueden configurarse para filtrar eventos específicos
  - Suelen requerir webhooks o polling para detectar eventos

### Nodos de Acción

Los nodos de Acción realizan operaciones en la aplicación externa:

- **Ejemplos**:
  - Gmail: Enviar un correo electrónico
  - Google Sheets: Añadir una fila a una hoja de cálculo
  - Telegram: Enviar un mensaje
  - Airtable: Crear un nuevo registro

- **Características**:
  - Ejecutan operaciones específicas en la aplicación
  - Pueden configurarse con datos dinámicos
  - Devuelven información sobre el resultado de la acción

### Nodos de Datos

Los nodos de Datos recuperan o manipulan información en la aplicación externa:

- **Ejemplos**:
  - Gmail: Buscar correos electrónicos
  - Google Sheets: Leer filas de una hoja de cálculo
  - Notion: Buscar páginas o bases de datos
  - Airtable: Listar registros con filtros

- **Características**:
  - Permiten consultar y recuperar información
  - Suelen ofrecer opciones de filtrado y ordenación
  - Facilitan la integración de datos entre aplicaciones

## Principales proveedores e integraciones

n8n ofrece integraciones con cientos de aplicaciones y servicios. Veamos algunos de los más populares y versátiles:

### Gmail y Google Workspace

La integración con Google Workspace es una de las más completas y utilizadas:

- **Gmail**: Enviar y recibir correos, gestionar etiquetas, buscar mensajes
- **Google Sheets**: Crear y actualizar hojas de cálculo, leer y escribir datos
- **Google Drive**: Gestionar archivos, crear carpetas, compartir documentos
- **Google Calendar**: Programar eventos, recibir notificaciones, gestionar calendarios

**Caso de uso**: Automatizar el envío de informes semanales generados por IA a partir de datos en Google Sheets.

### Airtable

Airtable es una plataforma de base de datos flexible y visual que se integra perfectamente con n8n:

- **Operaciones**: Crear, leer, actualizar y eliminar registros
- **Triggers**: Detectar nuevos o modificados registros
- **Filtros**: Buscar registros que cumplan criterios específicos

**Caso de uso**: Almacenar y categorizar automáticamente información extraída por un agente de IA.

### Telegram

La integración con Telegram permite crear bots y automatizaciones para esta plataforma de mensajería:

- **Recibir mensajes**: Capturar mensajes enviados al bot
- **Enviar mensajes**: Texto, imágenes, documentos, etc.
- **Comandos**: Responder a comandos específicos
- **Grupos**: Gestionar conversaciones grupales

**Caso de uso**: Crear un bot de Telegram que utilice IA para responder preguntas o realizar tareas específicas.

### Slack

Similar a Telegram, la integración con Slack permite automatizar comunicaciones en este popular servicio de mensajería empresarial:

- **Mensajes**: Enviar y recibir mensajes en canales o directos
- **Reacciones**: Detectar y añadir reacciones a mensajes
- **Archivos**: Compartir y gestionar archivos
- **Usuarios**: Gestionar información de usuarios

**Caso de uso**: Crear un asistente de IA para equipos que responda a consultas en canales de Slack.

### Notion

Notion es una herramienta todo-en-uno para notas, bases de datos y gestión de proyectos:

- **Páginas**: Crear, leer y actualizar páginas
- **Bases de datos**: Gestionar registros en bases de datos
- **Búsqueda**: Encontrar contenido específico
- **Comentarios**: Añadir y gestionar comentarios

**Caso de uso**: Crear un sistema que documente automáticamente información generada por IA en páginas de Notion.

## Integraciones para herramientas de IA

Algunas integraciones In App son especialmente útiles cuando se combinan con nodos de IA:

1. **Google Sheets**: Para almacenar y recuperar datos que alimentan modelos de IA
2. **Notion**: Para documentar resultados de análisis de IA
3. **Gmail**: Para procesar correos con IA y enviar respuestas inteligentes
4. **Telegram/Slack**: Para crear interfaces conversacionales con agentes de IA
5. **Airtable**: Para crear bases de conocimiento que pueden ser consultadas por sistemas RAG

Estas integraciones permiten que nuestros modelos de IA interactúen con el mundo real, recibiendo información y realizando acciones concretas.

## Similaridad entre nodos In App y herramientas para agentes

Existe una interesante similitud conceptual entre los nodos In App y las herramientas que pueden utilizar los agentes de IA:

| Nodos In App | Herramientas para Agentes |
|--------------|---------------------------|
| Realizan acciones específicas en aplicaciones externas | Realizan acciones específicas cuando el agente las invoca |
| Tienen parámetros configurables | Tienen parámetros que el agente debe proporcionar |
| Devuelven resultados estructurados | Devuelven resultados que el agente puede interpretar |
| Se conectan a servicios externos | Amplían las capacidades del agente más allá del modelo de lenguaje |

Esta similitud no es casualidad: ambos conceptos buscan extender las capacidades básicas del sistema (n8n o el modelo de lenguaje) permitiéndole interactuar con servicios externos.

La principal diferencia es que los nodos In App son configurados y conectados manualmente por el usuario, mientras que las herramientas para agentes son seleccionadas y utilizadas dinámicamente por el propio agente.


## Desafío del episodio 12

Para poner en práctica lo aprendido, te invitamos a completar el [desafío del episodio 12](desafio-episodio-12.md), donde crearás un asistente inteligente que combine IA con integraciones de aplicaciones para resolver un problema práctico. 