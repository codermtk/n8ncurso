# Episodio 7: Nodos de Lógica (Flow)

## Desafío

Crea un workflow que simule un sistema de entradas de cine. Usa un nodo "Set" para definir la edad de una persona (por ejemplo, {"edad": 16}) y luego usa un nodo "If" para determinar si puede ver una película clasificada para mayores de 18 años. Si es menor, muestra un mensaje de "Acceso denegado"; si es mayor, "Acceso permitido".

## Instrucciones

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador (http://localhost:5678).
2. Crea un nuevo workflow y nómbralo "Sistema de Entradas de Cine".

### Paso 2: Configurar el nodo "Manual Trigger"

1. Añade un nodo "Manual Trigger" al canvas.
2. No es necesario configurar nada en este nodo, ya que simplemente iniciará el workflow manualmente.

### Paso 3: Configurar el nodo "Set" para definir la edad

1. Añade un nodo "Set" después del "Manual Trigger".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el campo con:
   - Name: `edad`
   - Type: `Number`
   - Value: `16` (puedes cambiar este valor para probar diferentes escenarios)
4. Guarda la configuración del nodo.

### Paso 4: Configurar el nodo "If"

1. Añade un nodo "If" después del nodo "Set".
2. En la configuración del nodo "If", configura los siguientes parámetros:
   - Value 1: `{{$json.edad}}`
   - Operation: `Larger or Equal`
   - Value 2: `18`
3. Guarda la configuración del nodo.

### Paso 5: Configurar los nodos "Set" para las respuestas

1. Añade un nodo "Set" conectado a la salida "true" del nodo "If".
2. Configura este nodo con:
   - Name: `mensaje`
   - Type: `String`
   - Value: `Acceso permitido`
3. Guarda la configuración del nodo.

4. Añade otro nodo "Set" conectado a la salida "false" del nodo "If".
5. Configura este nodo con:
   - Name: `mensaje`
   - Type: `String`
   - Value: `Acceso denegado`
6. Guarda la configuración del nodo.

### Paso 6: Ejecutar y verificar el workflow

1. Haz clic en "Execute Workflow" para ejecutar el workflow.
2. Una vez completada la ejecución, observa qué camino ha tomado el flujo de datos.
3. Verifica que el mensaje generado sea el correcto según la edad definida.
4. Cambia el valor de la edad en el primer nodo "Set" y ejecuta el workflow nuevamente para ver cómo cambia el resultado.

## Entrega

Para completar este desafío, debes:

1. Adjuntar una captura de pantalla del canvas con todos los nodos conectados.
2. Adjuntar dos capturas de pantalla mostrando los resultados con diferentes edades (una menor de 18 y otra mayor o igual a 18).
3. Responder a las siguientes preguntas:
   - ¿Qué otros operadores de comparación ofrece el nodo "If"?
   - ¿Cómo podrías modificar este workflow para incluir una categoría adicional para películas clasificadas para mayores de 13 años?
   - ¿Qué otros nodos de lógica ofrece n8n y para qué podrían ser útiles?

## Conceptos clave

- **Nodo If**: Cómo implementar lógica condicional en tus workflows.
- **Ramificación de flujos**: Cómo los datos pueden seguir diferentes caminos según ciertas condiciones.
- **Operadores de comparación**: Diferentes formas de comparar valores en n8n.
- **Toma de decisiones automatizada**: Cómo automatizar decisiones basadas en datos.

## Recursos adicionales

- [Documentación del nodo If](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.if/)
- [Guía de nodos de lógica en n8n](https://docs.n8n.io/workflows/flow-logic/)
- [Patrones de diseño de workflows](https://docs.n8n.io/workflows/best-practices/) 