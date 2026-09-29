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

# Provoca un error a propósito
¿Este caso de prueba pasó o falló? Justifica tu respuesta.

Es caso paso, porque el usuarios intensionalmenta busco un  servidor no existe y lo que obtuvo fue el resultado espera que es el estado 404 que es Not found. 

¿qué pasaría si esa misma petición hubiera devuelto 200 con un cuerpo vacío?
¿Sería un defecto?

Significa que la solicitud se proceso correctamente , pero es un falla ya que el resultado que buscamos era 404 que indica que el recurso no exite en el servidor.

# Crea un recurso con POST

¿qué observaste? ¿Por qué crees que ocurre eso? ¿Cómo comprobarías, en una
API real, que el recurso se creó de verdad?

mis odservaciones fueron que el id simpre se mantuvo en 101 el unico cuando se le dio la opcion de darle 5 veces segidas y lo que cambio fue el tiempo de espera.

Creo que ocurre porque hay 100 recurso y si le agregar uno nuevo por eso el id es 101 y siempre va a dar 101 sin importar las veces que lo envies es porque la API utilizada es una simulación y no está guardando realmente los recursos enviados. 

 En una API real, comprobaría que la respuesta de Postman muestre:

1. El estado que tiene que ser  201 ok que es el estado created.

2. En el body tiene que aparecer el recurso que agregamos con una id coherente. 

3. Después, realizaría una petición GET utilizando ese ID para comprobar que el recurso realmente existe y que se puede consultar.

# La diferencia entre PUT y PATCH

¿qué diferencia encontraste entre ambas respuestas? 

Las diferencia entre ambas es que PUT cambia todos los campos. Como solo pusimos title, este se modifico, mientras que los demas campo que no se enviaron que fué el body y el id_user los dejo en blanco.

En cambio el PATCH solo se modifico el title y las demas variable las dejo como estaban.

¿Cuál usarías para corregir un error de escritura en un solo campo, y por qué?

Usaria el PATCH, porque si usaba PUT las demas variables se borrarian que no es lo que se esta buscando y con PATCH solo cambiaria esa variable que es lo que  queremos corregir.

# Encuentra el límite

¿Cómo se llama este tipo de caso de prueba?
Prueba de valores límite: nos permite verificar los valores validos como los anteriores y posteriores siendo estos

- 1 y 100: bordes válidos (mínimo y máximo).

- 0 y 101: justo fuera del rango (inválidos).



¿Por qué se dice que los defectos se concentran en los límites?

- Errores de "uno de más o uno de menos por ejemplo si nosotros escribimos el id < 100 cuando debía ser id <= 100 con lo que el registro 100 dejaría de devolverse.

- Malas interpretaciones de los requisitos al decidir si el límite está incluido o excluido.

# Explora otros recursos

Rutas encontradas

GET albums

GETphotos

Rutas anidada

GET posts/1/comments

Esplicación

Yo la descubri metiendo al link del API de pruena que nos https://jsonplaceholder.typicode.com.

La primer ruta