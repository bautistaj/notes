# Api Rest

#### ¿Qué es un API y para que sirve?

API: Application Programming Interface, conjunto de reglas que definen como se van a comunicar dos aplicaciones, por ejemplo qué tipos de request y response se van a utilizar.

En **POO** una API son todos los elemento públicos que están disponibles.

## Conocer conceptos principales de Rest

#### ¿Qué es y cómo funciona el protocolo HTTP?

HTTP: Hytpertext Transfer Protocol, conjunto de reglas en las que se van a comunicar dos entidades.

Protocolo: conjunto de reglas.

#### ¿Qué significa Rest?

REST: Representational State Transfer o bien transferencia de estado representacional.

API RESTful es una API diseñada con los conceptos de REST.
* Recurso: todo dentro de una Api RESTFul debe ser un recurso.
* URI: Todos los recursos se manipulan a partir de una URL (Identificadores Universales de Recursos).
* Acction: todas las peticiones de un Api Rest debe de estar asociado con un verbo HTTP:
  * Get: para obtener recursos.
  * Post: para escribir un recurso.
  * Put: Para editar un recurso.
  * Delete: para eliminar un recurso.

#### Métodos de autenticación 
#### HTTP
* Mediante HTTP auth user, debe de ir en el encabezado authorization.

#### HMAC
* HMAC: (Hash Message Authorizarion Code) para lo cual se necesita 3 elementos, Basado en Hash de Mensajes:
  * Función hash: Difícil de romper y que sea conocida por el cliente y el servidor.
  * Clave Secreta: para corroborar el HASH
  * UID: Id de usuario será utilizado dentro del HASH junto con la clave secreta y el timestamp

Es mucho más seguro que la autenticación vía HTTP.

#### Acceso mediante Tokens
Roles del servidores:
* Uno se encarga de la autenticación.
* Otro se encarga de desplegar los recursos del API.

Flujo.
* Petición para la solicitud de Token
* El servidor devuelve token
* El usuario hace una petición para pedir recurso.
* El servidor con los recursos hace una petición al servidor de autenticación para verificar token sea valido.
* Una vez verificado el token, el servidor devuelve los recursos al cliente.


## Manejo de Errores en servicio REST

Para las respuestas con error se utilizaran los siguientes códigos:
en los encabezados HTTP.
* 400: Bad Request, que el servidor no puede procesar la petición.
* 404: Not Found, el servidor no encuentra el recurso buscado.
* 500 Invernal Error Server, la petición no se pudo procesar por un error en el servidor.

## Buenas prácticas
* Utilizar sustantivos para nombrar los recursos.
* Añadir los nombres en plural para las URLs
* Las modificaciones se deben de hacer con su verbo HTTP correspondiente.
* Para devolver recursos asociados se debe incorporar sub-recursos
~~~
autos/1/choferes
~~~
* Navegabilida vía vínculos
* Cuando devuelva colecciones deben de ser filtrables, ordenables y paginables.
* Versionar las api
~~~
v1/autos/1/choferes
~~~








