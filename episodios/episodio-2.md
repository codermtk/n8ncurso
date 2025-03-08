# Episodio 2: Cómo instalar n8n

![Instalación de n8n](https://docs.n8n.io/assets/img/quickstart-cli.a9a7bc2e.gif)

## Métodos de instalación

Existen varias formas de instalar n8n en tu sistema. Las más comunes son mediante npm (Node Package Manager) y Docker. Cada método tiene sus ventajas y desventajas.

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

## Acceso a la interfaz

Una vez instalado n8n, puedes acceder a la interfaz web a través de tu navegador en:

```
http://localhost:5678
```

## Recursos

- [Documentación oficial de instalación de n8n](https://docs.n8n.io/hosting/)
- [Guía de Docker para principiantes](https://docs.docker.com/get-started/)
- [Guía de npm para principiantes](https://docs.npmjs.com/about-npm) 