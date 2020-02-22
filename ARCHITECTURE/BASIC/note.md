# Fundamentos de arquitectura de software

Como la arquitectura esta envuelata en el desarrollo de software.
## Proceso de desarrollo de software
#### Etapas de proceso de desarrollo 
En el desarrollo de software tradicional tenía etapas muy marcadas donde la salida de una etapa representaba la entrada de otra.

* Análisis de requerimiento: Todo surge apartir de un problema del cual debemos de entender como se debe de resolver, ahora en este problema pude existir requerimientos fucionales y no funcionale.
* Diseño de la solución: Análisis profundo del problema del cual debemos obtener las posibles soluciones bien detalladas utilizando modelos.
* Desarollo y evolución: Implementación de la solución y evaluar el funcionameinto de este, al final tendremos un producto artefacto de software.
* Despliegue: Se necesita de infraestructura para poder poner el producto en linea, por ejemplo servidores web, balanseadores.
* Mantenimiento y evolución: Desarrollo + Despliegue + Mantenimiento, esta etapa se mantienen hasta que el producto deja de ser necesario.

#### Dificultades en el desarrollo de softaware
En la etapa de análisis y diseño nos concetramos en los problemas que queremos resolver, estos problemas de dividen en 2 grandes tipos de problemas, esenciales y accidentales.

Los problemas escenciales se dividen en 4, que tratan sobre entender el concepto que vamos a resolver:
* Complejidad: Cuando el problema es complejo.
* Conformidad: En que contexto se va a utilizar.
* Tolerancia al cambio: Va a poder cambiarse y si podemos adaptarnos a los cambios.
* Invisibilidad: El software no es tangible, ya que su forma esta plasmada en código.

Accidentales: esta basada practicamente en la infraestructura a utilizar por ejemplo tecnologias, lenguajes, frameworks etc.

* Lenguajes de alto nivel
* Multi-procesamiento
* Entornos de programación

*No hay un proceso que pueda solucionar un problema escencial*

* Si es muy complejo tal vez la opción es no desarrollar y mejor comprar software.
* No desarrollar, Aprovechar Open source: utilizar modulos ya desarrollados y personalizar.
* Metodologias agiles, la idea es obtener feedback muy rapido. Prototipado rapido: la idea es obtener feedback de fora muy rapido para saber si estamos solucionando el problema.
* Desarrollo evolutivo: en dónde apartir de un producto pequeño podemos iterarlo para optener algo más complejo.
* Grandes diseñadores: Diseñar un problema con gran calidad.

#### Roles
Es importante diferenciar del ROL y puesto de trabajo ya que hay roles que pueden ser desarrolladas por la misma persona.

* Experto del dominio: Experto en el negocio que nos ayuda a entender el problema a resolver, stakeholders en las metodologias agiles.
* Administradr de sistemas DEV OPS: Rol de operaciones y desarrollo, SRE (Site Reability, Enginier).
* Equipo de desarrollo: QA, Testing, Desarrolladores, Arquitectos todos los involucrados en el desarrollo
* Gestor de proyecto facilitador: Lleva al equipo para el desarrollo en proceso iterativo.


## Introducción a la arquitectura de software
#### ¿Qué es la arcuitectura de software?
* La estructura del sistema esta compuesta por elementos de software sus propiedaeds visebles y sus relaciones (Bass, Clemment, Kazman 2003).
* Conjunto de desiciones (Theory and Practice 2010).
* Cualquier cosa importante (Fowler 2002).

#### Importancia de la comunicación Ley de Conway
Cualquier organización que diseña un sistema producirá un diseño cuya estructura es una copia de la estructura de comunicación de la organización.

#### Objetivos del arquitecto
El arquitecto coneta a todos los stakeholder con el sistema a construir, análizando los requeriemitos de los stakeholder.
* Cliente: Entregas, respetando tiempos de entrega y costos
* Manager: Cumplir con requerimientos del cliente, crear equipos de trabajo autogestionables.
* DEV: Que se sea facil de desarrollar y mantener.
* Usuario: Que el producto cumpla con el objetivo.
* Tester QA: Que el producto sea sencillo de probar.

