# Ejercicio 5 - Búsquedas Semánticas con Azure AI Search

## Objetivo
Aprender a configurar un índice en **Azure AI Search**, cargar datos y realizar búsquedas semánticas.

## Pasos

### 1. Crear un Servicio de Azure AI Search
Ejecuta el siguiente comando para crear el servicio:
```bash
az search service create --name mi-search-service --resource-group mi-grupo --sku free
```

### 2. Crear un Índice en Azure AI Search
Crea un archivo `create_index.json` con la siguiente configuración:
```json
{
    "name": "productos",
    "fields": [
        {"name": "id", "type": "Edm.String", "key": true},
        {"name": "nombre", "type": "Edm.String", "searchable": true},
        {"name": "descripcion", "type": "Edm.String", "searchable": true},
        {"name": "categoria", "type": "Edm.String", "filterable": true}
    ]
}
```
Ejecuta:
```bash
az search index create --service-name mi-search-service --name productos --data create_index.json
```

### 3. Insertar Datos en el Índice
Crea `insert_data.py` con el siguiente código:
```python
import requests

endpoint = "<URL_DE_AZURE_SEARCH>"
api_key = "<CLAVE_DE_AZURE_SEARCH>"
headers = {"Content-Type": "application/json", "api-key": api_key}

data = {
    "value": [
        {"id": "1", "nombre": "Laptop", "descripcion": "Computadora portátil rápida", "categoria": "Electrónica"},
        {"id": "2", "nombre": "Silla ergonómica", "descripcion": "Silla de oficina con soporte lumbar", "categoria": "Muebles"}
    ]
}

response = requests.post(f"{endpoint}/indexes/productos/docs/index", headers=headers, json=data)
print(response.json())
```
Ejecuta:
```bash
python insert_data.py
```

### 4. Realizar una Búsqueda Semántica
Crea `search_data.py` con el siguiente código:
```python
query = {"search": "computadora", "queryType": "semantic", "queryLanguage": "es-ES"}
response = requests.get(f"{endpoint}/indexes/productos/docs?api-version=2021-04-30-Preview", headers=headers, json=query)
print(response.json())
```
Ejecuta:
```bash
python search_data.py
```
Si obtienes resultados relevantes, ¡has completado con éxito este ejercicio!
