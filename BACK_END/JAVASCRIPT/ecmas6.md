# ECMAScript

ECMAScript es la especificación del lenguaje por ECMA Internacional institución encargada de los estándares.

## ¿Qué se implemento en ES6?
Nace en Junio del 2015
* Default params y concatenación
* LET y CONST, Multilinea, Spread Operator y Desestructuración
* Arrow Functions, Promesas y Parámetros en objetos
* Clases, Módulos y Generadores
[Referencias](https://carlosazaustre.es/ecmascript6)

#### Default params y concatenación
~~~js
//es6 default values
function newFunction2(name = 'Jose Luis', age = 30, country = 'México') {
  console.log(name, age, country);
}
~~~

~~~js
//Template literals
let hello = 'Hello';
let world = 'World';

console.log(`${hello} ${world}`);
~~~

#### LET y CONST, Multilinea, Spread Operator y Desestructuración

~~~js
//es6
let lorem = `Concatenar lieneas
con salto de liena`;

console.log(lorem);
~~~

~~~js
//Desestructuración de elementos
let person = {
  name: 'Jose luis',
  age: 30
};

let { name, age } = person;

console.log(name, age);
~~~

~~~js
//Spread operator
let teamOne = ['Jose','Luis'];
let teamTwo = ['Laura', 'Sandi'];

let funcionTeam = [...teamOne, ...teamTwo];

console.log(`Result: ${funcionTeam}`);
Result: [ 'Jose', 'Luis', 'Laura', 'Sandi' ]
~~~

~~~js
//var, let, const
{
  var varVariable = 'global';
}

{
  let letVariable = 'global';
  const contant = 'Const Varible ';
  //Presenta erro debido que se declara 
  //como constate por lo cúal no se le puede 
  //reasignar nuevo valor
  contant = 'Const Varible ';
}

// Se tiene error debido a que existe en
// bloque donde fue declarado.
console.log(varVariable, letVariable);
~~~

#### Arrow Functions, Promesas y Parámetros en objetos

~~~js
//Párametros en objetos
let name = 'Jose Luis';
let age = 30;

//es5
let obj = {
  'name': name,
  'age': age
}

let obj2 = { name, age };

console.log(obj);
console.log(obj2);
~~~

~~~js
// arrow function
//
let names = [
  {'name': 'Jose Luis'},
  {'name': 'Laura'},
];

//Se pasa una fusión anónima
name.map(function (item) {
  console.log(item.name);
});

//Se pasa una fusión anónima Arrow Function
name.map(item => console.log(item.name));

//Otra forma para declararlo 
const listName = (name, age) => {
  //body function
};

//Si en la función solo se realiza una operación
const square = num => num * num;
~~~

~~~js
//Promesas

// Una Promise (promesa en castellano) es 
//un objeto que representa la terminación o el 
//fracaso eventual de una operación asíncrona

//Utiliza dos callbacks resolve y reject
//Cuando todo sale bien se ejecuta resolve de locontrario 
//reject 

const promise = (value) => {
  return new Promise((resolve, reject) => {
    if (value) {
      resolve('Todo bien');
    } else {
      reject('Algo salio mal');
    }
  });
};

promise(false)
.then(result => console.log(result))
.catch(error => console.error(error));


//se ejecuta con .then y para capturar el error .catch
//puede utilziar tambien async await para que esta 
//el comportamiento sea como una opearacón sincrona
//para capturar el error utilizamos un bloque de try catch

const executePromise = async(value) =>{
  try {
    let result = await promise(value);
    console.log(result);  
  } catch (error) {
    console.error(error);
  }
} 

executePromise(false);
~~~

#### Clases, Módulos y Generadores

~~~js
//Clases, Módulos y Generadores

class Calculator {
  constructor(){
    this.a = 0;
    this.b = 2;
  }

  sum(a, b) {
    this.a = a;
    this.b = b;
    return this.a +this.b;
  }
}

const calc = new Calculator();
console.log(calc.sum(2,3));
~~~

~~~js
//Modulos
//module.js
const hello = () => {
  return 'Hello module';
}
export default hello;

//index.js
import hello from './module';
hello();
~~~

~~~js
//Generators
// Función especial que retorna valores según la lógica implementada
function* hello(){
  if(true){
    yield 'Hello';
  }
  if(true) {
    yield 'World'
  }
}

const generator = hello();

console.log(generator.next().value);
console.log(generator.next().value);
console.log(generator.next().value);
~~~

## ¿Qué se implemento en ES7?
Nace en Junio del 2016

#### Método que permite include para arreglos y strings
~~~js
let numbers = [1,2,3,4,5,6,7];

if (numbers.includes(7)) {
  console.log('El 7 se encuentra')
} else {
  console.log('El 7 se NO encuentra')
}
~~~

#### ¿Cómo elevar a la potencia.?
~~~js
let base = 4;
let exponenent = 3;
let result = base ** exponenent;

console.log('result: ',result);
~~~

## ¿Qué se implemento en ES8?
Nace en Junio del 2017
~~~js
const data = {
  front: 'Oscar',
  back: 'Isabel',
  desing: 'Ana',
};

//Crear una matriz
const entries = Object.entries(data);
~~~

~~~js
const data = {
  front: 'Oscar',
  back: 'Isabel',
  desing: 'Ana',
};

// Crear un array de string solo con los values.
const values = Object.values(data);
console.log(values);
~~~

~~~js
// Agregar una número de caracteres al inicio
const str = 'Hello';
str.padStart(8,'Hi') //"Hi Hello"
'abc'.padStart(10);         // "       abc"
'abc'.padStart(10, "foo");  // "foofoofabc"
'abc'.padStart(6,"123465"); // "123abc"


str.padEnd(8,'Hi') //"Hello  Hi"
'abc'.padEnd(10);         // "abc       "
'abc'.padEnd(10, "foo");  // "fabcfoofoo"
'abc'.padEnd(6,"123465"); // "abc123"
~~~


#### Async Away

~~~js

const hello = () => {
  return new Promise((resolve, reject) => {
    (true) ? setTimeout(() => resolve('Hello Worls', 300))
    : reject(new Error());
  });
};

const helloAsync = async () => {
  try {
    const helloWorld = await hello();
    console.log(helloWorld);
  } catch (error) {
    console.error(error.message);
  }
};

helloAsync();
~~~

## ¿Qué se implemento en ES9?
Se lanzo el Julio de 2018

~~~js
//Operador de reposo

const data = {
  front: 'Oscar',
  back: 'Isabel',
  desing: 'Ana',
};
let { desing, ...all} = data;
console.log(desing, all); // Ana { front: 'Oscar', back: 'Isabel'}
~~~

~~~js
// operador de propagación
const obj1 = {
  name: 'Luis'
}

const obj2 = {
  ...obj1,
  country: 'MX'
}

console.log(obj2); //{name: 'Luis', country: 'MX'}
~~~


## ¿Qué se implemento en ES10?
Se lanzo en Junio de 2019
~~~js
// flat
let array = [1,2,3,[1,2,3,[1,2,3]]]

console.log(array.flat()); // se llama niveles 
console.log(array.flat(1)); // se llama niveles
~~~

~~~js
//flatMap
let array = [1,2,3,4]
console.log(array.flatMap(values => [value, value * 2]));
~~~

~~~js
//trimStart
let hello = '         hello      ';

console.log(hello.trimStart());
console.log(hello.trimEnd());
~~~

~~~js
//optional error

try {

} catch {
  console.log(error);
}
~~~


~~~js
//optional error

let entries = [["name","Luis"],["country", "MX"]];

 console.log(Object.formEntrie(entries));// { name: 'Luis', country: 'MX' }
~~~










