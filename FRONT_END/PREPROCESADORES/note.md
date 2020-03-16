# Preprocesadores CSS
## Introducción
#### Conceptos básicos de CSS
Cascading Styles Sheet, prácticamente son las reglas que se les aplicas a un documento HTML.
* Extención .css
* Puede ser envevido dentro de la etiqueta style en el documento HTML
* Puede ser exportado con la etiqueta link dentro de la etiqueta header.

**Un estilo CSS esta formado por: Selector, declaración y una propiedad o valor.**

```css
h1 { color: blue; }
```

#### Selectores CSS

Nos permiten seleccionar un elemento de página a la cual vamos a aplicar los estilos.

Selectores:
* Selector universal **\***: Sirve para aplicar estilos a todo el documento.
```css
/*
Todas las etiquetas tendran margen de 0
*/
* {
  margin: 0;
}
```
* Selector de etiqueta: Se utiliza las etiquetas de html a las las cuales podemos agreagrarles estilos.

```css
/*
Las etiquetas h1,h2,p tendran color blanco
*/
h1,h2,p {
  color: white;
}
```
* Selector de ID: este selector se indentfica con **\#**, este debe de setr único
```css
#service {
  color: white;
}

```
* Selector de clase: este selector se indentfica con **.**.
```css
.service {
  color: white;
}
```

* Selector anidado, se aplican estilos a elemetos decendientes

```html
<h1>Services</h1>
<div class="container">
  <h1>Services</h1>
</div>
```
```css
/*
Para este caso todas la etiquetas dentro de la case container seran de color blanco.
*/
.container h1{
  color: white;
}
```

* Selector hijo **>**
```css
/*
  Para este caso los hijos directos de la clase service son los que tomaran los estilos
*/
.service > p{
  color: white;
}
```

* Selector adyacente **+**
```html
<h1>Services</h1>
<h1>Services</h1>
```

```css
/*
  Para este caso a la primera etiqueta de h1 tendra el color negro y las segunda sera de color blanco
*/
h1 {
  color: black;
}
h1+h1{
  color: white;
}
```

* Selector de atributo **input[type: number]**
```html
<input type="text">
<input type="number">
```

```css
/*
  El inout de tipo texto sera de color azul y el de numero rojo
*/
input[type: "number"]{
  color: red;
}

input[type: "text"]{
  color: blue;
}
```

Como determinar el valor de una regla CSS
* ID: 100
* clase: 10
* 

## Evelución de las tecnologías de Front-End
#### Introcucción a los preprocesadores

Los preprocesadores nos ayudan a escribir pseudocódigo de forma modular el cual puede ser transformado de forma que el navagador pueda entender.

Ventajas:
* Tiempo
* Código sencillo
* Modularización

#### Metodologías para estructurar código

Ventajas 
* Evitar redundancia
* Evitar mal uso de propiedades
* Solución de problemas de manejo en sistemas grandes y complejos

#### Introducción a BEM

BEM establece que debemos utilziar clases para nuestros selectores:
* Bloques: Son los elementos más grandes los cuales contienen otros elementos
* Elementos: Estos siempre formam parate de un bloque, estos pueden ser:
  * Textos
  * Botones
  * Imagnes
* Modificadores: Se uzan para darle un estilos espesifico a un bloque o elemento.

#### Guías para creación y mantenimiento de código

* Ser consistentes con la indentación.
* Consistencia con espacios, corchetes, puntos y comas.
* Consistencia de números, de selectores y divisiones.
* Agrupaciones de propiedades.
Uso de ID’s y clases.

## Preprocesadores para HTML

#### Interpolación 

Prácticamente es la anidación de los elementos de HTML

```html
html(lang="en")
  head
    meta(charset="UTF-8")
    meta(name="viewport", content="width=device-width, initial-scale=1.0")
    title Document
    link(rel="stylesheet", href="style.css")
```

#### Variables

Para declarar una variable en pug se realiza de la siguiente manera

```pug
-var titlte = "Title"
```

Para acceder a ella
```pug
h1= titlte

h1 #{titlte}
```

#### Condicionales y Loops

Loops
```pug
-var titles = ["One","Two","Three"]
ul
  each title in titles
    li #{title}
```

Condicionales
```pug
-var user = "Jose Luis"
if user
  a Hola #{user}
else 
  a.button Registro
```


#### Mixins 
Su finalidad es crear una funcionalidad que pueda ser reutilizada pero no de forma autonoma, nos permiten crear bloaues de código que cambian de acuerdo al valor del paramarametro que le enviemos.

```pug
mixin box(image, title, content)
  .box
    .box__image: img(src="", alt="")
    .box__content
      h3 #{title}
      p #{content}


main.content
  +box("image0", "title1", "content2")
  +box("image0", "title1", "content2")
  +box("image0", "title1", "content2")
```

#### Includes y Extends

Se puede utilizar **Includes** para importar archivos externos y **Extends** permite adicionar bloques de código.


## Introducción a Less

#### Importar otros archivos
```less
@import "file.less"
``` 

#### Declaración de variables
```less
@primary-color: #000000;

h1 {
  color: @primary-color;
}
```

#### Funciones ya definidas
```less
//Cambiar la opacidad
color: fade(@color, 50%)
```

#### Mixins

Su funcionalidad es utilidar esta funcionalidad en otros componentes.
```less
// se declara
.box-shadow {
  -webkit-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
  -moz-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
  box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
}

//como se invoca
.box {
  .box-shadow;
}
```

## Introducción a Sass
Syntactically Awesome StyleSheets
Badasa en Ruby

#### Variable
```scss
$font-one = "Lato";

h1 {
  font-family: $font-one;
}
```

#### Imports y Extends

**Import** nos permite escribir código modular separando en diferentes archivos para después importarlos todos en uno solo y tener una base código mucho más ordenada.

**Extends** sirve para insertar los estilos de un selector en otro.

```scss
@import"../componentes/globales.scss";

.class-one {
  background: #FFFFFF;
}

.class-two {
  @extend .class-one;
}
```

#### Mixins

Su funcionalidad es utilidar esta funcionalidad en otros componentes.

```scss
// se declara
@mixin box-shadow {
  -webkit-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
  -moz-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
  box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
}

//como se invoca
.box {
  @include box-shadow;
}
```


#### Funciones

La diferencia entre mixins y funciones es que las funciones por general hacen cálculos y regresan un resultado que es usado como valor de alguna propiedad.

```scss
@function get-opacity($color, $level){
  @return rgba($color, $level);
}

.box {
  color: get-opacity($color, 50%);
}
```

#### Condicionales y Loops
```scss
@each $header, $size in (h1: 30px, h2: 25px, h3: 20px){
  #($header){
    font-size: $size;
    margin: 0;
  }
}

@if () {
//
} @else {
//
}
```

## Stylus

Es el preprocesador CSS más reciente de los tres. Fue creado por TJ Holowaychuk (ex programador de Node.js) y escrito en JADE y Node.js.

#### Variables

```stylus
FontOne =  'Lato'
FontTwo = 'Oswald'


h1
  font-family FontOne
````

#### Mixins

```stylus
container()
  ...

.demo
  container()
```

#### Functiones

```stylus
add(a, b)
  a + b

body 
  padding add(10px, 5)
```

#### Condicionales y Loop

```stylus
compare(a, b)
  if a > b
    higher
  else if a < b
    lower
  else
    equal


compare(5, 2)


for header in 3 2 1
  h{ header }
    font-zise 35px -(5 * header)
    margin 0
```