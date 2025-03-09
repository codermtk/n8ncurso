# Desafío del Episodio 4

## Contenido del desafío
- [Desafío](#desafío)
- [Instrucciones de Solución](#instrucciones-de-solución)
  - [Paso 1: Crear un nuevo workflow](#paso-1-crear-un-nuevo-workflow)
  - [Paso 2: Configurar el nodo "Manual Trigger"](#paso-2-configurar-el-nodo-manual-trigger)
  - [Paso 3: Configurar el nodo "Set"](#paso-3-configurar-el-nodo-set)
  - [Paso 4: Ejecutar y visualizar el workflow](#paso-4-ejecutar-y-visualizar-el-workflow)
- [Extensión del desafío (opcional)](#extensión-del-desafío-opcional)
- [Conceptos clave](#conceptos-clave)
- [Recursos adicionales](#recursos-adicionales)

## Desafío

Construye un workflow que use un "Manual Trigger" y un nodo "Set" para crear tu primer dato artificial: un objeto JSON con tu nombre y apellido (por ejemplo, {"nombre": "Juan", "apellido": "García"}). Ejecuta el workflow y visualiza el resultado en diferentes formatos (JSON, Table y Schema).

![Desafío Parte 4](../images/parte4/desafioparte4.png)

## Instrucciones de Solución

### Paso 1: Crear un nuevo workflow

1. Accede a la interfaz de n8n en tu navegador.
2. Crea un nuevo workflow y nómbralo "Mi Primer Dato".

### Paso 2: Configurar el nodo "Manual Trigger"

1. Añade un nodo "Manual Trigger" al canvas.
2. No es necesario configurar nada en este nodo, ya que simplemente iniciará el workflow manualmente.

### Paso 3: Configurar el nodo "Set"

1. Añade un nodo "Set" después del "Manual Trigger".
2. En la configuración del nodo "Set", haz clic en "Add Value" para añadir un nuevo campo.
3. Configura el primer campo con:
   - Name: `nombre`
   - Type: `String`
   - Value: `[Tu nombre]` (reemplaza con tu nombre real)
4. Haz clic en "Add Value" nuevamente para añadir otro campo.
5. Configura el segundo campo con:
   - Name: `apellido`
   - Type: `String`
   - Value: `[Tu apellido]` (reemplaza con tu apellido real)
6. Guarda la configuración del nodo.

### Paso 4: Ejecutar y visualizar el workflow

1. Haz clic en "Test Workflow" para ejecutar el workflow.
2. Una vez completada la ejecución, haz clic en el nodo "Set" para ver el resultado.
3. En el panel que se abre, explora las diferentes vistas:
   - **JSON**: Muestra la estructura completa de los datos
   - **Table**: Presenta los datos en formato de tabla
   - **Schema**: Muestra el esquema de los datos (tipos y estructura)

## Extensión del desafío (opcional)

Si quieres llevar este desafío un paso más allá, puedes:

1. Añadir un segundo nodo "Set" que combine el nombre y apellido en un campo "nombreCompleto".
2. Utilizar el modo Expression para crear este campo, con una expresión como:
   ```
   {{ $json.nombre + " " + $json.apellido }}
   ```
3. Añadir todo el resto de campos que quieras como "edad", "ciudad" o "profesión".
   ```


## Conceptos clave

- **JSON (JavaScript Object Notation)**: Un formato ligero de intercambio de datos.
- **Nodo Set**: Permite definir valores estáticos o dinámicos en un workflow.
- **Modos Fixed vs Expression**: Diferentes formas de configurar valores en n8n.
- **Visualización de datos**: Diferentes formas de ver y entender los datos en n8n.

## Recursos adicionales

- [Documentación del nodo Set](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.set/)
- [Guía de expresiones en n8n](https://docs.n8n.io/code-examples/expressions/)
- [Guía de JSON](https://www.json.org/json-es.html) 
