# Desafío del Episodio 8

## Contenido
- [Descripción del desafío](#descripción-del-desafío)
- [Objetivos](#objetivos)
- [Recursos necesarios](#recursos-necesarios)
- [Recursos adicionales](#recursos-adicionales)

## Descripción del desafío

En este desafío, crearás un workflow que utilice la API de Agify para predecir la edad de una persona basándose en su nombre. Luego, compararás esta predicción con la edad real de la persona y, dependiendo del resultado, el flujo tomará diferentes caminos. Este desafío te permitirá aplicar los conceptos aprendidos sobre el nodo HTTP Request, manipulación de strings y control de flujo en n8n.


## Objetivos

Tu workflow debe cumplir con los siguientes objetivos:

1. Utilizar un nodo "Chat Input" para iniciar el workflow y recibir un texto con el formato: `nombre, edad`
   - Ejemplo: `Juan, 35`

2. Utilizar nodos "Set" con expresiones para extraer el nombre y la edad del texto de entrada:
   - Para extraer la edad (último valor después de la coma):
     ```
     {{$json.chatInput.split(",").last()}}
     ```
   - Para extraer el nombre (primer valor antes de la coma):
     ```
     {{$json.chatInput.split(",").first()}}
     ```

3. Utilizar un nodo "HTTP Request" para consultar la API de Agify y obtener la predicción de edad:
   - Método: `GET`
   - URL: `https://api.agify.io`
   - Parámetros de consulta: `name` con el valor del nombre extraído

4. Utilizar un nodo "Set" para extraer la edad predicha de la respuesta de la API y calcular la diferencia con la edad real

5. Utilizar un nodo "Switch" para dirigir el flujo a diferentes ramas según la comparación:
   - Si la edad predicha es mayor que la edad real: rama "Por encima"
   - Si la edad predicha es igual a la edad real: rama "Exacta"
   - Si la edad predicha es menor que la edad real: rama "Por debajo"

6. Utilizar un nodo "Set" en cada rama para añadir un mensaje personalizado:
   - Rama "Por encima": "La predicción se ha pasado por X años"
   - Rama "Exacta": "¡La predicción ha acertado exactamente!"
   - Rama "Por debajo": "La predicción se ha quedado corta por X años"

7. Utilizar un nodo "Merge" para reunir todas las ramas

## Recursos necesarios

- **API de Agify**: https://api.agify.io
  - Esta API predice la edad de una persona basándose en su nombre
  - No requiere autenticación
  - Parámetro requerido: `name` (el nombre de la persona)
  - Ejemplo de URL: `https://api.agify.io?name=Juan`
  - Ejemplo de respuesta:
    ```json
    {
      "name": "Juan",
      "age": 42,
      "count": 25886
    }
    ```


## Recursos adicionales

- [Documentación de la API de Agify](https://agify.io/)
- [Documentación del nodo HTTP Request](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/)
- [Documentación del nodo Set](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.set/)
- [Documentación del nodo Switch](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.switch/)
- [Documentación del nodo Merge](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.merge/)
- [Guía de expresiones en n8n](https://docs.n8n.io/code-examples/expressions/) 
