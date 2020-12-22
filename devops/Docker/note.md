# Fundamentos de Docker

# Introducción

## Introducción
Durante el desarrollo de software vamos a tener diferentes problamaticas que resolver, como por ejemplo:
las construcción, distribución y la ejecuón. Cada uno de estos problemas nos enfrentamos todos los desarrolladores.

Acontinuacón detallamos más las problematicas antes mencionadas.

Escribir código es solo una parte de la contrucción de Software y algunos problematicas a las que nos enfrentamos se describen acontinuacón.
	
* Entorno de desarrollo: que nuenstro entorno de desarrollo es diferente a los de stagin, qa o producción.
* Dependencias: las dependencias que utilizamos son diferentes entre cada desarrollador.
* Entorno de ejecución: diferentes sistemas operativos que se utlizan en cada uno de nuestros entornos.
* Equivalencia con entorno productivo: capacidadades de las intancias utlizadoas, como por ejemplo las version de SO, memoria entre otras.
* Servicios externos: las conexiónes a las bases dedatos o bien el consumo de apis

Distribución de software: Tu código tiene que transformarse en un artefacto, o varios, que puedan ser transportados a donde tengan que ser ejecutados.

* Divergencia de repositorios
* Divergencia de artefactos
* Versionado

Ejecutar Software: La máquina donde se escribe el software siempre es distinta a la máquina donde se ejecuta de manera productiva.

* Compatibilidad con el entorno productivo
* Dependencias
* Disponibilidad de servicios externos
* Recursos de hardware.

## Virtualización
Versión virtual de algún recurso como hardware, sitema operativo, dispositivo de almacenamiento o recurso de red.

Con palabras más simples, es que nos permite atacar los tres grandes problemas del desarrollo de software profecionales.

Ya  antes se a propuesto formas para atacar los problemas antes mencionado como por ejemplo las maquinas virtuales, acontinuación se describe algunas problematicas que presnetan.
* Peso: que va en el orden de GB.
* Consto de administración: necesitan mantenimiento al igual que un maquina.
* Múltipls formatos: VDI, VMDK, VHD.


Los contenedores son practicamnte la estandarización

* Flexibles
* Livianos
* Protables
* Bajo acoplamineto
* Escalables
* Seguros

## ¿Qué es y como funciona Docker?
* Docker deamon, es un servicion el cual maneja todas las entidades con las cuales utiliza docker, encargado directo de conmunicación con SO.
* Docker API.
* Client Docker.


4 entidades importantes:
* Container
* Image
* Data volumes
* Network


# Contenedores

## Comandos de docker

Arrancar un contenedor.
* docker run <image_container>
* docker run hello-world

Arrancar un contenedor asignándole un nombre.
* docker run --name <name_container> <image_container>
* docker run --name contenedor_test ubuntu

Arrancar un contenedor con una terminal interactiva. Pasándole una shell para acceder al contenedor.

 * docker run -it <image_container> <shell>
 * docker run -it ubuntu bash

Arrancar un contenedor. Mapeando un puerto del host a un puerto del contenedor.

puerto_host : puerto_contenedor
* docker run -p <host_port>:<container_port> <image_container>
* docker run -p 8080:80 nginx


Arrancar un contenedor con un volume.
* docker run -v <volume_name>:<mount_point>:<options> <image_container>
* Volume -> test
* Punto de montaje en el contenedor -> /apps
* Opciones -> rw (Lectura y escritura)
* docker run -v test:/apps:rw nginx



Arrancar un contenedor con un bind mount.
* docker run -v <shared_folder>:<mount_point>:<options> <image_container>
* Ruta del host a compartir -> /home/application
* Punto de montaje en el contenedor -> /apps
* Opciones -> ro (Solo lectura)
* docker run -v /home/application:/apps:ro ubuntu

Arrancar un contenedor con tmpfs.
* docker run \
--mount type=tmpfs,destination=<mount_point>,tmpfs-mode=<permisos>,tmpfs-size=<bytes_size> \
<image_container>
Ejemplo:

* Punto de montaje en el contenedor -> /temporal
* Permisos -> Todos los permisos solo para el propietario.
* Tamaño del FS -> 21474836480 bytes = 20G
* docker run \
--mount type=tmpfs,destination=/temporal,tmpfs-mode=700,tmpfs-size=21474836480 \
nginx


