# Ejercicio 4 - Consultas a CosmosDB

## Objetivo
Aprender a crear una base de datos en **CosmosDB**, insertar datos de ejemplo y realizar consultas desde Python.

## Pasos

### 1. Crear una Cuenta de CosmosDB
Ejecuta el siguiente comando para crear una cuenta en Azure:
```bash
az cosmosdb create --name mi-cosmosdb --resource-group mi-grupo
```

### 2. Crear una Base de Datos y Contenedor
```bash
az cosmosdb sql database create --account-name mi-cosmosdb --name MiBaseDatos --resource-group mi-grupo
az cosmosdb sql container create --account-name mi-cosmosdb --database-name MiBaseDatos --name MiContenedor --partition-key-path "/id" --resource-group mi-grupo
```

### 3. Insertar Datos de Ejemplo
Crea un archivo `insert_data.py` y copia el siguiente código:
```python
from azure.cosmos import CosmosClient

url = "<URL_DE_COSMOSDB>"
key = "<CLAVE_DE_COSMOSDB>"
client = CosmosClient(url, credential=key)
database = client.get_database_client("MiBaseDatos")
container = database.get_container_client("MiContenedor")

data = {"id": "1", "nombre": "Ejemplo", "valor": 100}
container.create_item(body=data)
print("Datos insertados correctamente")
```
Ejecuta:
```bash
python insert_data.py
```

### 4. Realizar una Consulta
Crea `query_data.py` y copia este código:
```python
query = "SELECT * FROM c WHERE c.nombre = 'Ejemplo'"
items = list(container.query_items(query=query, enable_cross_partition_query=True))
for item in items:
    print(item)
```
Ejecuta:
```bash
python query_data.py
```
Si ves los datos insertados, ¡has completado con éxito este ejercicio!