El arquitecto es el encargado de tomar las deciaciones para que el impacto del diseño sea agradable para todos los involucrados.

#### Arquitectura y metodologias

Metodología tradicional: diseñar solución a gran escala.
Metodología Agil: emerge de un equipo autogestionado.

## Análisis de requerimientos

#### Entender el problema
Comprender el problema, lo importante es separar la comprención de la propuesta de solución. debemos evitar mesclar unir la parte tecnologica, esto no debe de influir en la propuesta de solución.

Se debe de separar en espacio del problema y espacio de la soulicón.

Espacio del problema: saber lo que voy a resolver sin entrar en el como.
* Idea
* Criterios de de éxito
* Historias de usuarios

Espacio de la solución: Entra en el detalle del como "detalles tecnicos".
* Diseño
* Desarrollo
* Evaluación
* Criterios de aceptación
* Despliegue

#### Requerimientos
Una vez comprendido el espacio del problema y de solución vamos a la parte del requerimiento.

Requrimiento de Producto: Que es lo que el producto necesita.
Requerirmiento de producto se divide en 3:
* Capa de negocio: Reglas de negocio que alimentan a los requerimientos. [Requemientos de negocio, Reglas de negocio]
* Capa de usuario: Tine que ver como el usuario se desenvuelve utilizando el sistema.[Requemientos de usuario, Atributos de calidad, Requemientos No funcionales]
* Capa fucional: Requerimientos del sistema, ¿Qué cosa tiene operativamente? Restricciones operativas.[Requerimientos de sistema, Requemientos Funcionales, Restricciones]

Requerimientos de producto:
Fucionales: Historias de usuarios, hablan espesificamente de lo que hace el sistema, como el sistema responde a un estimulo.
No funcionales: Son los que agregan cualidaedes al sistema, por ejemplo que el login sea más seguro, agregar cualidad, por ejemplo la seguridad. reporte en tiempo real pueda considerarse como no funcionales.

Los requrimientos significativos engloban todos aquellos que afete a hora de diseñar.

Requerimientos de proyectos: Fechas de entrega, planes
Requerimientos de proyecto: Tiene que ver con el rol de gestor de proyecto:
* Recursos
* Capacitación
* Ceritificaciones
* Documentos de usuarios
* Infraestructura
* Licencias
* Plan de despliegue
* Plan de transicions
* Infraestructura

#### Riesgos
Es importante identificar los riesgos y plantear los posibles escenarios en caso de que estos sucedan con el objetivo de asegurar las soluciones arquitectonicas.

Se pueden identificar:
* En la toma de requerimientos: dificultad/ complejidad
* En los atributos de calidad: Incertidumbre, encuanto más incertidumbre más alto el riesgo.
* Conocimiento del dominio: Riesgo generico: aquellos que se pueden atacar de forma estadar.

una vez identificados se debe de priorizar, recuerde que no se debe priorizar todos, si no aquellos que pongan en riesgo a la propuesta de solución.

#### Restricciones
Restricciones que limitan las opciones del sistema tanto de diseño y desarrollo.

* Los stakeholders son los que dan las restricciones, "Reglas de negocios".
* La integración con otros sistemas "Restricciones tecnicas".
* Ciclo de vida del producto "Prceso de evolución de producto".

El arquitecto debe de balancearentre requerimientos y restricciones.

Realizar reto de App.

## Estilos de arquitectura
Es algo generico que se puede reutilizar para resolver un problema en espesifico.

Colecciones de decisiones de diseño aplicados en un contexto determinado esperando tener el exito que se obtuvo anteriormente.

El panorama arquitectonico.
Puede estar implicito dentro de una tecnologia.
Se debe de balancear beneficios y contras de cada arquitectura.

#### Llamado y retorno
Cada uno de los componentes hace invocaciones a los componentes externos y estos retornan información.

Cada llamado espera una respuesta.

* Programa y subrutinas: Instrucciones secuenciales que el programa ejecuta una por una.

