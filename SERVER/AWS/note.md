# AWS

#### ¿Qué es el cómputo en la nube?
* Sitios web
* Respaldos y configuración
* Archivos permanentes
* DevOps
* Análisis masivos
* Computo Serverless: Micorservicios
* Computo de alto rendimiento
* Aplicaciones empresariales: Levantar servicios cada que se utilice
* Internet of Things
* Aplicaciones empresariales
* Distribución de media: Archivos, mecanismos de hacer transcoding
* Servicios móviles
* Cómputo cientifico
* E-commerce
* Ambientes híbridos.
* Blockchain

Ventajas de AWS
* Cero inversión inicial
* Uso lo que necesitas
* Velocidad cuando la necesitas
* Si no lo usas. no lo pagas
* Cobertura mundial.


#### Introducción a la oferta de servicios de AWS y sus aplicaciones

* Sección de computo:
* Storage
* DataBase
* Migrations of services
* Networking & Content
* Developer Tools
* Management Tool
  * Cloud Watch
* Media Service
  * Elastic trasncoder: transmisión streaming
* Machine Leraning
  * Recognition
* Analytics
* Security, Identity & Compliance
  * IAM Administración de usuarios
  * GuardDuty: Registro de actividad para ataques
* Mobile Services
* AR & VR
* Application Integration
* Customer Engagement
* Business Productivity
* Desktop & Apps Streaming
  * Workspace configuración de recursos
* Internet of Things
* Game Development

#### Ejemplo de arquitectura con Elastic Beanstalk
Tiene como ventaja la alta disponibilidad y la eficiencia para atender una gran cantidad de usuarios

#### ¿Qué es EC2?
Maquinas virtuales en linea
* instancias: Maquinas virtuales
* Seguridad: Generación de diferentes llaves
* Espacio: Diversos opciones de espacio en disco, virtualmente infinito
* Redundancia: Tener varias copias de misma máquina.
* Firewall: Configuración desde maquina y los puertos a utilizar.
* Direcciones IP estáticas: Puedes optar comprar una IP pública estática.
* Respaldos: Respaldo de ambientes, sistemas
* Escalables: Incrementar los recursos de la máquina: CPU, RAM
* Migración de snapshot: Puedes copiar snapshot en cualquier región.

#### Creando una isntancia de ECs

#### Conectándonos a nuestra instancia desde Windows

Responsable
* Actualizar software
  * Libertad de instalar lo que se necesite
* Respaldos
* Restauración

Actualizar e instalar emacs
* yum update
* yum emacs 

#### Subiendo un proyecto: Clonando un repositorio de GitHub a nuestra Instancia de EC2
* Instalar git: yum install git
* Clonar proyecto

#### Subiendo un proyecto a nuestra instancia de EC2: Ejecutar nuestro proyecto
Instalar
* pip install flask: pip gestor de dependencias de python
* security groups agregar nueva regla para abrir puerto.

#### ¿Qué es Lambda y Serverless?

¿Qué es lambda?
Lugar donde puedes ejecutar tus funciones de código.
* Serverless: No existe un servidor y solo el código que AWS se encarga de ejecutarlo.
* Lenguajes soportados:
  * Node (Javascript)
  * Python
  * Java 8
  * C#
  * .Net Core
  * Go

  Ventajas:
  * Seguridad
  * Performance
  * Código aislado
  
  1 000 000 de peticiones gratis al año.

  #### Creando una función Lambda

  ## Elastic Beastalk

  #### Conociendo Elastic Beanstalk
  ¿Qué es?
  Es una plataforma donde obtienes un balanceador de cargas y tantas instancias de EC2 como se requieran.
  Puedes escalar de manera dinámica según la respuesta del usuario CPU, RAM
  Soporta:
  * Docker image
  * GO
  * Java SE
  * Java con Tomcat
  * .NET + Windows server + IIS"
  * Node JS
  * Python 
  * Ruby

  #### Creando un ambiente en Elastic Beanstalk
  #### Almacenamiento - S3
  Opciones de almacenamiento
  * S3: Repositorio de archivos para crear y manipular datos.
  * Glacier: Servicio de almacenamiento en la nube para almacenar datos y realizar copias de seguridad a largo plazo.

  #### Almacenamiento - Glacier
  Repositorio de almacenamiento económico pero más lento excelente para cuando requieras guardar archivos históricos.
  Tiempo de respuesta de entre 2 a 15 minutos.

  ## Bases de datos
  #### Bases de Datos - RDS Aurora PG

  Amazon creo un servicio llamado RDS que optimiza el rendimiento de base de datos.
  RDS tiene varias opciones de motores de base de datos:
  * Aurora PG
  * Aurora MySQL, MariaDB, PostgreSQL, Oracle y Microsoft SQL Server

  #### Conociendo RDS PG
  AWS implementa el motor de PostgreSQL (RDS PG)
  * Tareas optimizadas
  * Respaldos frecuentes automatizados
  * Cifrado
  * Migración asistida
  * Alta disponibilidad

  No es posible conectarse a la base de datos hasta que explícitamente lo indiques.

  #### Conociendo Aurora PG (Postgrest)
  Toma el motor de base datos Postgres optimiza el Kernel de lo cual se obtiene un postgrest 3x más rápido.
  * No es gratuito
  * AWS RDS PG es eficiente:
    * Modificaciones del código al mismo motor de la base de datos
    * Instancias de última generación
  * Compatible con PG 9.6.x
  Debido a que tiene un espejo entonces, al ralizar algún cambio este no deja de funcionar.
  Configuración inicial de alta disponibilidad en 3 diferentes zonas.

  #### Mejores prácticas de Bases de Datos y RDS

  * Respaldo diarios
  * Replicar la base de datos.
  
  ## Redes
  #### Redes - Route53
  Uno de los servicios de red más interesantes es Route53
  AWS provee un DNS muy poderos con el cual podras crear subdominios asignados a instancias y lo veras reflejado es segundos.
  Route53 esta disponible en todas las regiones.


  ## Herramientas de administración.
  Estas las herramientas de AWS para la administración
  * IAM: permite contralar los permisos de accesos de todos los usuarios.
  * CloudWatch: Te mostrara diversos eventos que suceden en el entorno, lo cual te va a permitir la centralización de los LOGS.
  * Cloudtrail: Herramienta de auditoría que permite ver quién y que realizó en la cuenta de AWS.

  Estas opciones cuentan con almacenamiento histórico.

#### Utilizando IAM.

#### Cloud Watch
#### Cloudtrail

#### Certificate manager
Dos de los más importantes herramientas de seguridad son:
* Certificate Manager: AWS te permite crear tus certificados o bien importarlos si ya tienes uno.
* GuardDuty: Te permite auditar todos los intentos de conexión a tus instancias.

#### GuardDuty
Sistema de seguridad que permite ver los intentos de acceso a todas las instancias.

## Bonus

#### AWS Rekognition
Deep learning

#### Creando servicio de postgres
#### Accediendo a nustra base de datos de PG