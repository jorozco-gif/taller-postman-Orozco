# Taller de APIs y Postman

*Estudiante:* Juan Sebastián Orozco Rios

*Código:* 1113865729

*Asignatura:* Ingeniería de Software II — Cotecnova

## Marco conceptual

### ¿Que es API Rest?

API Rest son un conjunto de reglas ligadas directamente  al protocolo https que permit la comunicación de dos maquinas por el modelo cliente servidor.

#### ¿Que es una API?

Son unos protocolo que varian según el proveedor a usuario que le exige unos datos claves para poder devolverle la respuesta que necesite el usuario.

Ejemplo: El cliente hace una solicitud de pedido de compras ya sea por una web o app. Esta le pedire algunos datos para que la compra sea exitosa como son nombre, cuenta bancaria y dirección para después mandarle el servidor un mensaje de compra exitosa.

#### ¿Como un API puede ser REST?

Para que un API sea un REST debe cumplir distintas reglas:

1. Debe tener un modelo cliente-servidor.El cliente hace la solicitudes al servidor devuelve una respuesta, esto atrave de comandos HTTP. 

2. Debe ser independiente cada solicitud que el cliente haga. Esto significa que el servidor debe recibir en cada solicitud la información necesaria para procesarla, sin depender de lo ocurrido anteriormente.

por ejemplo: El cliente realiza una solicitud para consultar un viaje con determinadas fechas. Después, realiza otra solicitud para consultar un viaje con fechas completamente diferentes. La segunda solicitud es independiente de la primera y debe contener toda la información necesaria para que el servidor pueda procesarla.

3. Debe poder almacenar las respuestas del usuario y datos importantes en la memoria cache, para potenciar la interacción con el usuario.

4. La comunicación entre el cliente y el servidor debe seguir reglas estandarizadas y consistentes. Los recursos deben poder identificarse mediante URL y el cliente debe poder interactuar con ellos mediante métodos HTTP como GET, POST, PUT y DELETE.

Además, la información debe enviarse mediante una representación estándar. Un formato muy utilizado es JSON, pero REST no obliga a utilizar únicamente JSON.

#### ¿Qué es un recuerso?

 Son objeto del dominio los cuales podemos hacerle diferente acción como: buscar, eliminar y modificar.

 Ejmplo: usuario, pedidos, productos, facturas y sesiones.

 Los recursos también deben protegerse para evitar que un usuario pueda acceder o realizar acciones que no tiene permitidas. Para esto se pueden definir aspectos como:
 
 1. Definir quien puede ver cada recurso y quienes no lo pueden ver.

2. Definir quien puede crear o modificar los recursos.

3. Definir como se identifica de forma segura.

4. Deifnir qué relaciones tiene con otros recursos.

### ¿qué es un endpoint?

Es un punto de acceso que permite la comunicación entre el cliente y el servidor se conforman con una url del servidor y el metodo HTTP y dependiendo del metodo utilizado el resultado sera diferente.

### Un ejemplo de una aplicación que uses a diario y que dependa de APIs

Nequi es una aplicación que depende de las APIs, ya que el usuario para ver el dinero que tiene en su cuenta, Nequi envia un GET al servidor para obtener su saldo. Igualmente es indespensable un API cuando un usuario le manda dinero a otro. En esta acción primero la app le manda una solicitud al servidor con el metodo Post despues, el servidor devuelve al otro usuario la suma de lo que tenia con lo que se le haya enviado y una notificacion con el monto, mientras que al usuario que envió le resta ese dinero de su saldo. Por estas razones, Nequi es muy dependiente de las APIs.

#### Fuentes consultadas:

Arquitectura de APIs REST, recursos, endpoints y superficie de ataque: https://tutorialesprogramacionya.com/ciberseguridad/seguridadenapisrest/tema2.html#google_vignette

¿Qué es una API REST?: https://cloud.google.com/discover/what-is-rest-api?hl=es

¿Qué es un endpoint de API?: https://www.ibm.com/es-es/think/topics/api-endpoint

# Métodos HTTP

| Método | Operación CRUD | Qué hace |
| :--- | :--- | :--- |
| *GET* | Consultar | Obtener información de una lista |
| *POST* | Crear | Registrar datos |
| *PUT* | Modificar | Modificar los datos |
| *PATCH* | Actualizar | Cambiar datos |
| *DELETE* | Eliminar | Eliminar datos |

# Codigos de estado

-1xx: el servidor recibio la peticion enviado por el navegador y continua procesandola y por cierto el cliente no  podrá encontrar este estado ya que es un estado de transición y el cliente solo puede ver el estado final.

ej:100 Continue,101 Switching Protocols

-2xx:indica que la solicitud que se pidio fue enviada correctamente.

ej: 200 OK, 201 Created, 204 No Content

-3xx:Indica que el recurso solicitado ha sido movido o que el cliente debe realizar alguna acción adicional para obtenerlo desde otra ubicación.

ej:301 Moved Permanently, 302 Found, 304 Not Modified
 
-4xx El servidor no pudo completar la petición debido a un problema relacionado con la solicitud realizada por el cliente, por ejemplo, porque la solicitud es incorrecta, no está autorizada o el recurso no existe.

ej:400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found
 
-5xx:la petición era válida, pero el servidor falló al procesarla ya sea porque se agoto el tiempo de espera o problemas temporales de la red.

ej:500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable

## ¿por qué se separan los errores 4xx de los 5xx? 

Se separan porque son errores muy diferentes el 4xx implica una equivocación en la solicitud enviada, así que el cliente debe corregirla. En cambio el 5xx implica que el problema esta en el servidore, por lo que el usuario no tiene nada que ver y quien debe arreglarlo es el administrador del servidor. 

## ¿Qué cambia entre unos y otros desde el punto de vista de quién tiene la culpa?        

En el 4xx la responsabilidad es del cliente, porque envió una solicitud incorrecta o sin autorización. En el 5xx la responsabilidad es del servidor, porque la solicitud era correcta pero no pudo cumplirla.

### Fuentes consultadas:

¿Qué son los códigos HTTP? + lista completa de explicaciones de los códigos de estado: https://www.hostinger.com/es/tutoriales/codigos-http/