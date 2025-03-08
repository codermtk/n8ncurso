# Desafío 1: Instalación de n8n

![Imagen de n8n instalado](https://docs.n8n.io/assets/img/workflow-demo.a9a7bc2e.gif)

## Contenidos

### Instalación con npm

Para instalar n8n utilizando npm, necesitas tener Node.js (versión 16 o superior) instalado en tu sistema. Luego, ejecuta el siguiente comando:

```bash
npm install n8n -g
```

Una vez instalado, puedes iniciar n8n con:

```bash
n8n start
```

### Instalación con Docker Desktop

Para instalar n8n utilizando Docker Desktop:

1. Abre Docker Desktop
2. Ve a la pestaña "Images"
3. Busca "n8nio/n8n" en el campo de búsqueda
4. Haz clic en "Pull" para descargar la imagen
5. Una vez descargada, haz clic en "Run"
6. Configura los puertos (mapea el puerto 5678 del contenedor al puerto 5678 de tu máquina)
7. Opcionalmente, configura un volumen para persistir los datos
8. Haz clic en "Run" para iniciar el contenedor

Alternativamente, puedes usar el siguiente comando en la terminal:

```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

### Actualización de n8n

#### Actualizar con npm

Para actualizar n8n cuando lo has instalado con npm:

```bash
npm update -g n8n
```

#### Actualizar con Docker

Para actualizar n8n cuando lo has instalado con Docker Desktop:

1. Ve a la pestaña "Images" en Docker Desktop
2. Localiza la imagen "n8nio/n8n"
3. Haz clic en los tres puntos (⋮) junto a la imagen
4. Selecciona "Pull" para descargar la última versión
5. Detén y elimina el contenedor actual si está en ejecución
6. Inicia un nuevo contenedor con la imagen actualizada

#### Actualizar en Railway

Si has desplegado n8n en Railway, para actualizarlo simplemente:

1. Ve a tu proyecto en el dashboard de Railway
2. Haz clic en "Redeploy"

### Desinstalación de n8n

#### Desinstalar la versión npm

Para desinstalar n8n cuando lo has instalado con npm:

```bash
npm uninstall -g n8n
```

#### Desinstalar la versión Docker

Para desinstalar n8n cuando lo has instalado con Docker:

1. Detén y elimina el contenedor
2. Elimina la imagen si ya no la necesitas:
   ```bash
   docker rmi n8nio/n8n
   ```

## Desafío

### Objetivo

Instalar n8n en tu máquina local utilizando dos métodos diferentes: Docker y npm. Comparar ambos métodos para entender sus ventajas y desventajas.

### Contexto

Antes de comenzar a crear flujos de trabajo, necesitas instalar n8n en tu entorno local. Existen diferentes métodos para hacerlo, cada uno con sus propias ventajas. En este desafío, explorarás dos de los métodos más comunes: Docker y npm.

### Requisitos

- Conocimientos básicos de línea de comandos
- Docker instalado (para el primer método)
- Node.js v16 o superior instalado (para el segundo método)

### El desafío

1. **Instalación con Docker**
   - Instala n8n usando Docker Desktop o el comando Docker
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

### Pistas

- La interfaz web de n8n suele estar disponible en `http://localhost:5678`
- Recuerda que Docker aísla la aplicación en un contenedor, mientras que npm la instala directamente en tu sistema
- Considera aspectos como la facilidad de actualización y desinstalación en tu comparación

### Entrega

Para completar este desafío, debes entregar:

1. Captura de pantalla del canvas vacío de n8n instalado con Docker
2. Captura de pantalla del canvas vacío de n8n instalado con npm
3. Tu análisis comparativo de ambos métodos de instalación (300-400 palabras)

## Recursos

- [Documentación oficial de instalación de n8n](https://docs.n8n.io/hosting/)
- [Guía de Docker para principiantes](https://docs.docker.com/get-started/)
- [Guía de npm para principiantes](https://docs.npmjs.com/about-npm) 