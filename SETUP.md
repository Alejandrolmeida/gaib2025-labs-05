# Configuración del Entorno

## Requisitos Previos
Antes de comenzar, asegúrate de contar con lo siguiente:
- Cuenta de **Microsoft Azure** con permisos adecuados.
- **Python 3.9+** instalado.
- **Visual Studio Code** con la extensión de **Azure Machine Learning**.
- **PromptFlow SDK** instalado en tu entorno.

## Instalación de Herramientas
1. **Instalar Python y dependencias**
   ```bash
   python -m venv ai_foundry_env
   source ai_foundry_env/bin/activate  # En Windows usar `ai_foundry_env\Scripts\activate`
   pip install --upgrade pip
   pip install promptflow azure-ai-ml
   ```

2. **Configurar la CLI de Azure**
   ```bash
   az login
   az account set --subscription "<ID de tu suscripción>"
   ```

3. **Configurar el entorno de trabajo**
   ```bash
   mkdir ai_foundry_project && cd ai_foundry_project
   git init
   ```

## Verificación de la Configuración
Para asegurarte de que todo está correctamente instalado, ejecuta:
```bash
python -c "import promptflow; print(promptflow.__version__)"
```
Si ves una versión sin errores, ¡ya estás listo para empezar!