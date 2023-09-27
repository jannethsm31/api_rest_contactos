# Design Document: API REST CONTACTOS

## 1. Descrpción
Ejemplo API REST para gestionar contactos en un DB utilizando FastAPI

## 2. Objetivo
Realizar un ejemplo de diseño de una API REST de tipo CRUD y su posterior codificación utilizando el framework FastAPI [FastAPI].(https://fastapi.tiangolo.com/).

## 3. Diseño de la BD 
Para este ejemplo se utilizará el gestor de bases de datos .[SQLite3](https://www.sqlite.org). con las siguientes tablas:

### 3.1 Tabla: contactos

|No.|Campos|Tipo|Restrincciones|Descripción|Tamaño|
|--|--|--|--|--|--|
|1|id_contactos|int|PRIMARY KEY|Llave primaria de la tabla|AUTOINCREMENT|
|2|nombre|varchar|Not Null|Campo que almacena el nombre del contacto|100|
|3|Apellido Paterno|varchar|Not Null|Campo que almacena el apellido paterno del contacto|50|
|4|Apellido Materno|varchar|Not Null|Campo que almacena el apellido paterno del contacto|50|
|5|Email|varchar|Not Null|Campo que almacena el correo electronico del contacto|50|
|6|Teléfono|varchar|Not Null|Campo que almacena el teléfono del contacto|50|

## 4. Script de SQLite

```sql
SELECT 'script APIRest' AS Actividad;

CREATE TABLE IF NOT EXISTS personas(
id_contactos INTEGER PRIMARY KEY AUTOINCREMENT,
nombre TEXT NOT NULL,
primer_apellido TEXT NOT NULL,
segundo_apellido TEXT NOT NULL,
  email TEXT NOT NULL,
email TEXT NOT NULL)

## 5. Diseño de los métodos

### 5.1 GET

|No|Propiedad|Detalle|
|--|--|--|
|1|Description|Endpoint raíz de la API|
|2|Summary|Endpoint raiz|
|3|Method|GET|
|4|Endpoint|http://localhost:8000/|
|5|QueryParam|NA|
|6|PathParam|NA|
|7|DATA|NA|
|8|Versiones|v1|
|9|Status code|200 (OK)|
|10|Response-Type|application/json|
|11|Response|{"version":"v1","message":"endpoint raiz","datatime":"21/9/23 10:16"}|
|12|Curl|curl -X 'GET' 'http://localhost:8000/' -H 'accept: application/json'|
|13|Status code(error)|NA|
|14|Response Type(error)|NA|
|15|Response(error)|NA|

### 5.2 GET - http://localhost:8000/contactos

|No|Propiedad|Detalle|
|--|--|--|
|1|Description|Endpoint para obtener lista de contactos|
|2|Summary|Endpoint para listar|
|3|Method|GET|
|4|Endpoint|http://localhost:8000/contactos|
|5|QueryParam|limit:int, offset:int, nombre:string|
|6|PathParam|NA|
|7|DATA|NA|
|8|Versiones|V1|
|9|Status code|200 (OK)|
|10|Response-Type|application/json|
|11|Response|{"version":"v1","message":"Lista de contactos","datatime":"25/9/23 9:36"}|
|12|Curl|curl -X 'GET' 'http://localhost:8000/?limit=10&offset=0&nombre=Juan' -H 'accept: application/json'|
|13|Status code(error)|400(Bad Request)|
|14|Response Type(error)|application/json|
|15|Response(error)|{"version":"v1","message-error":"<ocurrió un error","datatime":"25/9/27 9:36"}|

### 5.3 POST

|No|Propiedad|Detalle|
|--|--|--|
|1|Description|Endpoint para enviar datos a la API|
|2|Summary|Endpoint para enviar datos|
|3|Method|POST|
|4|Endpoint|http://localhost:8000/contactos|
|5|QueryParam|NA|
|6|PathParam|NA|
|7|DATA|{"id_contacto":int, "nombre":string, "apellido_paterno":string, "apellido_materno":string, "email":string, "telefono":string}|
|8|Versiones|v1|
|9|Status code|201(Created)|
|10|Response-Type|application/json|
|11|Response|{"version":"v1","message":"Lista de contactos","datatime":"25/9/23 9:46"}|
|12|Curl|curl -X 'POST' 'http://localhost:8000/contactos' -H 'accept: application/json' -d '{"id_contacto":int, "nombre":string, "apellido_paterno":string, "apellido_materno":string, "email":string, "telefono":string}'|
|13|Status code(error)|400 (Bad Request)|
|14|Response Type(error)|application/json|
|15|Response(error)|{"version":"v1","message-error":"ocurrió un error","datatime":"25/9/27 9:46"}|

### 5.4 DELETE - http://localhost:8000/contactos/?id_contacto=

|No|Propiedad|Detalle|
|--|--|--|
|1|Description|Endpoint para eliminar un recurso de la API|
|2|Summary|Endpoint para eliminar un recurso|
|3|Method|DELETE|
|4|Endpoint|http://localhost:8000/contactos/?id_contacto=|
|5|QueryParam|id_contacto|
|6|PathParam|NA|
|7|DATA|NA|
|8|Versiones|V1|
|9|Status code|204 (No Content)|
|10|Response-Type|application/json|
|11|Response|{"version":"v1","message":"Se eliminó con éxito","datatime":"25/9/23 9:56"}|
|12|Curl|curl -X 'DELETE' 'http://localhost:8000/?id_contacto=1' -H 'accept: application/json'|
|13|Status code(error)|400 (Bad Request)|
|14|Response Type(error)|application/json|
|15|Response(error)|{"version":"v1","message-error":"ocurrió un error al eliminar","datatime":"25/9/27 9:56"}|

### 5.5 PUT - http://localhost:8000/contactos/?id_contactos=

|No|Propiedad|Detalle|
|--|--|--|
|1|Description|Endpoint para actualizar recursos de la API|
|2|Summary|Endpoint para actulizar datos|
|3|Method|PUT|
|4|Endpoint|http://localhost:8000/contactos/?id_contacto=|
|5|QueryParam|id_contacto|
|6|PathParam|NA|
|7|DATA|NA|
|8|Versiones|v1|
|9|Status code|200 (OK)|
|10|Response-Type|application/json|
|11|Response|{"version":"v1","message":"Actualizado con éxito","datatime":"25/9/23 10:06"}|
|12|Curl|curl -X 'DELETE' 'http://localhost:8000/?id_contacto=1' -H 'accept: application/json'|
|13|Status code(error)|400 (Bad Request)|
|14|Response Type(error)|application/json|
|15|Response(error)|{"version":"v1","message-error":"ocurrió un error al actualizar","datatime":"21/9/27 10:06"}|
