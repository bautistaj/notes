# GraphQL

#### ¿Qué es GraphQL?
Paradigma implementado para la comunicación entre aplicaciones, antes existían protocolos como CORBA, SOAP, RPC y el más reciente Rest.

GraphQl puede ser visto como una evolución del protocolo REST.

Ventajas:
* Lenguaje agnostico que permite definir de forma clara y concisa los objectos y acciones del API.
* Validación automatica de los datos a ingresar.
* Control de errores.

La última versión de Junio 18

#### Schema y tipos de datos.

Es Schema es la base de una API en GrapQL, es la encargada de definir los datos que se van a utilizar.

En el Schema se definen campos, argumentos, tipos.

Tipos de datos:
* String
* Int
* Float
* Boolean
* ID

#### Queries y Resolvers

Un Query nos permite ejecutar una petición al API, GraphQL devuelve el valor dentro de un Object data.

Para ejecutar la petición se debe de utilizar un resolver este va a contener las mismas propiedades declaradas dentro del Query.

Un resolver es una función que resuelve el valor de un tipo o campo.

#### Sirviendo el API en la web

~~~js
app.use('/api', gqlMiddleware({
  schema: schema, // definir el schema
  rootValue: resolvers, // definir el resolver a utilizar
  graphiql: true // entorno de desarrollo que va utilizar
}))
~~~

#### Custom Types
Tipo de dato customizado.

~~~json
type Course {
  _id: ID
  title: String
  teacher: String
  description: String
  topic: String
}

type Query {
  getCourses: [Course]
}
~~~

#### Argumentos
ID! Argumento debe ser obligatorio

#### Mutations e Inputs
Mutations practicamnete es un mecanismo para insertar datos.
Los mutations por lo general siempre reciben un parametro de tipo Input
~~~js
nombreMutation(input: InputType): tipo
~~~

#### Nested Types
Relación entre tipos de del schema
~~~graphql
type Course {
  _id: ID!
  title: String!
  teacher: String!
  description: String
  topic: String @deprecated
  "Nested types, relación entre tipos de datos, en este caso un curso tiene varios estudiantes"
  people: [Student]
  level: Level
}
~~~

#### Fragments

Los Fragments nos permiten agrupar campos para que puedan ser reutilizacos en diferentes peticiones.

~~~graphql
{
  allCourses: getCourses{
    ...CourseFields
    teacher
  }
  
  oneCourse: getCourse(id: "5e652905b7a4b80533d535b9"){
    ...CourseFields
  }
}

fragment CourseFields on Course {
    _id
    title
    people{
      name
    }
}
~~~

#### Variables 
Las variables son utilizacadas para utilizarlas en los queries.

Declaración de variables.
~~~
$nombre: tipo
~~~

~~~graphql
query GetCourse2 ($course: ID!) {
  getCourse(id: $course){
   _id
    title
    people{
      _id
      name
    }
  }
}
~~~

Requiere un objeto JSON como:

~~~json
json
{
  "course": "5cb4b8ce75f954a0585f7be3"
}
~~~

#### Errors
GraphQL nos va a retornar un objeto llamado errors con detaller del mismo.


#### Nota
Instalar CORS para poder acceder desde cualquier lugar.
* Schemas types
* Custom types
* Argumentos
* Nested types
* Resolver tipos
* Errores
* Alias y fragments
* Variables 
* Enums
* Interfaces
* Directivas
* Unions



