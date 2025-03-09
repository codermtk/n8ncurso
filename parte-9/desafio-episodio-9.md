# Desafío del Episodio 9: Creando un Asistente Pirata con LLM Chain

## Contenido
- [Descripción del desafío](#descripción-del-desafío)
- [Objetivos](#objetivos)
- [Recursos necesarios](#recursos-necesarios)
- [Recursos adicionales](#recursos-adicionales)

## Descripción del desafío

En este desafío, pondrás en práctica lo aprendido sobre los nodos de IA en n8n creando un asistente virtual con personalidad de pirata. Este asistente deberá responder preguntas, contar historias del mar, utilizar jerga pirata y mantener el carácter durante toda la interacción.

Este proyecto te permitirá experimentar con las system prompts para definir personalidades en modelos de lenguaje, así como practicar la configuración de parámetros.

![Desafío 9](../images/parte9/pirata.jpg)

## Objetivos

Tu asistente pirata debe cumplir con los siguientes requisitos:

1. **Personalidad consistente**: Mantener el carácter de pirata en todas sus respuestas, utilizando vocabulario y expresiones típicas de piratas.

2. **Capacidades conversacionales**:
   - Responder preguntas generales desde la perspectiva de un pirata
   - Contar historias de aventuras en el mar cuando se le solicite
   - Describir tesoros, barcos y otros elementos del mundo pirata
   - Convertir frases normales a "habla pirata"

## Recursos necesarios

### Credenciales de un modelo de lenguaje

Para este desafío, necesitarás acceso a un modelo de lenguaje. Recomiendo utilizar Gemini de Google, ya que hay modelos muy buenos y son gratuitos, pero puedes utilizar cualquiera de estos proveedores:

- **Google AI (Gemini)**: [Consigue una API key aquí](https://aistudio.google.com/apikey)
- **OpenAI**: [Consigue una API key aquí](https://platform.openai.com/)
- **Anthropic (Claude)**: [Consigue una API key aquí](https://www.anthropic.com/product)
- **Ollama**: Para ejecutar modelos localmente [Instrucciones de instalación](https://ollama.ai/)

### Ejemplos de jerga pirata

Para ayudarte a diseñar un buen prompt de sistema, aquí tienes algunos ejemplos de expresiones piratas:

- "¡Arr!" - Expresión general de emoción o acuerdo
- "¡Ahoy, marinero!" - Saludo
- "Avast ye" - Prestar atención
- "Shiver me timbers" - Expresión de sorpresa
- "Yo-ho-ho" - Risa o celebración
- "Camina por la plancha" - Amenaza
- "Botín" - Tesoro o recompensa
- "Grumete" - Marinero novato
- "Galeón" - Tipo de barco
- "Davy Jones' locker" - El fondo del mar (muerte)

## Recursos adicionales

- [Guía de Google AI para Gemini](https://ai.google.dev/docs/gemini_api_overview)

## Conceptos clave

- **Prompts de sistema**: Cómo definir personalidades y comportamientos específicos en modelos de lenguaje.
- **Parámetros de generación**: Cómo ajustar la creatividad y estilo de las respuestas.
