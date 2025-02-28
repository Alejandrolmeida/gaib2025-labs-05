# Ejercicio 3 - Integración con Modelos de Azure AI

## Objetivo
Aprender a integrar un modelo de **Azure AI** en un flujo de **PromptFlow**.

## Pasos

### 1. Configurar el Acceso a Azure AI
Ejecuta los siguientes comandos para autenticarte y configurar los servicios necesarios:
```bash
az login
az ml workspace list
az account set --subscription "<ID de tu suscripción>"
```

### 2. Crear un Flujo con un Modelo de Azure AI
Edita el archivo `flow.dag.yaml` y agrega la siguiente configuración:
```yaml
nodes:
  - name: input_node
    type: input
    schema:
      text: string

  - name: azure_ai_model
    type: azure-ai
    model_name: "text-davinci-003"
    dependencies: [input_node]
    parameters:
      max_tokens: 100

  - name: output_node
    type: output
    dependencies: [azure_ai_model]
```

### 3. Ejecutar el Flujo con Azure AI
Corre el flujo de trabajo con:
```bash
promptflow run
```
Si recibes una respuesta generada por el modelo de Azure AI, ¡has completado con éxito este ejercicio!
