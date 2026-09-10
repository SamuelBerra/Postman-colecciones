# Pruebas API — DummyJSON con Postman

Colección de Postman para demostrar pruebas funcionales y de contrato sobre una API REST pública de práctica. Incluye variables de entorno, autenticación, pruebas automáticas y un escenario negativo.

## API utilizada

- Base URL: `https://dummyjson.com`
- Documentación: [DummyJSON Docs](https://dummyjson.com/docs)
- Propósito: API de datos simulados para pruebas y prototipado.

> DummyJSON usa datos de demostración. Las credenciales incluidas en el entorno son públicas y pertenecen a esa API. Nunca subas contraseñas, tokens o claves reales a GitHub.

## Contenido

| Archivo | Descripción |
| --- | --- |
| `QA_DummyJSON.postman_collection.json` | Colección con ocho solicitudes y pruebas automáticas. |
| `QA_DummyJSON.postman_environment.json` | Variables de entorno para ejecutar las solicitudes. |

## Cobertura

| # | Solicitud | Validaciones principales |
| --- | --- | --- |
| 01 | Salud de la API | HTTP 200, estado `ok` y método `GET`. |
| 02 | Productos paginados | HTTP 200, estructura de paginación y límite solicitado. |
| 03 | Producto por ID | HTTP 200, ID, título, precio y categoría. |
| 04 | Búsqueda de productos | HTTP 200, arreglo de resultados y campos obligatorios. |
| 05 | Login | HTTP 200, usuario y tokens; guarda tokens en el entorno. |
| 06 | Usuario autenticado | HTTP 200 e identidad de la sesión. |
| 07 | Producto inexistente | HTTP 404 y mensaje de error. |
| 08 | Crear producto simulado | HTTP 201 y datos de respuesta. |

## Cómo ejecutar en Postman

1. Descarga o clona este repositorio.
2. Abre Postman y selecciona **Import**.
3. Importa los dos archivos `.json` de esta carpeta.
4. En la esquina superior derecha, elige el entorno **QA - DummyJSON (Demo)**.
5. Abre la colección **QA - DummyJSON API**.
6. Selecciona **Run collection** y ejecuta las ocho solicitudes en el orden presentado.
7. Revisa que las pruebas queden aprobadas. El login debe ejecutarse antes de **Consultar usuario autenticado**, ya que almacena el token temporal.

## Ejecución con Newman (opcional)

Si tienes Newman instalado, ejecuta desde una terminal dentro de esta carpeta:

```bash
newman run QA_DummyJSON.postman_collection.json -e QA_DummyJSON.postman_environment.json
```

## Nota sobre el POST

El endpoint `POST /products/add` de DummyJSON simula la creación y no guarda el producto de forma permanente. Se incluye para demostrar la validación de un método POST sin modificar datos reales.
