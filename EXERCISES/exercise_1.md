# Ejercicio 1 - Configuración del Entorno

## Objetivo
Configurar correctamente el entorno de desarrollo para poder trabajar con **Microsoft AI Foundry** y **PromptFlow**.

## Pasos

### 1. Crear y Activar un Entorno Virtual
Ejecuta los siguientes comandos en tu terminal o consola de comandos:
```bash
python -m venv ai_foundry_env
source ai_foundry_env/bin/activate  # En Windows usar `ai_foundry_env\Scripts\activate`
```

### 2. Instalar Dependencias Necesarias
Instala los paquetes requeridos con:
```bash
pip install --upgrade pip
pip install promptflow azure-ai-ml
```

### 3. Configurar la CLI de Azure
Asegúrate de iniciar sesión en Azure y seleccionar la suscripción correcta:
```bash
az login
az account set --subscription "<ID de tu suscripción>"
```

### 4. Verificación de Instalación
Verifica que la instalación de **PromptFlow** fue exitosa ejecutando:
```bash
python -c "import promptflow; print(promptflow.__version__)"
```
Si ves una versión impresa sin errores, ¡has completado con éxito este ejercicio!