# Episodio 9: Nodos de IA 1 - Introducción y Chains

## Contenido del episodio
- [Introducción a los nodos de IA en n8n](#introducción-a-los-nodos-de-ia-en-n8n)
- [Arquitectura de los nodos de IA: LangChain](#arquitectura-de-los-nodos-de-ia-langchain)
- [Comunicación con modelos de IA](#comunicación-con-modelos-de-ia)
- [Diferencia entre Chains y Agentes](#diferencia-entre-chains-y-agentes)
- [Componentes de una LLM Chain](#componentes-de-una-llm-chain)
  - [Modelos de lenguaje](#modelos-de-lenguaje)
  - [Prompts y mensajes](#prompts-y-mensajes)
  - [Parámetros de generación](#parámetros-de-generación)
- [Implementando nuestra primera Chain](#implementando-nuestra-primera-chain)
- [Caso práctico: Web Scraping con IA](#caso-práctico-web-scraping-con-ia)
- [Desafío del episodio 9](#desafío-del-episodio-9)

## Introducción a los nodos de IA en n8n

En este episodio, comenzamos una nueva sección del curso dedicada a la integración de Inteligencia Artificial en nuestros flujos de trabajo con n8n. La plataforma n8n ha incorporado un conjunto de nodos especializados que nos permiten aprovechar el poder de los modelos de lenguaje de gran tamaño (LLMs) y otras tecnologías de IA para automatizar tareas complejas que antes requerían intervención humana.

Estos nodos de IA nos permiten:

- Generar texto, código y contenido creativo
- Resumir y analizar documentos
- Extraer información estructurada de textos no estructurados
- Responder preguntas basadas en conocimiento específico
- Automatizar interacciones conversacionales
- Crear agentes inteligentes que pueden razonar y utilizar herramientas

## Arquitectura de los nodos de IA: LangChain

Los nodos de IA en n8n están construidos sobre [LangChain](https://www.langchain.com/), un framework de código abierto diseñado para desarrollar aplicaciones potenciadas por modelos de lenguaje. LangChain proporciona abstracciones que facilitan la creación de aplicaciones complejas de IA, y n8n ha integrado estas capacidades en su interfaz visual.

La arquitectura básica de los nodos de IA en n8n incluye:

1. **Nodos de conexión a modelos**: Permiten establecer conexión con diferentes proveedores de modelos de IA (OpenAI, Google, Anthropic, etc.)
2. **Nodos de cadenas (Chains)**: Combinan modelos con prompts y lógica para realizar tareas específicas
3. **Nodos de agentes**: Implementan agentes que pueden razonar y utilizar herramientas para resolver problemas
4. **Nodos de memoria**: Permiten a los modelos mantener contexto a lo largo de una conversación
5. **Nodos de herramientas**: Proporcionan capacidades adicionales a los agentes (búsqueda web, cálculos, etc.)
6. **Nodos de almacenamiento vectorial**: Facilitan la implementación de sistemas RAG (Retrieval Augmented Generation)

## Comunicación con modelos de IA

n8n se comunica con los modelos de IA a través de APIs proporcionadas por los diferentes proveedores. El flujo básico es el siguiente:

1. **Autenticación**: n8n utiliza claves API para autenticarse con el proveedor del modelo
2. **Preparación de la solicitud**: Los datos de entrada se formatean según los requisitos de la API
3. **Envío de la solicitud**: n8n envía la solicitud al endpoint correspondiente
4. **Recepción de la respuesta**: El modelo procesa la solicitud y devuelve una respuesta
5. **Procesamiento de la respuesta**: n8n procesa la respuesta y la pasa al siguiente nodo en el flujo

Este proceso está encapsulado en los nodos de IA, lo que nos permite interactuar con modelos complejos sin tener que gestionar manualmente las llamadas a la API.

## Diferencia entre Chains y Agentes

En el ecosistema de LangChain, existen dos conceptos fundamentales que debemos entender:

### Chains (Cadenas)

Las Chains son secuencias predefinidas de operaciones que combinan modelos de lenguaje con prompts específicos para realizar una tarea concreta. Son como "recetas" que definen exactamente cómo se debe procesar la entrada y generar la salida.

**Características de las Chains:**
- Flujo de trabajo determinista y predecible
- Diseñadas para tareas específicas y bien definidas
- No tienen capacidad de "razonamiento" o toma de decisiones dinámica
- Más eficientes en términos de tokens y costos
- Más rápidas en la ejecución

### Agentes

Los Agentes, por otro lado, son sistemas más avanzados que pueden "razonar" sobre cómo resolver un problema, decidir qué herramientas utilizar y planificar una secuencia de acciones. Los agentes utilizan un bucle de razonamiento (reasoning loop) para determinar los pasos a seguir.

**Características de los Agentes:**
- Flujo de trabajo dinámico basado en el razonamiento del modelo
- Pueden utilizar herramientas (calculadoras, búsqueda web, etc.)
- Mantienen memoria del contexto y acciones previas
- Más flexibles y adaptables a diferentes situaciones
- Consumen más tokens y son más costosos
- Ejecución más lenta debido al proceso de razonamiento

En este episodio nos centraremos en las Chains, mientras que los Agentes serán el foco del próximo episodio.

## Componentes de una LLM Chain

Una LLM Chain básica en n8n consta de varios componentes esenciales:

### Modelos de lenguaje

El componente central es el modelo de lenguaje (LLM) que realizará el procesamiento. n8n soporta varios proveedores:

- **OpenAI**: Modelos como gpt-4o o o3-mini
- **Google**: Modelos como gemini-2.0-flash o gemini-2.0-flash-thinking-exp-01-21
- **Anthropic**: Modelos como claude-3.5-sonnet o claude-3.7-sonnet
- **Ollama**: Para ejecutar modelos localmente
- **Otros proveedores**: DeepSeek, xAI etc.

Para conectar con estos modelos, necesitamos configurar una credencial con la clave API correspondiente.

### Prompts y mensajes

Los prompts son las instrucciones que enviamos al modelo. En el contexto de los modelos de chat, trabajamos con diferentes tipos de mensajes:

- **System Message (Mensaje del sistema)**: Define el comportamiento general, personalidad o rol del asistente. Establece las reglas y el contexto global.
  
- **User Message (Mensaje del usuario)**: Representa la entrada o consulta del usuario final.
  
- **Assistant Message (Mensaje del asistente)**: Contiene respuestas previas del asistente, útil para mantener contexto en conversaciones.

Un prompt bien diseñado es crucial para obtener resultados de calidad. Algunas técnicas incluyen:

- Ser específico y claro en las instrucciones
- Proporcionar ejemplos (few-shot prompting)
- Estructurar la información de manera lógica
- Especificar el formato de salida deseado

### Parámetros de generación

Los parámetros de generación controlan cómo el modelo genera texto. Los más importantes son:

- **Temperature (Temperatura)**: Controla la aleatoriedad de las respuestas. Valores más bajos (cercanos a 0) producen respuestas más deterministas y enfocadas, mientras que valores más altos (cercanos a 1) generan respuestas más creativas y diversas.

- **Top K**: Limita la selección de tokens a los K más probables en cada paso de generación. Ayuda a evitar tokens muy improbables.

- **Top P (Nucleus Sampling)**: En lugar de considerar todos los tokens posibles, solo considera los tokens cuya probabilidad acumulada alcanza el valor P. Un valor de 0.9 significa que solo se consideran los tokens que constituyen el 90% de la probabilidad total.

## Implementando nuestra primera Chain

Vamos a implementar una Chain básica que responda preguntas sobre n8n utilizando el nodo LLM Chain. Seguiremos estos pasos:

1. **Crear un nuevo workflow**:
   - Nombre: "Asistente de n8n"
   - Descripción: "Una Chain simple para responder preguntas sobre n8n"

2. **Añadir un nodo de Chat**:
   - Este será el punto de entrada de nuestro workflow
   - Configurar un campo de entrada para la pregunta del usuario

3. **Añadir un nodo LLM Chain**:
   - Conectar con el proveedor de modelo (usaremos Google para este ejemplo)
   - Configurar el System Message para definir el comportamiento del asistente
   - Configurar el User Message para incluir la pregunta del usuario
   - Ajustar los parámetros de generación según nuestras necesidades


### Configuración del nodo LLM Chain

La configuración del nodo LLM Chain sería la siguiente:

1. **Conexión al modelo**:
   - Modelo: gemini-2.0-flash
   - Credencial: Tu clave API de Google

2. **System Message**:
   ```
   Eres un asistente experto en n8n, una plataforma de automatización de flujos de trabajo. 
   Tu objetivo es proporcionar información precisa y útil sobre n8n, sus características, 
   nodos y mejores prácticas. Responde de manera concisa y con ejemplos prácticos cuando sea posible.
   ```

3. **User Message**:
   ```
   {{$json.pregunta}}
   ```

4. **Parámetros de generación**:
   - Temperature: 0.3 (para respuestas más precisas)
   - Top P: 0.9

El resultado será una Chain simple pero efectiva que puede responder preguntas sobre n8n de manera informativa y útil.

## Caso práctico: Web Scraping con IA

Un caso de uso poderoso para las Chains es el procesamiento de información obtenida de la web. Vamos a crear un workflow que:

1. Obtenga contenido de una página web
2. Utilice una LLM Chain para extraer información específica
3. Presente los resultados de manera estructurada

### Implementación del Web Scraper con IA

1. **Añadir un nodo HTTP Request**:
   - Método: GET
   - URL: La URL de la página web que queremos analizar
   - Autenticación: Ninguna (para páginas públicas)

2. **Añadir un nodo Set**:
   - Extraer el contenido HTML de la respuesta
   - Opcionalmente, limpiar el HTML para obtener solo el texto (usar un nodo Markdown para ayudar a limpiar)

3. **Añadir un nodo LLM Chain**:
   - System Message:
     ```
     Eres un experto en extraer información de páginas web que todavía están en formato HTML. 
     Tu tarea es analizar el contenido proporcionado y extraer toda la información escrita de la web.
     ```
   
   - User Message:
     ```
     Analiza el siguiente contenido de una página web y extrae:

     1. Toda la información de la web en texto
     2. Un breve resumen del contenido

     Contenido:
     {{$json.contenido}}

     Devuelve la información en este formato JSON:
     {
       "texto": "Título principal",
       "resumen": "Breve resumen del contenido"
     }
     ```

4. **Añadir un nodo JSON Parse**:
   - Para convertir la respuesta en formato JSON a un objeto que podamos manipular

Este workflow nos permite extraer información estructurada de páginas web de manera automática, algo que sería muy difícil de lograr con métodos tradicionales de scraping.

## Desafío del episodio 9

Para poner en práctica lo aprendido, te invitamos a completar el [desafío del episodio 9](desafio-episodio-9.md), donde crearás una Chain con personalidad de pirata.
