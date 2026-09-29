# Idempotencia

¿Qué significa que un metodo HTTP sea idempotente?

La idempotencia es un cualidad de un operacion informatica en la cuál se puede aplicar varias veces y la solucion siempre sera la misma.

Metodos Idempotente

GET: Es un metodo de buscar recursos ya creado, por lo que hacer la misma solicitud de busqueda de recurso no deberia cambiar en absoluto

PUT: Este modifica un recurso por completo. Si actualiza el correo electronico de una persona varias veces con la misma solicitud no va a cambiar en absoluto.

DELETE: Este elimina un recurso al servidor, si borra un recurso al servidor y después lo vuelves a borrar y el recurso seguira borrado y no cambiara nada.

Metodos No Idempotente

Post: Este agrega el recurso al servidor cada que ejecuta, si ejecutamos 2 veces la misma operación agregara 2 recursos al servidor no solamente uno y vuelve ejecutarla agregara mas recursos distintos.

Patch:  Se utiliza para realizar modificaciones parciales de un recurso. Dependiendo de la operación que realice, puede ser idempotente o no idempotente.


Por ejemplo, si usamos PATCH para cambiar el nombre de una persona a “Juan”, realizar la misma solicitud varias veces dejará el nombre en “Juan”, por lo que el resultado final será el mismo.

En cambio, si usamos PATCH para aumentar un contador en +1, la operación no será idempotente. Si el contador empieza en 1 y ejecutamos la misma solicitud una vez, pasará a 2; si la ejecutamos nuevamente, pasará a 3.

Peticiones con el PUT y POST.

PUT: Al ejecutarlo varias veces seguidas, miramos que no cambiara el resultado respecto a la primera ver que lo ejecutamos.

POST:Al ejecutarlo varias veces siempre saldra el mismo resultado, esto porque estamos en una API simulación esta no guardará lo recurso que creamos, si fuera un API real el resultado sera distinto, sería que cada vez que se ejecutara la solitud la id cambiaría esto es porque cada recurso creado serían distintos.