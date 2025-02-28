# Ejercicio 2 - Creación de un Flujo en PromptFlow

## Objetivo
Crear y ejecutar un flujo básico en **PromptFlow** para procesar datos.

## Pasos

### 1. Crear un Proyecto de PromptFlow
Ejecuta los siguientes comandos:
```bash
mkdir my_promptflow_project && cd my_promptflow_project
promptflow init
```

### 2. Definir un Flujo Básico
Crea un archivo `flow.dag.yaml` con el siguiente contenido:
```yaml
nodes:
  - name: input_node
    type: input
    schema:
      text: string

  - name: uppercase_node
    type: transform
    script: |
      def transform(data):
          return {"text": data["text"].upper()}
    dependencies: [input_node]

  - name: output_node
    type: output
    dependencies: [uppercase_node]
```

### 3. Ejecutar el Flujo
Corre el flujo con:
```bash
promptflow run
```

Si el resultado muestra el texto en mayúsculas, ¡has completado con éxito este ejercicio!