Lista de los contenedores activos.
* docker ps


Lista de todos los contenedores activos e inactivos del sistema.
* docker ps -a

Lista los ID de todos los contenedores.
* docker ps -aq

Debugging

Inspeccionar la data de un contenedor.
Por su ID:
* docker inspect <id_container>

Por su nombre:
* docker inspect <name_container>

Aplicando filtros. Por ejemplo buscando las variables de entorno:
* docker inspect -f '{{ json .Config.Env }}' <name_container>

Ver los logs del contenedor.

docker logs <name_container>
- Eliminando contenedores
🔹 Eliminar un contenedor que no este arriba.

Se puede hacer tanto por nombre como por ID.
* docker rm <name_container>

Eliminar un contenedor aunque este arriba. Forzándolo.

Se puede hacer tanto por nombre como por ID.
* docker rm -f <id_container>


Eliminar todos los contenedores que no esten arriba a la vez.
* docker rm $(docker ps -aq)


## Conceptos fundamentales de Docker: contenedores
Un contenedor es una agrupación lógica la cual esta limitada a los recursos que puede puede acceder.

Un contenedor es una maquina virtual la cual configuramos a los recursos que puede acceder.

## Comprendiendo el estado de Docker

Comandos:

* docker run hello-world (corro el contenedor hello-world)
* docker ps (muestra los contenedores activos)
* docker ps -a (muestra todos los contenedores)
* docker inspect <containe ID> (muestra el detalle completo de un contenedor)
* docker inspect <name> (igual que el anterior pero invocado con el nombre)
* docker run –-name hello-platzi hello-world (le asigno un nombre custom “hello-platzi”)
* docker rename hello-platzi hola-platzy (cambio el nombre de hello-platzi a hola-platzi)
* docker rm <ID o nombre> (borro un contenedor)
* docker container prune (borro todos lo contenedores que esten parados)




## Ciclo de vida de los contenedores.

Cada vez que un contenedor se ejecuta, lo que pasa es que un nuevo proceso se ejecuta.

Un contenedor corre simpre y cunado su procesos principal esta corriendo.

Entonces para mantener un contenedor corriendo podemos ejecutar.
* docker run --name alwaysup --detach ubuntu tail -f /dev/null

Y para connectarnos a un contenedor que se esta ejecutando:
* docker exec -it alwaysup bach


El sieguiente comando nos devuelve el pid del proceso pricipal del contenedor.
* docker inspect --format '{{.State.Pid}}' alwaysup

## Exponiendo contenedores

Cada contenedor tiene su propia interfaz de red virtual.

Para exporner un prueto del contendor a nuestra maquina usamos el siguiente comando.
* docker run -name proxy -p pruesto_anfitrion:puerto_contenedor
* docker run --name proxy -p 8080:80 -d


Para poder seguir los log del cotenedor podemos ejecutar:
* docker logs -- tail 10 -f

# Dato en docker
## Bind mounts

Persistir la data en nuestra maquina y no en en el contenedor.

* docker run -d --name db -v /Users/mac/Documents/DEV/dev-ops/docker/mongo/data:/data/db mongo

Uno de los riesgos es que tiene acceso a nuestros disco.

## Volúmenes
Forma más estandar de manjar datos con docker.

Los volúmenes son el mecanismo preferido para conservar los datos generados y utilizados por los contenedores de Docker.

Mostrar todos los vólumenes
* docker volume ls

Crear un nuevo volumen
* docker volume create dbdata

Montar un volumen en un docker container
* docker run -d --name db --mount src=dbdata,dst=/data/db mongo


## Insertar y extraer archivos de un contenedor
Para poder copiar un archivo desde el host a nuetro contenedor.

* docker cp file_name container_name:/path/file_name
* docker cp test.txt copytest:/testing/prueba.txt

Para extraer un archivo desde el contenedor a nuestro host
* docker cp name_container:/path path_host
* docker cp copytest:/testing/ localtesting

No es necesario que el contenedor no esta corriendo para extraer los archivos.

# Conceptos fundamentales de Docker: imágenes
Imagenes es la forma en que docker intenta solucionar os problemas de contrucción y distribuicón de software.

