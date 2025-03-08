# Desafío 1: Instalación de n8n

![Imagen de n8n instalado](https://docs.n8n.io/assets/img/workflow-demo.a9a7bc2e.gif)

## Objetivo

Instalar n8n en tu máquina local utilizando dos métodos diferentes: Docker y npm. Comparar ambos métodos para entender sus ventajas y desventajas.

## Contexto

Antes de comenzar a crear flujos de trabajo, necesitas instalar n8n en tu entorno local. Existen diferentes métodos para hacerlo, cada uno con sus propias ventajas. En este desafío, explorarás dos de los métodos más comunes: Docker y npm.

## Requisitos

- Conocimientos básicos de línea de comandos
- Docker instalado (para el primer método)
- Node.js v16 o superior instalado (para el segundo método)

## El desafío

1. **Instalación con Docker**
   - Investiga cómo ejecutar n8n utilizando Docker
   - Instala n8n usando Docker
   - Accede a la interfaz web de n8n
   - Toma una captura de pantalla del canvas vacío

2. **Instalación con npm**
   - Desinstala la versión de Docker
   - Instala n8n globalmente usando npm
   - Inicia n8n y accede a la interfaz web
   - Toma otra captura de pantalla

3. **Comparación**
   - Escribe un breve párrafo comparando ambos métodos de instalación:
     - ¿Cuál fue más rápido?
     - ¿Cuál fue más sencillo?
     - ¿Qué ventajas y desventajas tiene cada método?
     - ¿Cuál preferirías usar en el futuro y por qué?

## Pistas

- Para Docker, necesitarás usar el comando `docker run` con los parámetros adecuados
- Para npm, el comando principal es `npm install n8n -g`
- La interfaz web de n8n suele estar disponible en `http://localhost:5678`
- Recuerda que Docker aísla la aplicación en un contenedor, mientras que npm la instala directamente en tu sistema

## Entrega

Para completar este desafío, debes entregar:

1. Captura de pantalla del canvas vacío de n8n instalado con Docker
2. Captura de pantalla del canvas vacío de n8n instalado con npm
3. Tu análisis comparativo de ambos métodos de instalación (300-400 palabras)

## Recursos

- [Documentación oficial de instalación de n8n](https://docs.n8n.io/hosting/)
- [Guía de Docker para principiantes](https://docs.docker.com/get-started/)
- [Guía de npm para principiantes](https://docs.npmjs.com/about-npm) 