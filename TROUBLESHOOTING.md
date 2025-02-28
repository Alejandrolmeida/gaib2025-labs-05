# Solución de Problemas

## Problemas Comunes y Soluciones

### 1. Error al Instalar `promptflow`
#### Problema:
```bash
ERROR: Could not find a version that satisfies the requirement promptflow
```
#### Solución:
Asegúrate de estar usando Python 3.9 o superior. Ejecuta:
```bash
python --version
pip install --upgrade pip setuptools wheel
pip install promptflow
```

### 2. No se Puede Autenticar con Azure
#### Problema:
```bash
az login
ERROR: Please install the latest version of Azure CLI
```
#### Solución:
Actualiza la CLI de Azure:
```bash
az upgrade
```
Luego, intenta nuevamente iniciar sesión:
```bash
az login
```

### 3. `promptflow run` No Ejecuta el Flujo
#### Problema:
```bash
promptflow run
ERROR: No valid flow.dag.yaml found
```
#### Solución:
Verifica que el archivo `flow.dag.yaml` esté en el directorio correcto y tenga una sintaxis válida.