Las imagenes son plantillas a paratir de las cuales docker genera contenedores.

Es solo una pieza de software que contiene lo necesario para que un contenedor se peude ejecutar exitosamente.

Se podria comparar como una clase en POO.


Listar las imagenes 
* docker image ls 

el *tag* es la version de la imagen.

Descargar una imagen desde docker hub
* docker pull ubuntu:20.04


## Construyendo una imagen propia
Para construir una imagen nos basamos en un archivo llamado Dockerfile.

```Docker
FROM ubuntu:latest
RUN touch /usr/src/hola-platzi.txt
```


* docker pull
* docker push

Crear una imagen apartir de un Dockerfile
* docker build -t ubuntu:btaj .
Cambiar el tag para poder publicar nuestras propias imagenes
* dcoker tag ubuntu:btaj bautistaj/ubuntu:btaj

## El sistema de capas

Revisar las capas de una imagen

* docker history ubuntu


Una imagen ocupa espacion dependinedo de las capas agregadas.

Si agegamos y removemos archivos el peso aunmenta ya que cada capa es inmutable.


# Usando Docker para desarrollar aplicaciones

La configuración de Dockerfile es muy importante, esto para aprovechar todos los beneficios que docker nos ofrece.

Para el siguiente caso que es para un aplicación de Node.

Los archivos principales  para el manejo de las dependencias son:
* package.json
* package-lock.json

Por esta razón son las mirameras en mover al contenedor y posteriormente hacer el install de node.

El siguienete paso es mover los archivos de nuestra app, en este caso docker.

```docker
FROM node:12

COPY ["package.json","package-lock.json", "/usr/src/"]

WORKDIR /usr/src

RUN npm install

COPY [".", "/usr/src/"]

EXPOSE 3000

CMD ["npx","nodemon", "index.js"]
```

Ahora bien, necesitamos que nuestra app refleje los cambios de la app sin la necesidad de hacer el build.
Paa ello vamos a realizar un bind-mount de los archivos que implican nustro app. Que para el caso es index.js
* docker run --rm -p 3000:3000 -v /Users/mac/docker/index.js:/usr/src/index.js platziapp



## Docker networking: colaboración entre contenedores

Listar las redes de red:
* docker network ls

bridge: retrocompatibilida
host: para que el contenedor tenga acceso a las redes de la maquina host.
none: deshbilitar la networking.

Crear red en docker.
* docker network create --attachable platzinet
--atachable permite que otros contenedores se conecte a ella.

Inspeccionar las redes.
* docker network inspect platzinet

Vamos a crear un nuevo contenedor con mongo
* docker run -d --name db mongo

Ahora conectar el contendor anterior a nuestra red
* docker network connect platzinet db

Es turno de levantar una app para que se conecte a nuestra base de datos.
* docker run -d --name app -p 3000:3000 --env MONGO_URL=mongodb://db:27017/test platziapp

Si dos contenedores estan connectados a una misma red estas se pueden encontrar entre si con el nombre del contendor.

Ahora solo resta conectar el contendor anterior a la red
* docker network connect platzinet app


## Docker Compose

Todo lo anterio se puede realizar utilizando docker-compose
```docker
version: "3.8"

services:
  app:
    image: platziapp
    environment:
      MONGO_URL: "mongodb://db:27017/test"
    depends_on:
      - db
    ports:
      - "3000:3000"

  db:
    image: mongo
```

## Comandos

Ver la red que crea docer compose
* docker network inspect docker_default

Ver los servicios de docker compose
* docker-compose ps

Ver los logs de los servicios
* docker-compose logs -f app

Ejecutar un compnado
* docker-compose exec app bash

Bajar los servicios 
* docker-compose down


## Docker Compose como herramienta de desarrollo

```docker
version: "3.8"

services:
  app:
    build: .
    environment:
      MONGO_URL: "mongodb://db:27017/test"
    depends_on:
      - db
    ports:
      - "3000:3000"
    volumes:
      - .:/usr/src
      - /usr/src/node_modules
    command: npx nodemon index.js

  db:
    image: mongo
```


## Compose en equipo: override

El archivo docker-compose.override.yml nos ayuda a sibreescribir el archivo original lo cuál no ayuda en el desarrollo.

