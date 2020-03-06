# Fundamentos de arquitectura de software

¿Cómo la arquitectura esta envuelata en el desarrollo de software?

## Proceso de desarrollo de software

#### Etapas de proceso de desarrollo 
En el desarrollo de software tradicional tenía etapas muy marcadas donde la salida de una etapa representaba la entrada de otra.

* Análisis de requerimiento: Todo surge a partir de un problema del cual debemos de entender cómo se debe de resolver, ahora en este problema pude existir requerimientos funcionales y no funcionales.
* Diseño de la solución: Análisis profundo del problema del cual debemos obtener las posibles soluciones bien detalladas utilizando modelos.
* Desarrollo y evolución: Implementación de la solución y evaluar el funcionamiento de este, al final tendremos un producto u artefacto de software.
* Despliegue: Se necesita de infraestructura para poder poner el producto en linea, por ejemplo servidores web, balanceadores.
* Mantenimiento y evolución: Desarrollo + Despliegue + Mantenimiento, esta etapa se mantienen hasta que el producto deja de ser necesario.

#### Dificultades en el desarrollo de software
En la etapa de análisis y diseño nos concentramos en los problemas que queremos resolver, estos problemas de dividen en 2 grandes tipos de problemas, esenciales y accidentales.

Los problemas esenciales se dividen en 4, que tratan sobre entender el concepto que vamos a resolver:
* Complejidad: Cuando el problema es complejo.
* Conformidad: En qué contexto se va a utilizar.
* Tolerancia al cambio: Va a poder cambiarse y si podemos adaptarnos a los cambios.
* Invisibilidad: El software no es tangible ya que su forma esta plasmada en código.

* Problemas Accidentales: esta basada prácticamente en la infraestructura a utilizar por ejemplo tecnologías, lenguajes, frameworks etc.

* Lenguajes de alto nivel
* Multi-procesamiento
* Entornos de programación

*No hay un proceso que pueda solucionar un problema esencial*

* Si la solución es muy compleja, tal vez la opción es no desarrollar y mejor comprar software.
* No desarrollar, Aprovechar Open source: utilizar módulos ya desarrollados y personalizar.
* Metodologías ágiles, la idea es obtener feedback muy rápido. Se obtiene un prototipo rápido: la idea es obtener feedback de forma muy rápido para saber si estamos solucionando el problema.
* Desarrollo evolutivo: en donde a partir de un producto pequeño podemos iterarlo para obtener algo más complejo.
* Grandes diseñadores: Diseñar un problema con gran calidad.

#### Roles
Es importante diferenciar del ROL y puesto de trabajo ya que hay roles que pueden ser desarrolladas por la misma persona.

* Experto del dominio: Experto en el negocio que nos ayuda a entender el problema a resolver, stakeholders en las metodologías ágiles.
* Administrador de sistemas DEV OPS: Rol de operaciones y desarrollo, SRE (Site Reability, Enginier).
* Equipo de desarrollo: QA, Testing, Desarrolladores, Arquitectos todos los involucrados en el desarrollo
* Gestor de proyecto facilitador: Lleva al equipo para el desarrollo en proceso iterativo.


## Introducción a la arquitectura de software
#### ¿Qué es la arquitectura de software?
* La estructura del sistema esta compuesta por elementos de software, sus propiedades visibles y sus relaciones (Bass, Clemment, Kazman 2003).
* Conjunto de desiciones (Theory and Practice 2010).
* Cualquier cosa importante (Fowler 2002).

#### Importancia de la comunicación Ley de Conway
Cualquier organización que diseña un sistema producirá un diseño cuya estructura es una copia de la estructura de comunicación de la organización.

#### Objetivos del arquitecto
El arquitecto conecta a todos los stakeholder con el sistema a construir, analizando los requeriemientos de los stakeholder.
* Cliente: Entregas, respetando tiempos de entrega y costos
* Manager: Cumplir con requerimientos del cliente, crear equipos de trabajo auto gestionables.
* DEV: Que se sea fácil de desarrollar y mantener.
* Usuario: Que el producto cumpla con el objetivo.
* Tester QA: Que el producto sea sencillo de probar.

El arquitecto es el encargado de tomar las decisiones para que el impacto del diseño sea agradable para todos los involucrados.

#### Arquitectura y metodologias
Metodología tradicional: diseñar solución a gran escala.
Metodología ágil: emerge de un equipo autogestionado.

## Análisis de requerimientos

#### Entender el problema
Comprender el problema, lo importante es separar la comprensión de la propuesta de solución y debemos evitar mezclarlo con la parte tecnológica, esto no debe de influir en la propuesta de solución.

Se debe de separar en espacio del problema y espacio de la solución.

Espacio del problema: saber lo que voy a resolver sin entrar en el cómo.
* Idea
* Criterios de de éxito
* Historias de usuarios

Espacio de la solución: Entra en el detalle del como "detalles técnicos".
* Diseño
* Desarrollo
* Evaluación
* Criterios de aceptación
* Despliegue

#### Requerimientos
Una vez comprendido el espacio del problema y de solución vamos a la parte del requerimiento.

Requerimiento de Producto: ¿Qué es lo que el producto necesita?.
Requerimiento de producto se divide en 3:
* Capa de negocio: Reglas de negocio que alimentan a los requerimientos. [Requerimientos de negocio, Reglas de negocio]
* Capa de usuario: Tiene que ver como el usuario se desenvuelve utilizando el sistema.[Requerimientos de usuario, Atributos de calidad, Requerimientos No funcionales]
* Capa funcional: Requerimientos del sistema, ¿Qué cosa tiene operativamente? Restricciones operativas.[Requerimientos de sistema, Requerimientos Funcionales, Restricciones]

