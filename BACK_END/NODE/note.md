# Node

#### Características
* Entorno de ejecución fuera de un navegador.
* Lenguaje concurrente.
* MonoHilo.
* Comunicación asyncrono
* Motor V8 de google, convierte el lenguaje de java script a código maquina.
* Funcionamiento basado en módulos.
* Orientado a eventos lo que permite la programación de forma reactiva.

#### EventLoop
Bucle de eventos y la razón por la que JavaScript trabaja de forma asyncrona.

* No se bloquea
* Alta concurrencia.

EventQUEUE -> Envia al event loop (Si es posible los resuelve en el momento si no lo manda a) -> ThreadPool
ThreadPool por cada tarea crea un nuevo hilo en nuestro procesador y cundo termina lo manda alevent loop y este a queue.


#### MonoHilo: Implicaciones de diseño de seguridad
Si existe un error este detendrá todo el flujo de el programa ya que todo trabaja en el mismo hilo, 
razón por la que debemos de tener cuidado.

#### Variables de entorno
Variables que se definen en el servidor, para poder leer estas variables de con process.env.NOMBRE-VARIABLE.

Process es un objeto que proporciona información y control sobre proceso actual de node, este simpre es global.

#### Herramientas para ser más felices: Nodemon y PM2
Nodemon crea una herrmienta que cada que hay cambio de forma automarica.
PM2 para entorno de Producción, administración de procesos.

#### CallBacks
Como gestionar algo asyncrono.