Archivo docker-compose.yml
```docker
version: "3.8"

services:
  app:
    build: .
    environment:
      MONGO_URL: "mongodb://db:27017/test"
    depends_on:
      - db
    ports:
      - "3000:3000"
    volumes:
      - .:/usr/src
      - /usr/src/node_modules
    command: npx nodemon index.js

  db:
    image: mongo
```

Archivo docker-compose.overrideyml
```docker
version: "3.8"

services:
  app:
    build: .
    volumes:
      - .:/usr/src
      - /usr/src/node_modules
    command: npx nodemon index.js
```

NOTA: *Se recominda manejar los puertos en un solo archivo.*


Podemos agregar un rango de puertos para poder escalar las aplicaciones.

```docker
ports:
      - "3000-3001:3000"
```

Para lavantar más de un servicio de un contenedor:
* docker-compose up -d --scale app=2


## Administrando tu ambiente de Docker

Eliminar los contenedores 
* docker container prune

Borra todos los contenedores que estén corriendo o apagados
* docker rm -f $(docker ps -aq)

Lista todos los volumes
* docker volume ls 

Borra todo lo que no se esté usando
* docker system prune

Limitar los recurso de nustros contenedores
* docker run --name app --memory 1G platziapp

Ver los estatus de los contenedores
* docker stats

## Deteniendo contenedores correctamente: SHELL vs. EXEC
sigterm 
sigkill

Ver los últimos procesos
* docker ps -l
* 
Si vemos el estatus de algún contenedor tiene un código de salida mayor a 128, la salida se produjo por un exception.


Construyo la imagen
* docker build -t loop.

Corro el contenedor
* docker run -d --name looper loop.

Le envía la señal SIGTERM al contenedor, y si no se puede detener manda SIGKILL
* docker stop looper

Muestra el ps del último proceso
* docker ps -l

Le envía la señal SIGKILL al contenedor
* docker kill looper

Ver los procesos del contenedor
* docker exec looper ps -ef


*NOTA*

*SHELL*
Deja como proeceso principal al shell y no así el comando que nosotros estamos ejecutando

*EXEC*
Deja como proeceso principal el comando que nosotros estamos ejecutando



## Contenedores ejecutables: ENTRYPOINT vs CMD

El ENTRYPOINT de un contenedor es el comando que se va a correr y va a utilizar lo que diga comando como parametro del 
ENTRYPOINT

```docker
FROM ubuntu:trusty

ENTRYPOINT ["/bin/ping", "-c", "3"]

CMD ["localhost"]
```

## El contexto de build
Docker va a montar en un filesystem temporal todo los archivos disponibles en la ruta que se le pasa como parametro, "Que le build puede utilizar"


Para evitar que no se copien archivos como node_modules al contenedor debemos utilizar .dockerignore

Ejemplo .dockerignore
```docker
*.log
.git
.gitignore
build/*
Dockerfile
npm-debug.logs
README.md
node_modules
docker-compose
```

## Multi-stage build
```docker

# Define una fase llamada builder
FROM node:12 as builder

# copiar los archivos necesario para las dependecnias
COPY ["package.json", "package-lock.json", "/usr/src/"]

WORKDIR /usr/src

# Se intalan las dependencias de producción esto para aprovechar las capas
RUN npm install --only=production

COPY [".", "/usr/src/"]

# instalación dependencias de desarrollo
RUN npm install --only=development

# Ejecutar los test
RUN npm run test
## Esta imagen esta creada solo para pasar los tests.

# Productive image
FROM node:12

COPY ["package.json", "package-lock.json", "/usr/src/"]

WORKDIR /usr/src
# instar las dependencias de PRO
RUN npm install --only=production

# Copiar  el fichero de la imagen anterior.
# De cada stage se reutilizan las capas que son iguales.
COPY --from=builder ["/usr/src/index.js", "/usr/src/"]
# Pone accesible el puerto
EXPOSE 3000

CMD ["node", "index.js"]
### En tiempo de build en caso de que algún paso falle, el build se detendrá por completo.
```

## Docker-in-Docker

* docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock docker:19.03.12
* docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock -v $(wich docker):/bin/docker wagoodman/dive:latest prodapp

















