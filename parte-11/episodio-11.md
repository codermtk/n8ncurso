# Episodio 11: Nodos de IA 3 - RAG y Vector Stores

## Contenido del episodio
- [Introducción a RAG y Vector Stores](#introducción-a-rag-y-vector-stores)
- [¿Qué es RAG (Retrieval Augmented Generation)?](#qué-es-rag-retrieval-augmented-generation)
  - [Limitaciones de los LLMs tradicionales](#limitaciones-de-los-llms-tradicionales)
  - [Cómo RAG soluciona estas limitaciones](#cómo-rag-soluciona-estas-limitaciones)
  - [Arquitectura básica de RAG](#arquitectura-básica-de-rag)
- [Vector Stores: El corazón de RAG](#vector-stores-el-corazón-de-rag)
  - [¿Qué son los embeddings?](#qué-son-los-embeddings)
  - [Funcionamiento de un Vector Store](#funcionamiento-de-un-vector-store)
  - [Tipos de Vector Stores](#tipos-de-vector-stores)
- [Implementando RAG en n8n](#implementando-rag-en-n8n)
  - [Nodos necesarios para RAG](#nodos-necesarios-para-rag)
  - [Flujo de trabajo básico](#flujo-de-trabajo-básico)
- [Nodos de Vector Store en detalle](#nodos-de-vector-store-en-detalle)
  - [Document Loader](#document-loader)
  - [Text Splitter](#text-splitter)
  - [Embeddings](#embeddings)
  - [Vector Store](#vector-store)
  - [Vector Store Retriever](#vector-store-retriever)
- [Caso práctico: Asistente de documentación técnica](#caso-práctico-asistente-de-documentación-técnica)
- [Optimizando sistemas RAG](#optimizando-sistemas-rag)
  - [Estrategias de chunking](#estrategias-de-chunking)
  - [Técnicas de retrieval avanzadas](#técnicas-de-retrieval-avanzadas)
  - [Evaluación de sistemas RAG](#evaluación-de-sistemas-rag)
- [Desafío del episodio 11](#desafío-del-episodio-11)

## Introducción a RAG y Vector Stores

En los episodios anteriores, exploramos las Chains y los Agentes como formas de utilizar modelos de lenguaje para tareas específicas. Sin embargo, estos enfoques tienen una limitación importante: dependen principalmente del conocimiento que el modelo adquirió durante su entrenamiento, que puede estar desactualizado o incompleto.

En este episodio, nos adentraremos en una técnica que permite a los modelos de lenguaje acceder a información externa y actualizada: RAG (Retrieval Augmented Generation) y su componente fundamental, los Vector Stores.

Esta combinación nos permitirá crear aplicaciones de IA que pueden:
- Responder preguntas basadas en documentos específicos
- Proporcionar información actualizada y precisa
- Citar fuentes de información
- Reducir las alucinaciones (información incorrecta generada por el modelo)
- Personalizar las respuestas según el contexto específico

## ¿Qué es RAG (Retrieval Augmented Generation)?

RAG es una arquitectura que combina la recuperación de información (retrieval) con la generación de texto (generation). En términos simples, RAG permite a un modelo de lenguaje "buscar" información relevante en una base de conocimiento externa antes de generar una respuesta.

### Limitaciones de los LLMs tradicionales

Los modelos de lenguaje tradicionales presentan varias limitaciones:

1. **Conocimiento estático**: Su conocimiento está limitado a los datos con los que fueron entrenados, que pueden estar desactualizados.
2. **Falta de contexto específico**: No tienen acceso a información especializada o documentos privados.
3. **Alucinaciones**: Pueden generar información incorrecta cuando no conocen la respuesta.
4. **Falta de transparencia**: No pueden citar fuentes para sus afirmaciones.
5. **Limitaciones de contexto**: Tienen un límite en la cantidad de texto que pueden procesar a la vez.

### Cómo RAG soluciona estas limitaciones

RAG aborda estas limitaciones mediante:

1. **Acceso a información externa**: Permite al modelo consultar bases de conocimiento actualizadas.
2. **Contextualización**: Proporciona al modelo el contexto específico necesario para responder con precisión.
3. **Reducción de alucinaciones**: Al basarse en información recuperada, disminuye la tendencia a inventar datos.
4. **Trazabilidad**: Permite citar las fuentes de la información proporcionada.
5. **Superación de límites de contexto**: Puede acceder a grandes volúmenes de información sin necesidad de incluirla toda en el prompt.

### Arquitectura básica de RAG

Un sistema RAG típico consta de los siguientes componentes:

1. **Base de conocimiento**: Documentos, textos o información estructurada que queremos que el modelo pueda consultar.
2. **Indexación**: Proceso de convertir la base de conocimiento en un formato que permita búsquedas eficientes (aquí es donde entran los Vector Stores).
3. **Retrieval (Recuperación)**: Mecanismo para encontrar la información más relevante para una consulta específica.
4. **Augmentation (Aumento)**: Incorporación de la información recuperada en el prompt del modelo.
5. **Generation (Generación)**: Creación de una respuesta basada en el prompt aumentado.

## Vector Stores: El corazón de RAG

Los Vector Stores son la tecnología que hace posible la recuperación eficiente de información en sistemas RAG. Pero, ¿qué son exactamente y cómo funcionan?

### ¿Qué son los embeddings?

Para entender los Vector Stores, primero debemos comprender los embeddings:

Los embeddings son representaciones numéricas (vectores) de datos como texto, imágenes o audio. En el caso del texto, un embedding captura el significado semántico de las palabras o frases en un espacio vectorial multidimensional.

Características clave de los embeddings:
- Textos con significados similares tienen embeddings cercanos en el espacio vectorial.
- La "distancia" entre embeddings puede medirse matemáticamente (distancia coseno, euclidiana, etc.).
- Los embeddings convierten el problema de búsqueda semántica en un problema de búsqueda de vecinos cercanos en un espacio vectorial.

Por ejemplo, los embeddings de "perro" y "canino" estarían más cerca entre sí que los embeddings de "perro" y "automóvil".

### Funcionamiento de un Vector Store

Un Vector Store es una base de datos especializada que:

1. **Almacena embeddings**: Guarda los vectores que representan fragmentos de texto de nuestra base de conocimiento.
2. **Permite búsquedas por similitud**: Encuentra los vectores más cercanos a un vector de consulta.
3. **Mantiene metadatos**: Asocia cada embedding con su texto original y metadatos adicionales.
4. **Optimiza para búsquedas rápidas**: Utiliza estructuras de datos y algoritmos especializados para búsquedas eficientes en espacios de alta dimensionalidad.

El proceso básico es:
1. Dividir documentos en fragmentos (chunks)
2. Convertir cada fragmento en un embedding
3. Almacenar los embeddings en el Vector Store
4. Para una consulta, convertirla en embedding y buscar los fragmentos más similares

## Implementando RAG en n8n

n8n proporciona un conjunto completo de nodos para implementar sistemas RAG, desde la carga de documentos hasta la recuperación y generación de respuestas.

### Nodos necesarios para RAG

Para implementar un sistema RAG básico en n8n, necesitamos los siguientes nodos:

1. **Document Loader**: Para cargar documentos desde diferentes fuentes (PDF, texto, web, etc.).
2. **Text Splitter**: Para dividir documentos largos en fragmentos manejables.
3. **Embeddings**: Para convertir texto en vectores.
4. **Vector Store**: Para almacenar y recuperar embeddings.
5. **Vector Store Retriever**: Para buscar información relevante.
6. **Agent**: Para generar respuestas basadas en la información recuperada.

### Flujo de trabajo básico

Un flujo de trabajo RAG típico en n8n seguiría estos pasos:

1. **Indexación (se realiza una vez)**:
   - Cargar documentos con Document Loader
   - Dividir documentos en fragmentos con Text Splitter
   - Convertir fragmentos en embeddings con Embeddings
   - Almacenar embeddings en Vector Store

2. **Consulta (se realiza cada vez que hay una pregunta)**:
   - Recibir pregunta del usuario
   - Recuperar fragmentos relevantes con Vector Store Retriever
   - Combinar pregunta y fragmentos en un prompt
   - Generar respuesta con LLM Chain o Agent

## Nodos de Vector Store en detalle

Vamos a explorar en detalle cada uno de los nodos principales involucrados en la implementación de RAG en n8n.

### Document Loader

El nodo Document Loader permite cargar documentos desde diferentes fuentes:

- **Tipos de documentos soportados**:
  - PDF
  - Texto plano
  - HTML
  - CSV
  - JSON
  - Y más

- **Configuración clave**:
  - Fuente del documento (archivo, URL, texto directo)
  - Metadatos adicionales
  - Opciones de procesamiento específicas del formato

- **Salida**:
  - Documento estructurado con contenido y metadatos

### Text Splitter

El nodo Text Splitter divide documentos largos en fragmentos más pequeños:

- **Importancia del chunking**:
  - Los modelos tienen límites de contexto
  - Fragmentos más pequeños permiten recuperación más precisa
  - El tamaño óptimo depende del caso de uso

- **Tipos de splitters**:
  - Por caracteres
  - Por tokens
  - Por frases o párrafos
  - Recursivo (divide por separadores jerárquicos)

- **Configuración clave**:
  - Tamaño del fragmento
  - Superposición (overlap)
  - Separadores

- **Salida**:
  - Array de fragmentos de documento

### Embeddings

El nodo Embeddings convierte texto en vectores:

- **Proveedores de embeddings**:
  - OpenAI (text-embedding-3-small, text-embedding-3-large)
  - Google (embedding-001)
  - Modelos locales (via Ollama)

- **Configuración clave**:
  - Proveedor de embeddings
  - Modelo específico
  - Dimensionalidad (depende del modelo)

- **Salida**:
  - Texto con su embedding asociado

### Vector Store

El nodo Vector Store almacena y gestiona embeddings:

- **Opciones de Vector Store en n8n**:
  - Pinecone
  - Qdrant
  - Y otros

- **Operaciones principales**:
  - Crear/actualizar colección
  - Añadir documentos
  - Eliminar documentos
  - Buscar documentos similares

- **Configuración clave**:
  - Tipo de Vector Store
  - Nombre de la colección
  - Configuración de conexión
  - Metadatos para filtrado

### Vector Store Retriever

El nodo Vector Store Retriever busca información relevante:

- **Métodos de recuperación**:
  - Similarity search (búsqueda por similitud)
  - MMR (Maximal Marginal Relevance)
  - Filtrado por metadatos

- **Configuración clave**:
  - Número de resultados (k)
  - Score mínimo de similitud
  - Filtros de metadatos
  - Método de recuperación

- **Salida**:
  - Fragmentos de documento relevantes con sus scores de similitud

## Optimizando sistemas RAG

Para obtener el mejor rendimiento de un sistema RAG, es importante optimizar varios aspectos:

### Estrategias de chunking

El tamaño y la forma de dividir los documentos afectan significativamente la calidad de las respuestas:

- **Tamaño del chunk**:
  - Chunks pequeños (100-500 caracteres): Mejor para recuperación precisa de datos específicos
  - Chunks medianos (500-1500 caracteres): Buen equilibrio para la mayoría de casos
  - Chunks grandes (1500+ caracteres): Mejor para preservar contexto amplio

- **Superposición (overlap)**:
  - Ayuda a mantener contexto entre chunks
  - Típicamente 10-20% del tamaño del chunk
  - Importante para no perder información en los límites

- **Chunking semántico**:
  - Dividir por unidades de significado (párrafos, secciones)
  - Más efectivo que dividir por número fijo de caracteres
  - Preserva la coherencia del contenido

### Evaluación de sistemas RAG

Es importante evaluar el rendimiento de tu sistema RAG:

- **Métricas clave**:
  - Precisión: ¿Las respuestas son correctas?
  - Relevancia: ¿Las respuestas abordan la pregunta?
  - Completitud: ¿Las respuestas incluyen toda la información necesaria?
  - Citación: ¿Las fuentes citadas son correctas y relevantes?

- **Métodos de evaluación**:
  - Comparación con respuestas de referencia
  - Evaluación humana
  - Evaluación automatizada con LLMs
  - Análisis de logs y feedback de usuarios

## Desafío del episodio 11

Para poner en práctica lo aprendido, te invitamos a completar el [desafío del episodio 11](desafio-episodio-11.md), donde crearás un sistema RAG especializado que pueda responder preguntas sobre un tema específico basándose en documentos proporcionados. 