* Orientada a objetos: Se utiliza en sistemas que sabemos vamos a utilizar por mucho tiempo. En este caso la abastracción ya no es una subrutina, ahora tenemos objectos que se hace llamdos entre si y esperan respuestsa.

Arquitectura de multinivel.
Un ejemplo es la arauitectura Cliente servidor.

#### Flujo de datos
En este caso no nos precupamos tanto por la secuencia de ejecución sino por los datos que van a ir de un lugar a otro.

* Lote secuencial: Procesar algo y que cuesta ser procesado, por ejemplo un reporte.

* Flujo de datos: Diferentes aplicaciones conectadas en tiempo real lo cual no dependen del usario para ser ejecutados.
Por ejemplo en los comando de linux que la salida de un comando puede ser la entrada de otro, como por ejemplo.
~~~ 
grep | sed | grep | sed 
~~~~ 

#### Centradas en datos
Se tienen múltiples componentes cada uno tiene una fución espesifica.

* Pizarron: Por ejemplo para realizar una tarea donde se necesitan varias partes involucradas donde es necesario que todas ellas se terminen para poder tener una salida.

* Centrado en datos: Ejemplo común es cuando dos aplicaciones utiliza la misma base de datos, cualquira de los componentes no se comunican entre si pero si escriben en la base de datos.

* Sistema experto o etilo basado en reglas: Algun componente de tipo cliente va comunicarse con otro que va tratar de inferir las reglas y determir si es una regla o una consulta  posterirmente consulta a una base de conocimiento.

Concetración de como hacer o guardar algo.

#### Componentes independientes
Existen dos grupos de componetes.
Cada aplicación se desarrollan por separados desaclapados 
* Invocación implicita: pueden mandarse mensajes entre si sin saber quien los esta mandando llamar.
    * basados en eventos
        * Publicar - Suscribir
        * Orientado a servicios 2.0: Se tiene un bus inteligente que sabe que hacer, enterprise service bus E.S.B.

 
* Invocación explicita: Desarrollar componentes que se conocen entre si pero estandesacoplados. 
    * Orientado a servicios 1.0

#### Comparar estilos
* Estilo monolitico: donde se despliega un solo artefacto.
    * Eficiencia, puede ser optimizado, faciles de probar.
    * Curva de aprendizaje: Es más fáccil comprender de que como se construye.
    * Capacidad de prueba: Más fácil de realizar test completos ya que todos los moduloes se encuentran juntos.
    * Capacidad de modificaión: Más fácil de integrar nuevos módulos.

* Estilo distribuido: donde se tienen despligues diferentes pero se comunican entre si.
    * Modularidad: Cada producto se despliega por separado
    * Disponibilidad: Que su un producto no esta disponible no significa que todos lo esten.
    * Uso de recursos: Utiliza menos recursos ya no estan grande.
    * Adaptabilidad:

Apartir de los riesgos restricciones y requetimientos podremos elegir una arquitectura de acuerdo a nuestro problema solucionar.


Errores:
1 En el contexto de metodologías tradicionales, ¿en qué etapa del proceso de desarrollo de software se toman las decisiones de arquitectura?
Diseño de la solución dónde el arquitecto y analista o equipo de desarrollo.

2 De las formas en las que podemos trabajar con las dificultades esenciales, ¿cuál es la que más involucra a los arquitectos de software?
Desarrollo de software evolutivo

10 ¿Cuál de estas prácticas es esencial para un arquitecto en contexto de metodologías ágiles?
No tomar deciciones de arquitectura ya que emerge del equipo autogestionado.

17 ¿Cuál de los siguientes requerimientos funcionales incluye explícitamente un requerimiento no funcional?
Canjear acumuldos 


De las formas en las que podemos trabajar con las dificultades esenciales, ¿cuál es la que más involucra a los arquitectos de software?
¿Cuál de estas prácticas es esencial para un arquitecto en contexto de metodologías ágiles?

¿Cuál de los siguientes requerimientos funcionales incluye explícitamente un requerimiento no funcional?