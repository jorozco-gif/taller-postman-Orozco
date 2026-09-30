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

## ¿Este caso de prueba pasó o falló? Justifica tu respuesta.

Es caso paso, porque el usuarios intensionalmenta busco un  servidor no existe y lo que obtuvo fue el resultado espera que es el estado 404 que es Not found. 

## ¿qué pasaría si esa misma petición hubiera devuelto 200 con un cuerpo vacío?

## ¿Sería un defecto?

Significa que la solicitud se proceso correctamente, pero es un falla ya que el resultado que buscamos era 404 que indica que el recurso no exite en el servidor.

# Crea un recurso con POST

## ¿qué observaste?

mis odservaciones fueron que el id simpre se mantuvo en 101 el unico cuando se le dio la opcion de darle 5 veces segidas y lo que cambio fue el tiempo de espera.

## ¿Por qué crees que ocurre eso?

Creo que ocurre porque hay 100 recurso y si le agregar uno nuevo por eso el id es 101 y siempre va a dar 101 sin importar las veces que lo envies es porque la API utilizada es una simulación y no está guardando realmente los recursos enviados. 

## ¿Cómo comprobarías, en una API real, que el recurso se creó de verdad?

 En una API real, comprobaría que la respuesta de Postman muestre:

1. El estado que tiene que ser  201 ok que es el estado created.

2. En el body tiene que aparecer el recurso que agregamos con una id coherente. 

3. Después, realizaría una petición GET utilizando ese ID para comprobar que el recurso realmente existe y que se puede consultar.

# La diferencia entre PUT y PATCH

## ¿qué diferencia encontraste entre ambas respuestas? 

Las diferencia entre ambas es que PUT cambia todos los campos. Como solo pusimos title, este se modifico, mientras que los demas campo que no se enviaron que fué el body y el id_user los dejo en blanco.

En cambio el PATCH solo se modifico el title y las demas variable las dejo como estaban.

## ¿Cuál usarías para corregir un error de escritura en un solo campo, y por qué?

Usaria el PATCH, porque si usaba PUT las demas variables se borrarian que no es lo que se esta buscando y con PATCH solo cambiaria esa variable que es lo que  queremos corregir.

# Encuentra el límite

## ¿Cómo se llama este tipo de caso de prueba?

Prueba de valores límite: nos permite verificar los valores validos como los anteriores y posteriores siendo estos

- 1 y 100: bordes válidos (mínimo y máximo).

- 0 y 101: justo fuera del rango (inválidos).

## ¿Por qué se dice que los defectos se concentran en los límites?

- Errores de "uno de más o uno de menos por ejemplo si nosotros escribimos el id < 100 cuando debía ser id <= 100 con lo que el registro 100 dejaría de devolverse.

- Malas interpretaciones de los requisitos al decidir si el límite está incluido o excluido.

# Explora otros recursos

Rutas encontradas.

GET albums

GET photos

Rutas anidada

GET posts/1/comments

Esplicación:

Yo la descubri metiendo al link del API de pruena que nos dio: https://jsonplaceholder.typicode.com.

La primera ruta, GET /albums, me muestra una lista de recursos. Cada álbum contiene 3 atributos: userId, que corresponde al identificador del usuario al que pertenece el álbum; id, que es el identificador de cada álbum y title, que corresponde al título del álbum.

La segunda ruta la GET photos me envia una lista de recursos con 5 atributo cada uno que son: albumId, que es una identificador que vincula a en que album esta la foto; id, identificador de cada foto; title, titulo de la foto ; Url, enlace directo a la imagen y thumbnailUrl, Contiene el enlace a la miniatura de la imagen.

La ruta anidada la descubri al ejecutar GET comment , observe que tenía un atributo llamado postid, que vinculada a un post con varios comments. Por esta razón, al usar la ruta anidada GET posts/1/comments me va a mostrar una lista de comments que contenga el postid:1.

Cada comentario contiene 5 atributos: postId, que identifica el post al que pertenece; id, que identifica cada comentario; name, que corresponde al nombre o título del comentario; email, que contiene el correo electrónico del usuario que lo escribió; y body, que contiene el texto del comentario.

# Escribe tu primera prueba automática

## ¿por qué es importante ver una prueba fallar antes de confiar en ella?

Es importante ver fallar una prueba primero para comprobar que realmente está validando lo que buscamos. Una prueba puede dar como correcta dependiendo de un atributo del API que no es el que nos interesa y en ese caso pasaría sin comprobar nada útil. Por eso conviene ejecutarla primero con un caso que sabemos que debe dar error de modo que, si falla, confirmaremos que lo que nos devuelve sí es lo que estamos buscando.

# Escribe tus propias pruebas.

Primer test verificando campos

Test con resultados esperados valido

pm.test("el correo del usuario que hizo el comentario id 2 es Jayne_Kuhic@sydney.com:", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.email).to.equal("Jayne_Kuhic@sydney.com");
});

Test con resultados esperados falla

pm.test("el correo del usuario que hizo el comentario id 2 es Meghan_Littel@rene.us:", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.email).to.equal("Meghan_Littel@rene.us");
});

Explicación:

Este test nos va ayudar para verificar el email usuario que hizo el comentario sea el esperado. En el primer test se verifico que el email del recurso 2 fuera Jayne_Kuhic@sydney.com y el resultado que dio fue el de passed. 

En el siguiente test se intento la misma operación pero con un email erroneo que es Meghan_Littel@rene.us y el resultado fue el espera que era failed. Esto sirve para comprobar que la prueba está diseñada correctamente.

Segundo test evaluando el tiempo de respuesta. 

Test con resultados esperados valido

pm.test("El tiempo de respuesta es menor a 500 ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});

Test con resultados esperados falla

pm.test("El tiempo de respuesta es menor a 10 ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(10);
});

Explicación:

Este test nos ayuda a verificar que el tiempo que tarda la API en responder esté dentro de un límite aceptable. En el primer test se verificó que el tiempo de respuesta fuera menor a 500 milisegundos (ms) y el resultado obtenido fue passed. 

En el siguiente test se intentó la misma validación exigiendo un tiempo de respuesta irrealmente corto (menor a 10 ms) y el resultado fue el esperado: failed. Esto sirve para evaluar el rendimiento de la petición y asegurarnos de que la condición de la prueba funciona correctamente.

Tercera test verificando el tipo de campo.

Test con resultados esperados valido

pm.test("el campo name es de tipo string", function () {
    pm.expect(pm.response.json().name).to.be.a('string')
});

Test con resultados esperados falla

pm.test("el campo name es de tipo number", function () {
    pm.expect(pm.response.json().name).to.be.a('number')
});

Explicación:

Este test nos permite comprobar que el formato o tipo de dato de un campo específico sea el correcto. En el primer test se verificó que el campo name fuera una cadena de texto (string), y el resultado fue passed. 

En el siguiente test se intentó la misma evaluación pero esperando que el campo fuera de tipo numérico (number); como el dato real es texto, el resultado fue el esperado: failed. Esto es muy útil para garantizar la consistencia en la estructura de los datos devueltos por la API y confirmar que la validación esté bien hecha.

## Fuentes consultadas:

Documentación de POSTMAN: https://www.postman.com/postman/postman-team-collections/http-request/gdbgfhu/json-schema-v4-validation