Requerimientos de producto:
Funcionales: Historias de usuarios, hablan específicamente de lo que hace el sistema, cómo el sistema responde a un estimulo.
No funcionales: Son los que agregan cualidades al sistema, por ejemplo que él login sea más seguro, en este caso se agrega una cualidad. Crear reportes en tiempo real pueda considerarse como no funcionales.

Los requerimientos significativos engloban todos aquellos que afecte a hora de diseñar.

Requerimientos de proyectos: Fechas de entrega, planes
Requerimientos de proyecto: Tiene que ver con el rol de gestor de proyecto:
* Recursos
* Capacitación
* Certificaciones
* Documentos de usuarios
* Infraestructura
* Licencias
* Plan de despliegue
* Plan de transiciones
* Infraestructura

#### Riesgos
Es importante identificar los riesgos y plantear los posibles escenarios en caso de que estos sucedan con el objetivo de asegurar las soluciones arquitectónicas.

Se pueden identificar:
* En la toma de requerimientos: dificultad/ complejidad
* En los atributos de calidad: Incertidumbre, en cuanto más incertidumbre más alto el riesgo.
* Conocimiento del dominio: Riesgo genérico: aquellos que se pueden atacar de forma estándar.

una vez identificados se debe de priorizar, recuerde que no se debe priorizar todos, si no aquellos que pongan en riesgo a la propuesta de solución.

#### Restricciones
Restricciones que limitan las opciones del sistema tanto de diseño y desarrollo.

* Los stakeholders son los que dan las restricciones, "Reglas de negocios".
* La integración con otros sistemas "Restricciones técnicas".
* Ciclo de vida del producto "Preciso de evolución de producto".

El arquitecto debe de balancear entre requerimientos y restricciones.

Realizar reto de App.

## Estilos de arquitectura
Es algo genérico que se puede reutilizar para resolver un problema en especifico.

Colecciones de decisiones de diseño aplicados en un contexto determinado esperando tener el éxito que sé obtuvo anteriormente.

El panorama arquitectónico.
Puede estar implícito dentro de una tecnología.
Se debe de balancear beneficios y contras de cada arquitectura.

#### Llamado y retorno
Cada uno de los componentes hace invocaciones a los componentes externos y estos retornan información.

Cada llamado espera una respuesta.

* Programa y subrutinas: Instrucciones secuenciales que el programa ejecuta una por una.

* Orientada a objetos: Se utiliza en sistemas que sabemos vamos a utilizar por mucho tiempo. En este caso la abstracción ya no es una subrutina, ahora tenemos objectos que se hacen llamados entre sí y esperan respuesta.

Arquitectura de multinivel.
Un ejemplo es la arquitectura **Cliente servidor**.

#### Flujo de datos
En este caso no nos preocupamos tanto por la secuencia de ejecución sino por los datos que van a ir de un lugar a otro.

* Lote secuencial: Procesar algo y que cuesta ser procesado, por ejemplo un reporte.

* Flujo de datos: Diferentes aplicaciones conectadas en tiempo real lo cual no dependen del usuario para ser ejecutados.
Por ejemplo en los comando de linux que la salida de un comando puede ser la entrada de otro, como por ejemplo.
~~~ 
grep | sed | grep | sed 
~~~ 

#### Centradas en datos
Se tienen múltiples componentes cada uno tiene una función específica.

* Pizarrón: Por ejemplo para realizar una tarea donde se necesitan varias partes involucradas donde es necesario que todas ellas se terminen para poder tener una salida.

* Centrado en datos: Ejemplo común es cuando dos aplicaciones utiliza la misma base de datos, cualquiera de los componentes no se comunican entre sí pero si escriben en la base de datos.

* Sistema experto o etilo basado en reglas: Algún componente de tipo cliente va comunicarse con otro que va tratar de inferir las reglas y determinar si es una regla o una consulta, posteriormente consulta a una base de conocimiento.

Concentración de cómo hacer o guardar algo.

#### Componentes independientes
Existen dos grupos de componentes.
Cada aplicación se desarrollan por separados desacoplados 
* Invocación implícita: pueden mandarse mensajes entre si sin saber quién los esta mandando llamar.
    * basados en eventos
        * Publicar - Suscribir
        * Orientado a servicios 2.0: Se tiene un bus inteligente que sabe que hacer, **Enterprise Service Bus E.S.B**.

 
* Invocación explicita: Desarrollar componentes que se conocen entre si pero están desacoplados. 
    * Orientado a servicios 1.0

#### Comparar estilos
* Estilo monolítico: donde se despliega un solo artefacto.
    * Eficiencia, puede ser optimizado, fáciles de probar.
    * Curva de aprendizaje: Es más fácil comprender de que como se construye.
    * Capacidad de prueba: Más fácil de realizar test completos ya que todos los módulos se encuentran juntos.
    * Capacidad de modificación: Más fácil de integrar nuevos módulos.

* Estilo distribuido: donde se tienen despliegues diferentes pero se comunican entre si.
    * Modularidad: Cada producto se despliega por separado
    * Disponibilidad: Que su un producto no esta disponible no significa que todos lo estén.
    * Uso de recursos: Utiliza menos recursos ya no es tan grande.
    * Adaptabilidad:

A partir de los riesgos restricciones y requerimientos podremos elegir una arquitectura de acuerdo a nuestro problema a solucionar.
