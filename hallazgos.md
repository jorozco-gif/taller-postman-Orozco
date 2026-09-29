# Tabla de observaciones del Postman

| # | Petición | Código esperado | Código obtenido | ¿Coincide? |
| :---: | :--- | :---: | :---: | :---: |
| 1 | GET /posts/1 | 200 | 200 | Sí |
| 2 | GET /posts | 200 | 200 | Sí |
| 3 | GET /posts/9999 | 404 | 404 | Sí |
| 4 | POST /posts | 201 | 201 | Sí |
| 5 | PUT /posts/1 | 200 | 200 | si |
| 6 | PATCH /posts/1 | 200 | 200 | si |
| 7 | DELETE /posts/1 | 200 | 200 | si |

# Ejecucion de las peticiones 1 y 2 de la tabla

GET/posts/1.
* El código de estado: 200 OK
* Cuántos elementos trae la respuesta: Trae 1 solo elemento en respuesta de la terminar con el metodo de json.
* Qué campos tiene cada elemento: presenta 4 campos que son userId, id, title y body

GET/posts/.
* El código de estado: 200 OK
* Cuántos elementos trae la respuesta: trae la lista completa de los elementos de la terminal de json devolviendo
un resultado de 100 publicaciones.
* Qué campos tiene cada elemento: presenta los mismos 4 campos de get post/1 userId, id, title y body