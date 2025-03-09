# Desafío del Episodio 7

## Contenido
- [Descripción del desafío](#descripción-del-desafío)
- [Objetivos](#objetivos)
- [Datos de ejemplo](#datos-de-ejemplo)
- [Recursos adicionales](#recursos-adicionales)

## Descripción del desafío

En este desafío, crearás un workflow que procese un archivo CSV con notas de estudiantes, los clasifique en diferentes categorías según su calificación y extraiga información específica sobre los mejores y peores estudiantes. Deberás aplicar los conceptos aprendidos sobre operadores lógicos y nodos de control de flujo.

![Desafío 7](../images/parte7/notas.png)

## Objetivos

Tu workflow debe cumplir con los siguientes objetivos:

1. Crear un formulario que permita subir un archivo CSV con datos de estudiantes (nombre, apellido y nota) (el archivo se encuentra dentro de skool)

2. Procesar el archivo CSV para extraer los datos, asegurarte de que la nota se trata como un valor numérico y de que no haya alumnos sin puntuar en los datos con los que se trabaja

3. Clasificar a los estudiantes en las siguientes categorías según su nota:
   - **Suspenso**: Nota < 5
   - **Suficiente**: Nota >= 5 y < 6
   - **Bien**: Nota >= 6 y < 7
   - **Notable**: Nota >= 7 y < 9
   - **Sobresaliente**: Nota >= 9 y <= 10

4. Para cada categoría, crear una rama separada en el workflow

5. Dentro del grupo de "Sobresalientes", identificar a los tres estudiantes con las mejores notas

6. Dentro del grupo de "Suspensos", identificar a los tres estudiantes con las peores notas


## Datos 

Los datos se encuentran dentro de la comunidad de Skool

## Recursos adicionales

- [Documentación del nodo Filter](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.filter/)
- [Documentación del nodo Switch](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.switch/)
- [Documentación del nodo Sort](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.sort/)
- [Documentación del nodo Limit](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.limit/)
- [Documentación del nodo Merge](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.merge/) 
