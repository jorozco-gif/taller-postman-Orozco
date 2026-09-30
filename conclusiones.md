# Idempotencia

## ¿Qué significa que un metodo HTTP sea idempotente?

La idempotencia es un cualidad de un operacion informatica en la cuál se puede aplicar varias veces y la solucion siempre sera la misma.

### Metodos Idempotente

GET: Es un metodo de buscar recursos ya creado, por lo que hacer la misma solicitud de busqueda de recurso no deberia cambiar en absoluto

PUT: Este modifica un recurso por completo. Si actualiza el correo electronico de una persona varias veces con la misma solicitud no va a cambiar en absoluto.

DELETE: Este elimina un recurso al servidor, si borra un recurso al servidor y después lo vuelves a borrar y el recurso seguira borrado y no cambiara nada.

### Metodos No Idempotente

Post: Este agrega el recurso al servidor cada que ejecuta, si ejecutamos 2 veces la misma operación agregara 2 recursos al servidor no solamente uno y vuelve ejecutarla agregara mas recursos distintos.

Patch: Se utiliza para realizar modificaciones parciales de un recurso. Dependiendo de la operación que realice, puede ser idempotente o no idempotente.

Por ejemplo, si usamos PATCH para cambiar el nombre de una persona a “Juan”, realizar la misma solicitud varias veces dejará el nombre en “Juan”, por lo que el resultado final será el mismo.

En cambio, si usamos PATCH para aumentar un contador en +1, la operación no será idempotente. Si el contador empieza en 1 y ejecutamos la misma solicitud una vez, pasará a 2; si la ejecutamos nuevamente, pasará a 3.

## Peticiones con el PUT y POST.

PUT: Al ejecutarlo varias veces seguidas, miramos que no cambiara el resultado respecto a la primera ver que lo ejecutamos.

POST:Al ejecutarlo varias veces siempre saldra el mismo resultado, esto porque estamos en una API simulación esta no guardará lo recurso que creamos, si fuera un API real el resultado sera distinto, sería que cada vez que se ejecutara la solitud la id cambiaría esto es porque cada recurso creado serían distintos.

## Fuentes consultadas:

¿Qué es la idempotencia?: https://cloud.google.com/discover/idempotency?hl=es-419

# Content type

X-Content-Type-Options
que significa:(nosniff)

para que sirve: sirve como cabecera de seguridad ordenando al navegador que respete estrictamente el Content-Type declarado que no intente adivinar
ya que podría interpretar un archivo mal etiquetado como script ejecutable que pueda llegar a tener ataques.

-cf-cache-estatus
que significa: (hit) indicacion de que la respuesta esta en el cache
para que sirve:nos permite saber si la respuesta viene del servidor original o de una copia almacenada mas cercana del usuario.

-Content-Length
que significa: (2018) indica el tamaño del cuerpo de la respuesta en bytes como la respuesta que también trae ese número corresponde al tamaño comprimido
(3.09 KB) en el postman que incluye el contenido descomprimido y las cabeceras.

Para qué sirve: le dice al cliente cuántos bytes debe esperar recibir. Así sabe cuándo terminó la respuesta, puede detectar si la descarga quedó incompleta y puede mostrar el progreso de una descarga.

Por qué es importante al probar una API:

Permite comprobar que la respuesta no llegó truncada o vacía cuando esperabas datos indica un problema.

Ayuda a medir el peso de las respuestas y evaluar el rendimiento de la API.

Si el valor no coincide con el tamaño real del cuerpo el cliente puede fallar o cortar la respuesta.

# Preguntas concluyentes 

## ¿Qué le faltaría a la tabla fase 2 para ser un plan de pruebas formal?

Le faltaría algunas columnas adicionales que complementaria a las columnas exitente que son estas.

- Objetivo de la prueba:Es una descripción del proposito de la consulta.

- Datos de entrada : En métodos como POST, PUT y PATCH, que envían o modifican información, es indispensable mostrar los datos que se van a enviar.

- Tests de verificación automáticos: El documento debe especificar qué validaciones lógicas o scripts se van a implementar en cada caso.

- resultado esperados del test: Muestra el resultado que debería obtenerse, por ejemplo el código de estado y los campos clave de la respuesta.

- coincide el resultado de test: Indica con "Sí" o "No" si lo obtenido corresponde con lo esperado.

## ¿por qué un 404 puede ser una buena noticia y un 200 puede ser un defecto.?
 
 Yaque la prueba se realizó, para que pase un error 404, si da 200 es un bug grave que puede deberse a varios factores. Una es  que la solicitud puede estar mal escrita la url o estas usando un metodo incorrecto o la otra,es que haya un bug en la API que esta devolviendo toda la respuestas exitosas. 