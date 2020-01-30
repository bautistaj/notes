#SQL y MySql


####¿Que es una base de datos?
Una Base de datos es un lugar donde se almacenan una gran cantidad de datos que posteriormente a través de un proceso se convierten en información. 

####Comandos MySql
Iniciar sesión
~~~
    mysql -u user-name -p
~~~
Donde -u es usuario y -p es password.
___
~~~
    use data-base-name;
~~~
Cambiar de base de datos a utilizar.
___

~~~
    show full columns from books;
~~~
Muestra el detalle completo de la tabla.
___


####Motores de base de datos
Los motores de base datos más conocidos son __Innodb__ y __Myissam__, entre ambos existen ciertas diferencia notables que vale la  pena mencionar para saber cual eligir.

Innodb considerado como un motor de base de datos transaccional conforme [ACID](https://dosideas.com/noticias/base-de-datos/973-acid-en-las-bases-de-datos) con la capacidad de commit, rollback, recuperación de fallos.

Myissam es un motor de base de datos que trata tablas no transaccionales lo cual lo hace más rápido en la lectura y escritura de datos.

#####Algunas ventajas y desventajas
Innodb
+ Soporte de transacciones.
+ Bloqueo de registros.

Myissam
+ Mayor velocidad en la recuperación de datos.
+ Recomendable para aplicaciones donde predominan la sentencia __select__ que los __inserts/updates__.

####Cardinalidad
La cardinalidad son simplemente las relaciones que pueden existir entre las tablas de una base de datos.
+ uno a uno
+ uno a muchos
+ muchos a a uno

####Lenguaje DDL
Lenguaje de definición de datos:
+ Create: crear objectos tales como vistas, tablas, store procedures e indices.
+ Drop: Utilizado para eliminar objectos como vistas, store procedures, tablas.
+ Alter: Empleado para editar tablas agregando campos o cambiando la definición de los mismos.

Una buena practica es que el nombre de la tabla debe ser un sustativo en plurarl en ingles.

~~~
create table if not exists books(
    id Integer unsigned primary key auto_increment,
    author Integer,
    title varchar(100) not null,
    year integer unsigned default 1990,
    language varchar(2) not null default 'es' comment 'ISO 639',
    cover_url varchar(500),
    price double(6,2) not null default 10.0,sellable tinyint () defaul 1,
    copies integer not null default 1,
    description text
);
~~~

####Lenguaje DML
Lenguaje de manipulación de datos proporcionado por los sistemas gestores de base de datos que permite tareas de consultas o modificación de datos.

##### Select
~~~
select * from table where field = 'value'
~~~
##### Insert
~~~
insert into table (field1, field2) values (value1, value2);
~~~

##### Update
~~~
udate table field = 'value to modify' where field = value
~~~
##### Delete
~~~
delete from table where field = value;
~~~ 

##### Inner JOIN
Es considerada la forma más fácil de obtner información, practicamente seobtienen todos las filas dela tabla A que conciden con la table B.

~~~
select * from table_a as a inner join table_b as b on a.pk = b.pk;
~~~ 

##### Left JOIN
Se selecciona todas las filas de la tabla A y ademas de las que coincidan de la tabal B.

~~~
select * from table_a as a left join table_b as b on a.pk = b.pk;
~~~ 
##### Right JOIN
Se selecciona todas las filas de la tabla B y ademas de las que coincidan de la tabal A.

~~~
select * from table_a as a left join table_b as b on a.pk = b.pk;
~~~ 
##### Outer JOIN
Retorna todas las filas de ambas tablas ademas de hacer la únion entr las tablas que coinciden.

~~~
select * from table_a as a outer join table_b as b on a.pk = b.pk;
~~~ 
##### Left excluding JOIN
Para este caso retorna todas las filas de la tabla A que no tengan ninguna coincidencia con la tabla B.
~~~
select * from table_a as a left join table_b as b on a.pk = b.pk where b.pk is null;
~~~ 
##### Right excluding JOIN
Para este caso retorna todas las filas de la tabla B que no tengan ninguna coincidencia con la tabla A.
~~~
select * from table_a as a right join table_b as b on a.pk = b.pk where b.pk is null;
~~~ 
##### Outer excluding JOIN
Para este caso retorna todas las filas de ambas tablas que no tengan coincidencias.
~~~
select * from table_a as a full outer join table_b as b on a.pk = b.pk where a.pk is null or b.pk is null;
~~~ 









