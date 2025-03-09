# Episodio 2: Cómo instalar n8n

## Contenido del episodio
- [Métodos de instalación](#métodos-de-instalación)
  - [Instalación con npm](#instalación-con-npm)
  - [Instalación con Docker](#instalación-con-docker)
  - [Instalación en Railway](#instalación-en-railway)
  - [n8n Cloud (Hosting Oficial)](#n8n-cloud-hosting-oficial)
- [Actualización de n8n](#actualización-de-n8n)
  - [Actualizar con npm](#actualizar-con-npm)
  - [Actualizar con Docker](#actualizar-con-docker)
  - [Actualizar en Railway](#actualizar-en-railway)
- [Desinstalación de n8n](#desinstalación-de-n8n)
  - [Desinstalar la versión npm](#desinstalar-la-versión-npm)
  - [Desinstalar la versión Docker](#desinstalar-la-versión-docker)
  - [Desinstalar en Railway](#desinstalar-en-railway)
- [Acceso a la interfaz](#acceso-a-la-interfaz)
- [Recursos](#recursos)

## Métodos de instalación

Existen varias formas de hostear localmente n8n en tu sistema. Las más comunes son:
- npm (Node Package Manager) 
- Docker 
- Railway (hosting en la nube)
- n8n Cloud (hosting oficial)

Cada método tiene sus ventajas y desventajas.

### Instalación con npm

Para instalar n8n utilizando npm, necesitas tener Node.js (versión 16 o superior) instalado en tu sistema. Luego, ejecuta el siguiente comando:

```bash
npm install n8n -g
```

Una vez instalado, puedes iniciar n8n con:

```bash
n8n start
```

### Instalación con Docker

#### Usando la línea de comandos

Para instalar n8n utilizando Docker desde la línea de comandos:

```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

#### Usando Docker Desktop

Para instalar n8n utilizando Docker Desktop:

1. Abre Docker Desktop
2. Ve a la pestaña "Images"
3. Busca "n8nio/n8n" en el campo de búsqueda
4. Haz clic en "Pull" para descargar la imagen
5. Una vez descargada, haz clic en "Run"
6. Configura los puertos (mapea el puerto 5678 del contenedor al puerto 5678 de tu máquina)
7. Opcionalmente, configura un volumen para persistir los datos
8. Haz clic en "Run" para iniciar el contenedor

### Instalación en Railway

Railway es una plataforma de hosting en la nube que permite desplegar n8n de manera sencilla y económica (desde $5 al mes), siendo una excelente alternativa al hosting oficial.

Para instalar n8n en Railway:

1. Visita el template de n8n en Railway: [https://railway.app/template/r2SNX_](https://railway.app/template/r2SNX_)
2. Haz clic en "Deploy on Railway"
3. Inicia sesión o crea una cuenta en Railway
4. Configura las variables de entorno necesarias (opcional)
5. Haz clic en "Deploy" para iniciar el despliegue

Una vez completado el despliegue, Railway te proporcionará una URL para acceder a tu instancia de n8n. El proceso toma aproximadamente 2-3 minutos.

#### Ventajas de Railway:
- Costo accesible (desde $5 al mes)
- Despliegue rápido y sencillo
- Escalabilidad automática
- No requiere configuración de infraestructura
- Excelente rendimiento y estabilidad

### n8n Cloud (Hosting Oficial)

n8n ofrece su propio servicio de hosting oficial con diferentes planes según tus necesidades.

Para utilizar n8n Cloud:

1. Visita [https://www.n8n.io/pricing/](https://www.n8n.io/pricing/)
2. Selecciona el plan que mejor se adapte a tus necesidades, aunque tienes una prueba gratuita de 14 días muy recomendable para comenzar a aprender n8n
3. Regístrate y configura tu cuenta
4. Accede a tu instancia de n8n a través de la URL que te proporcionen

#### Comparativa con Railway:
- **Costo**: n8n Cloud comienza desde €20/mes (plan Starter), mientras que Railway cuesta desde $5/mes
- **Soporte**: n8n Cloud ofrece soporte oficial y actualizaciones automáticas
- **Características adicionales**: n8n Cloud incluye características exclusivas según el plan seleccionado
- **Facilidad de uso**: Ambas opciones son fáciles de configurar, pero n8n Cloud está optimizado específicamente para n8n

## Actualización de n8n

Es importante mantener n8n actualizado para aprovechar las nuevas funcionalidades y correcciones de errores.

### Actualizar con npm

Para actualizar n8n cuando lo has instalado con npm:

```bash
npm update -g n8n
```

### Actualizar con Docker

Para actualizar n8n cuando lo has instalado con Docker Desktop:

1. Ve a la pestaña "Images" en Docker Desktop
2. Localiza la imagen "n8nio/n8n"
3. Haz clic en los tres puntos (⋮) junto a la imagen
4. Selecciona "Pull" para descargar la última versión
5. Detén y elimina el contenedor actual si está en ejecución
6. Inicia un nuevo contenedor con la imagen actualizada

Si estás utilizando la línea de comandos, puedes actualizar la imagen con:

```bash
docker pull n8nio/n8n
```

### Actualizar en Railway

Si has desplegado n8n en Railway, para actualizarlo simplemente:

1. Ve a tu proyecto en el dashboard de Railway
2. Haz clic en "Redeploy"

## Desinstalación de n8n

### Desinstalar la versión npm

Para desinstalar n8n cuando lo has instalado con npm:

```bash
npm uninstall -g n8n
```

### Desinstalar la versión Docker

Para desinstalar n8n cuando lo has instalado con Docker:

1. Detén y elimina el contenedor
2. Elimina la imagen si ya no la necesitas:
   ```bash
   docker rmi n8nio/n8n
   ```

### Desinstalar en Railway

Para desinstalar n8n de Railway:

1. Ve a tu proyecto en el dashboard de Railway
2. Haz clic en "Settings"
3. Desplázate hacia abajo hasta la sección "Danger Zone"
4. Haz clic en "Delete Project"

## Acceso a la interfaz

Una vez instalado n8n, puedes acceder a la interfaz web a través de:

- **Instalación local (npm o Docker)**: `http://localhost:5678`
- **Railway**: A través de la URL proporcionada por Railway
- **n8n Cloud**: A través de la URL proporcionada por n8n

## Recursos

- [Documentación oficial de instalación de n8n](https://docs.n8n.io/hosting/)
- [Guía de Docker para principiantes](https://docs.docker.com/get-started/)
- [Guía de npm para principiantes](https://docs.npmjs.com/about-npm)
- [Railway](https://railway.app/)
- [n8n Cloud](https://www.n8n.io/cloud/) 