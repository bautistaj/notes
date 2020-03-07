# MongoDB

## Introducción
#### Base de datos NoSQL
Las base de datos **Not Only SQL** se clasifican en 4 familias
* Key Values stores: Guardan datos de forma llave Valor.
  * Casos de uso: guardar datos en cache. 
  * Ejemplo: Redis.
  * Características: muy sencillas y rápidas. 

* Graph Databases: Basadas en Grafos.
  * Casos de uso: Realizar consultas eficientes en una base de datos relaciónal.
  * Ejemplo: Neo4J, JanusGraph.

* Wide-column Store: Bases de datos columnares en donde la columna cuenta con un id así como la fila. 
  * Casos de uso: Se usa en big data, el diseño de estas se vuelve complejo
  * Ejemplo: Cassandra o HBase.

* Documente database: Base de datos basada en documentos. 
  * Casos de uso: Nos permite modelar casos de la vida real de forma muy sencilla.
  * Ejemplo: MongoDM, CouchBase.

#### Definición de MongoDB y su ecosistema

Base de datos NoSQL que permite guardar grandes cantidades de datos en documentos de forma distribuida.
Características
* Guardar documentos de tipo BSON (Binary JSON)
* Base de datos distribuida: Cluster de MongoDB el cual permite escalar de forma horizontal.
* Es SchemaLess: Las colecciones podrían no tener la misma estructura, esto lo hace muy flexible.
* Código abierto.
* MongoDB mobile.
* Stich: Crear servicios ServerLess.


#### Mongo Shell
Comandos
* show dbs: Mostrar las base de datos.

#### MongoDB + Drivers
Los drivers son las librerías para comunicar la app con la base de datos:
* C
* C++
* Go
* Java
* Node.js
* Perl

Para agregar los drives se debe de utilizar un gestor de dependencias:
* Maven/Gradle para Java
* npm para Java script

Proceso de conexión a la base de datos.
* Crear conexión **MongoClient**
* Obtener la base de datos **MongoDataBase**
* Acceder a una colección **MongoCollection**
* **CRUD**

## Operaciones CRUD
#### Bases de datos, Colecciones y Documentos en MongoDB
Las bases de datos son un contenedor físico para las colecciones.

* Colecciones: Son  agrupaciones de documentos las cuales no están atadas a una estructura
 Rigida,
* Documentos: Son registros dentro de las colecciones, unidad básica de MongoDB, estos son similares a JSON pero en realidad son BSON.

<table>
    <tr>
        <td>SQL</td>
        <td>NoSQL</td>
    </tr>
    <tr>
      <td>Tablas</td>
      <td>Colecciones</td>
    </tr>
    <tr>
      <td>Tupla</td>
      <td>Documentos</td>
    </tr>
</table>


## Operaciones CRUD dentro de la consola
~~~js
db.dbName.insertOne({})
db.dbName.findOne()
db.dbName.inserMany([{},{},{},{}])
db.dbName.find({},{}).pretty()
db.dbName.updateOne(Object({_id:””}),{$set: {} } )
db.dbName.updateMany(Object({_id:””}),{$set: {} } )
db.dbName.deleteOne(Object({_id:””}),{$set: {} } )
db.dbName.deleteMany(Object({_id:””}),{$set: {} } )
~~~
## Esquemas y relaciones
#### Tipos de datos
Tipos de datos que se utilizan en MongoDB
* Strings
* Boolean
* ObjectId: Utiliza el tiempo para poder generar ids únicos.
* Date
* Númericos: Double, Integer, Integer64 lists y Decimals.
* Array:  Arreglos o listas de cualquier otro tipo de dato.
* Documentos embebidos: un documento puede tener otro documento.


#### ¿Qué son los esquemas y las relaciones?
Es la forma en la cual se enlazan unos con otros.

#### Proyecciones
Solo obtener los datos que necesitamos.
~~~js
db.dataBase.findOne({ status: “A”}, { item: 1, status: 1} ) // Para el query solo nos trae item y estatus incluido el _id.
~~~

**Operaciones de comparación**
* $eq: =
* $gt: >
* $gte: >=
* $lt: <
* $lte: <=
* $ne: !=
* $in: Valores dentro de un arreglo
* $nin: Valores no incluidos dentro de un arreglo.

**Operaciones Lógico**
* $and
* $not
* $nor 
* $or

**Operadores pora arreglos**
* $all: Arreglos que contengan todos los elementos del query.
* $elementMatch: Elemento que cumple con la condición.
* $size: Documento que tiene un dato tipo array con un tamaño en específico.

#### Operaciones Avanzadas con Agregaciones

* Pipeliene de Agregaciones: grupo de múltiples etapas que ejecutan agregaciones en diferentes momentos, estas corren en todo el cluster.

* Map-Reduce:  Nos permite definir funciones de JavaScript para ejecutar funciones avanzadas. Por ejemplo utilizar map o reduce.

* Agregaciones de proposito único: Funciones definidas las cuales nos ayudan a calcular algo en particular, debemos de tener cuidado ya que podrían mejorar o afectar el rendimiento de la base de datos. Por ejemplo: count(), estimateDocumentCount y distinct.

#### Indices
Ayudan a que las consultas sean más eficientes.

Tipos de indices:
* De un solo campo:  
* Compuestos: Se definen con varios campos
* Multi-llave: Se definen con varios campos
* Geoespaciales: Ayudan hacer queries por latitud y longitud
* Indeices de texto
* Hashes: Convertir valores en hash-

~~~js
db.survery.getIndexes() // obtenemos los indices de una colección.
db.survery.createIndex({ _id: "text"}) // creamos un index de tipo text
db.survery.find({ $text: { $search: "1" } }) // Realizar query con indice
~~~