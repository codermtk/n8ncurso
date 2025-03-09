# Episodio 10: Nodos de IA 2 - Agentes, Memoria y Herramientas

## Contenido del episodio
- [Introducción a los Agentes en n8n](#introducción-a-los-agentes-en-n8n)
- [Diferencias entre Chains y Agentes](#diferencias-entre-chains-y-agentes)
- [Componentes de un Agente](#componentes-de-un-agente)
  - [El bucle de razonamiento](#el-bucle-de-razonamiento)
  - [Herramientas disponibles](#herramientas-disponibles)
  - [Sistemas de memoria](#sistemas-de-memoria)
- [Implementando nuestro primer Agente](#implementando-nuestro-primer-agente)
- [Herramientas avanzadas](#herramientas-avanzadas)
  - [Calculadora](#calculadora)
  - [Búsqueda web con SerpAPI](#búsqueda-web-con-serpapi)
  - [Creando herramientas personalizadas](#creando-herramientas-personalizadas)
- [Memoria en Agentes](#memoria-en-agentes)
  - [Tipos de memoria](#tipos-de-memoria)
  - [Memoria de conversación](#memoria-de-conversación)
  - [Memoria persistente](#memoria-persistente)
- [Caso práctico: Asistente de investigación](#caso-práctico-asistente-de-investigación)
- [Desafío del episodio 10](#desafío-del-episodio-10)

## Introducción a los Agentes en n8n

En el episodio anterior, exploramos las Chains como una forma de combinar modelos de lenguaje con prompts específicos para realizar tareas predefinidas. En este episodio, daremos un paso más allá y nos adentraremos en el mundo de los Agentes, que representan un nivel superior de autonomía e inteligencia en nuestros flujos de trabajo.

Los Agentes en n8n son sistemas que pueden:

- Razonar sobre cómo resolver problemas complejos
- Decidir qué herramientas utilizar en cada momento
- Mantener memoria de interacciones previas
- Planificar y ejecutar secuencias de acciones
- Adaptarse a diferentes situaciones y consultas

Esta capacidad de "pensar" y tomar decisiones hace que los Agentes sean especialmente útiles para tareas que requieren flexibilidad, investigación o resolución de problemas en múltiples pasos.

## Diferencias entre Chains y Agentes

Aunque ya mencionamos algunas diferencias en el episodio anterior, es importante profundizar en lo que distingue a los Agentes de las Chains:

| Característica | Chains | Agentes |
|----------------|--------|---------|
| Flujo de trabajo | Predefinido y lineal | Dinámico y adaptativo |
| Toma de decisiones | No tienen capacidad de decisión | Pueden decidir qué acciones tomar |
| Uso de herramientas | Limitado o nulo | Pueden utilizar múltiples herramientas |
| Memoria | Generalmente no mantienen contexto | Pueden mantener memoria de conversaciones |
| Complejidad | Más simples y directas | Más complejos y versátiles |
| Consumo de recursos | Menor (menos tokens) | Mayor (más tokens) |
| Velocidad | Más rápidas | Más lentos debido al proceso de razonamiento |
| Casos de uso | Tareas específicas y bien definidas | Problemas complejos y abiertos |

## Componentes de un Agente

Un Agente en n8n consta de varios componentes esenciales:

### El bucle de razonamiento

El corazón de un Agente es su bucle de razonamiento (reasoning loop), que sigue estos pasos:

1. **Observación**: El Agente recibe una entrada (pregunta, instrucción, etc.)
2. **Pensamiento**: El Agente razona sobre cómo abordar el problema
3. **Decisión**: El Agente decide qué herramienta utilizar o qué acción tomar
4. **Acción**: El Agente ejecuta la acción decidida
5. **Observación de resultados**: El Agente analiza el resultado de la acción
6. **Iteración**: El Agente repite el proceso hasta resolver el problema

Este bucle permite al Agente adaptarse y encontrar soluciones de manera dinámica, similar a cómo un humano abordaría un problema.

### Sistemas de memoria

Los Agentes pueden mantener diferentes tipos de memoria:

- **Memoria a corto plazo**: Para mantener el contexto de la conversación actual
- **Memoria a largo plazo**: Para recordar información de conversaciones anteriores
- **Memoria persistente**: Para almacenar información importante entre sesiones

La memoria permite a los Agentes ofrecer respuestas más coherentes y personalizadas a lo largo del tiempo.

## Implementando nuestro primer Agente

Vamos a implementar un Agente básico que pueda responder preguntas utilizando herramientas cuando sea necesario. Seguiremos estos pasos:

1. **Crear un nuevo workflow**:
   - Nombre: "Asistente Inteligente"
   - Descripción: "Un Agente que puede responder preguntas y utilizar herramientas"

2. **Añadir un nodo Chat Input**:
   - Este será el punto de entrada para las preguntas del usuario

3. **Añadir un nodo Agent**:
   - Conectar con el proveedor de modelo (usaremos Google para este ejemplo)
   - Configurar el System Message para definir el comportamiento del agente
   - Configurar las herramientas que el agente puede utilizar
   - Configurar la memoria para mantener el contexto de la conversación

### Configuración del nodo Agent

La configuración del nodo Agent sería la siguiente:

1. **Conexión al modelo**:
   - Modelo: gemini-2.0-flash
   - Credencial: Tu clave API de Google

2. **System Message**:
   ```
   Eres un asistente inteligente y servicial. Tu objetivo es ayudar al usuario a resolver sus dudas y problemas.
   Cuando necesites información que no conoces o realizar cálculos, utiliza las herramientas disponibles.
   Explica tu razonamiento paso a paso y sé preciso en tus respuestas.
   ```

3. **Herramientas**:
   - Activar la herramienta Calculadora
   - Configurar otras herramientas según sea necesario

4. **Memoria**:
   - Activar la memoria de conversación
   - Configurar el número máximo de mensajes a recordar

5. **Parámetros de generación**:
   - Temperature: 0.2 (para respuestas más precisas)
   - Top P: 0.9


## Memoria en Agentes

La memoria es un componente crucial que permite a los Agentes mantener contexto y ofrecer respuestas coherentes a lo largo del tiempo.

## Desafío del episodio 10

Para poner en práctica lo aprendido, te invitamos a completar el [desafío del episodio 10](desafio-episodio-10.md), donde crearás un Agente de investigación con memoria persistente que pueda buscar información en internet y recordar datos importantes entre sesiones. 