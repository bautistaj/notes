# Docker Swarm

Herramienta que ofrece docker para poder escalar las aplicaciones.

## Conceptos básicos 
### ¿Qué es Swarm?
Docker Swarm es un herramienta de orquestación, esto permite el manejo de multiples contenedores desplegados en multiples maquinas.

### El problema de la escala. ¿Qué pasa cuándo una computadora sola no alcanza?

* Escalabilidad: Poder aumentar el poder computo de un servidor para poder servir a más usuarios. Podemos escalar de 2 formas:
  * Vertical: Agregar más Hardware
  * Horizontal: Tener muchos servidores donde se distribuye la carga.

* Disponibilidad: Capasidad de un servicio de estar disponibilidad 24/7.

### Arquitectura docker swarm
Par la arquitectura de Swarm, se ven involucrados dos tipos de servidores:

* Manager: Son nodos de la administración del cluster. 
* Workers: Es donde se va a ajecutar las aplicaciones, la parte principal.

Manager y Workers deben de tener la misma version de dokerdeamon y tener visibilidad entre ellos en la misma red.

### Preparando tus proyectos con docker swarm: 12 factores.

!2 fatores que se deben de tener en cuenta para empezar a utilizar Swarm en tus aplicaciones.

[12 Factores](https://12factor.net/)

  * Codebase: El código debería estar en un repo.
  * Dependencies: Las dependencias deben de estar en un archivo de configuración.
  *  Configuration: Configuración de todos los ambientes con el mismo código.
  *  Baking Services: Servicios que son necesarios para nuestar aplicación, estos se deberían tratar como servicios externos los cuales deben de tener una configuración para establecer la comunicación.
  *  Build, Release and Run: Estas faces en el flujo de desarrollo deben de estar bien separadas.
  *  Processes: La app debe poder ejecutarse sin algún tipo de estado, que el fucionamiento que realice debe ser atomica, de todo lo que necesite debe de tener un service configuration.
  *  Port Binding: La app debería poder exponerse así misma y no debe existir un intermediario.
  *  Concurrency: Que la app pueda correr con multiples intancias en paralelo.
  *  Disposability: La app debe de tener la capacidad de destriurse rapido y levantarse muy rapido y poder cambiar de lugar.
  *  Dev/Prod parity: Tener las mismas espesificaciones en los diferentes servidores.
  *  Logs: Flujos de bytes.
  *  Admin processes: Poder administrar las apps sin la neceisdad de inciar sesion como adminitrador para hacer dichas tareas.


## Primeros pasos.

### Tu primer docker swarm

Para inicializar **Swarm** solo ejecutamos

```bash
docker swarm init 
```

Cabe mencionar que este nodo se inicializa como un **manager**

Para agregar un nodo de tipo **worker** necesitamos ejecutar el siguiente comando.

```bash
docker swarm join --token <token> <ip>
```

Para agregar un **manager** ejecutamos y seguimos las intrucciones. 
```bash
docker swarm join-token manager
```

Listamos los nodos disponibles
```bash
docker node ls
```

Inspeccionar el nodo, pues usar **self** o bien el ID del container.
```bash
docker node inspect self
```

Para salir de docker Swarm ejecutamos
```bash
docker swarm leave --force
```
Debemos tener cuidado cuando salimos de un nodo, si este es de tipo **worker** no hay problema, el problema se presenta cunado intentamos salir de un **manager**.



### Fundamentos de docker swarm, Servicios

Los servicios de Swarm usan un modelo declarativo, lo que significa que el estado del servicio los pudes definir y confiar en docker para que lo mantenga.

Comando para crear un servicio
```bash
docker service create --name pinger alpine ping wwww.google.com
```

Listar los servicios 

```bash
docker service ls 
```


### Entendiendo el ciclo de vida de un servicio

Para ver el estatus de un servicio.
```
docker service ps service_name
```

Cliente: 
  * docker service create
Nodo manager:
  * Crea el servicio
  * Creaa tareas del servicio y asigna una IP
  * Asigna tareas a nodos
Nodo Worker
  * Recibe la descriptción de la tarea
  * Prepaa la tarea
  * Ejecuta contanedores


Comando para inpeccionar un servicio
```bash
docker service inspect service_name
```

Revisar los logs
```bash
docker service logs -f service_name
```

Eliminar un servicio
```bash
docker service rm service_name
```


