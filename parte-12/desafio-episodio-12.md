# Desafío del Episodio 12: Asistente de Correo Inteligente

## Contenido
- [Descripción del desafío](#descripción-del-desafío)
- [Objetivos](#objetivos)
- [Recursos necesarios](#recursos-necesarios)
- [Entrega](#entrega)
- [Recursos adicionales](#recursos-adicionales)

## Descripción del desafío

En este desafío final, crearás un asistente de correo electrónico inteligente que combine las capacidades de IA con la integración de Gmail. Este asistente será capaz de recibir consultas por correo electrónico, analizarlas, generar respuestas apropiadas utilizando un agente de IA, y enviar estas respuestas automáticamente.

Este proyecto te permitirá aplicar los conocimientos adquiridos sobre nodos In App y combinarlos con las capacidades de IA que hemos explorado en episodios anteriores, creando una solución práctica y útil.

## Objetivos

Tu asistente de correo inteligente debe cumplir con los siguientes requisitos:

1. **Recepción de correos**:
   - Configurar un trigger de Gmail para detectar nuevos correos

2. **Procesamiento con IA**:
   - Extraer el contenido relevante del correo
   - Utilizar un agente de IA para analizar la consulta y generar una respuesta apropiada
   - El agente debe poder utilizar herramientas si es necesario (búsqueda web, etc.)

3. **Respuesta automática**:
   - Formatear la respuesta generada por el agente
   - Enviar un correo de respuesta al remitente original
   - Incluir información de contacto o recursos adicionales si es apropiado

## Recursos necesarios

### Cuenta de Gmail

Para este desafío, necesitarás:

1. **Cuenta de Gmail**:
   - Una cuenta de Gmail que puedas utilizar para pruebas
   - Configuración de seguridad que permita el acceso de aplicaciones menos seguras o una contraseña de aplicación

2. **Credenciales de OAuth**:
   - Configurar OAuth para permitir que n8n acceda a tu cuenta de Gmail
   - Seguir las instrucciones de n8n para configurar las credenciales de Google

### Modelo de lenguaje

Para el componente de IA, necesitarás:

1. **API key para un modelo de lenguaje**:
   - Puedes utilizar OpenAI, Google AI (Gemini), Anthropic o cualquier otro proveedor compatible
   - Asegúrate de tener suficientes créditos para las pruebas

2. **Prompt de sistema para el agente**:
   - Diseñar un prompt que defina el comportamiento del asistente
   - Incluir instrucciones sobre cómo responder a diferentes tipos de consultas

## Recursos adicionales

- [Documentación de n8n sobre Gmail](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.gmail/)
- [Guía de autenticación con Google](https://docs.n8n.io/integrations/builtin/credentials/google/)
