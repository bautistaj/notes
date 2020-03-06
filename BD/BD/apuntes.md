# Base de datos
Es un conjunto de datos con un mismo contexto que pueden ser convertidos en información.

#### Base de datos relacionales y no relacionales
Existen dos tipos de bases de datos, bases de datos relacionarles y no relacionarles.


Ejemplos de Gestores para bases de datos Relacionales:
- SqlServer
- MySQL
- Postgrestsql
- MariaDB
- Oracle

Ejemplos de Gestores para bases de datos No Relacionales:
- Casandra
- Neo4j
- MongoDB
- Elasticsearch

#### Servicios de base de datos
Servicios de bases de datos se clasifican en dos tipos Auto Administradas y Administradas.
- Auto Administradas: Base de datos instalada en el servidor en donde tu te encargas de todo el mantenimiento de la misma.

- Administradas: Servicio contratado como por ejemplo Aws, Azure entre otros.

#### Historia de las RBD

Edgar Codd inventor de las RBD.

Surgen de a necesidad de almacenar datos y en un principio se hacia en texto plano, fáciles de guardar pero difíciles de consultarlas.

##### Entidades y atributos.

Una entidad es similar a un objeto (POO) y representa algo del mundo real y cuenta con atributos y por convención las entidades se nombran en plural.

* Atributos compuestos son aquellos que tienen atributos ellos mismos.
Atributos llaves son atributos que identifican a la entidad.

* Entidades débiles: no pueden existir sin una entidad fuerte

* Entidades débiles por identidad: No se distinguen entre si más que por la clave de su identidad.

* Entidades débiles por existencia:  Se les asigna una clave propia.


##### Relaciones
Las relaciones nos permiten unir nuestras entidades.

##### Cardinalidad
La carnalidad es una propiedad de las relaciones y tiene que ver con los números de pertenencias.

* Cardinalidad: 1 a 1
* Cardinalidad: 0 a 1
* Cardinalidad: 1 a N
* Cardinalidad: 0 a N

#### Diagrama Físico, tipos de datos y constrains

##### Tipos de datos
* Texto: Char(n), VARCHAR(n), TEXT
* Número: INTEGER, BIGINT, SMALLINT, DECIMAL(n,s), NUMERIC(n,s)
* Fecha/hora_ DATE,TIME, DATATIME, TIMESTAMP
* Lógicos: BOOLEAN

##### Constraints (Restricciones)
* NOT NULL: Asegura que la columna no tenga valores nulos
* UNIQUE: Se asegura que cada valor en la columna no se repita
* PRIMARY KEY: Es una combinación de NOT NULL y UNIQUE
* FOREING KEY: Identifica de manera única una tupla en otra tabla.
* CHECK: Se asegura que el valor en la columna cumpla una condición dada
* DEFAULT: Colocan un valor por defecto
* INDEX: Se crea por columna para permitir búsqueda más rápidas


#### Normalización
Nos permite minimizar la redundancia en una base de datos.
* Primera forma normal (1FN): Atributos atómicos,  los datos no deben de estar repetidos
* Segunda forma normal (2FN): Debe cumplir la 1FN y cada campo de la tabla debe de depender de una clave única.
* Tercera forma normal (2FN): Cumplir con las dos formas normales anteriores y no debe de existir dependencias con campos no clave.
* Cuarta forma normal (4FN):  Cumplir con las tres formas normales anteriores y los campos multivaluados se identifican por una clave única.
