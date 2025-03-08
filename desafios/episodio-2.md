# Episodio 2: Cómo instalar n8n

## Desafío

Instala n8n en tu máquina local usando Docker. Una vez instalado, accede a la interfaz de usuario y toma una captura de pantalla del canvas vacío. Luego, desinstala n8n y vuelve a instalarlo usando npm. Escribe un breve párrafo comparando ambos procesos de instalación (por ejemplo, cuál te pareció más rápido o sencillo).

## Instrucciones

### Instalación con Docker

1. Asegúrate de tener Docker instalado en tu sistema. Si no lo tienes, puedes descargarlo desde [docker.com](https://www.docker.com/products/docker-desktop/).

2. Abre una terminal y ejecuta el siguiente comando:

```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

3. Abre tu navegador y accede a `http://localhost:5678` para ver la interfaz de n8n.

4. Toma una captura de pantalla del canvas vacío.

5. Para detener y eliminar el contenedor, presiona `Ctrl+C` en la terminal donde está ejecutándose Docker.

### Instalación con npm

1. Asegúrate de tener Node.js instalado (versión 16 o superior). Puedes descargarlo desde [nodejs.org](https://nodejs.org/).

2. Abre una terminal y ejecuta el siguiente comando:

```bash
npm install n8n -g
```

3. Una vez instalado, inicia n8n con:

```bash
n8n start
```

4. Abre tu navegador y accede a `http://localhost:5678` para ver la interfaz de n8n.

5. Para detener n8n, presiona `Ctrl+C` en la terminal donde está ejecutándose.

## Entrega

Para completar este desafío, debes:

1. Adjuntar la captura de pantalla del canvas vacío de n8n.
2. Escribir un párrafo comparando ambos métodos de instalación, mencionando:
   - Cuál fue más rápido
   - Cuál fue más sencillo
   - Ventajas y desventajas de cada método
   - Tu método preferido y por qué

## Recursos adicionales

- [Documentación oficial de instalación de n8n](https://docs.n8n.io/hosting/)
- [Guía de Docker para principiantes](https://docs.docker.com/get-started/)
- [Guía de npm para principiantes](https://docs.npmjs.com/about-npm) 