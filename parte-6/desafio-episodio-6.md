# Desafío del Episodio 6

## Contenido
- [Descripción del desafío](#descripción-del-desafío)
- [Requisitos previos](#requisitos-previos)
- [Objetivos](#objetivos)
- [Datos de ejemplo](#datos-de-ejemplo)
- [Recursos adicionales](#recursos-adicionales)

## Descripción del desafío

En este desafío, crearás un workflow que procese datos de ventas de entradas de cine utilizando varios nodos de datos en n8n. Deberás aplicar los conceptos aprendidos sobre tipos de datos, transformación de datos y agregación utilizando el nodo Summarize.

![Desafío 6](../images/parte6/cine.png)

## Requisitos previos

- Tener n8n instalado y funcionando
- Conocimientos básicos sobre nodos de datos en n8n

## Objetivos

Tu workflow debe cumplir con los siguientes objetivos:

1. Crear un formulario que permita subir un archivo CSV con datos de ventas de entradas de cine
2. Procesar el archivo CSV para extraer los datos
3. Transformar los datos de la columna "entradas" de string a número
4. Filtrar las películas para mostrar solo las que contengan el género "Comedy"
6. Utilizar el nodo Summarize para calcular:
   - El total de entradas vendidas para películas de comedia

## Datos

Los datos se encuentran dentro de la comunidad de Skool

## Recursos adicionales

- [Documentación del nodo Form Trigger](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.formtrigger/)
- [Documentación del nodo Extract from File](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.extractfromfile/)
- [Documentación del nodo Filter](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.filter/)
- [Documentación del nodo Set](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.set/)
- [Documentación del nodo Summarize](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.summarize/)
- [Guía de manipulación de datos en n8n](https://docs.n8n.io/data/) 
