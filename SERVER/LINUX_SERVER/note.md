# Administradores de servidores

#### Comandos 
* clear: Limpiar pantalla
* ls: Listar contenido de directorio
* ls -l: listado en formato largo 
* ls -la: listado todos los archivos "incluyendo archivos ocultos" en formato largo 
* pwd: print work directory
* ~: Indica que estamos en el home
* touch: Crear nombre de archivos
* cp: copiar archivos/directorios.
* mkdir: male directory, crea directorios
* cd: change directory
* cd ..: Regresar al directorio padre
* cd -: Regresar al directorio inmediato anterior
* **d**rwxr-xr-x indica que es un directorio
* **-**rwxr-xr-x indica que es un archivos
* mv: mover un directorio que también nos sirve para cambiar nombre de directorio.
* rm: remove
* rm -r: Remove de forma recursiva
* touch: modifica la fecha de creación
* 

#### Diferencias entre LESS, CAT, HEAD y TAIL

Comandos para leer archivos.
* cat: concatenar archivos, no recomendable para archivos grandes.
* less: mostrar contenido de un archivos de forma paginado.
* tail: solo muestra las ultimas 10 lineas del archivos.
* tail -f: solo muestra las primeras lineas pero se mantiene y muestra todos los cambios
* head: muestra las primeras 10 lineas del archivo.

#### Integración con archivos y permisos
~~~bash
drwxr-xr-x   2 root root 4096 Feb 19 01:17 bin
drwxr-xr-x   2 root root 4096 Apr 24  2018 boot
~~~
Los primeros 0 caracteres excluyendo el primero nos muestran los permisos que se tienen en el archivo.

~~~
r lectura
w escritura
x ejecución

rwx-rwx-rwx
* Primer grupo es para el usuario propietario del archivo
* Segundo grupo es para el grupo al que pertenece el usuario
* Tercer grupo es para otros usuarios.
~~~

#### comandos 
* chmod: change owner
Este comando se puede utilizar con letras **ugoa** donde u: usuario propietario, g: grupo, o: otros usuarios y a: todos.

Para agregar el permiso de ejecuón al usuario ejecutamos
~~~
chmod u+x file.txt
~~~

Para el siguiente comando se agrega el permiso de ejeción para todos los usuarios
~~~
chmod +x file.txt
~~~

Hay otra forma de asignar permisos y es utilizando el formato **Octal** [1-7]
~~~
chmod 755 file.txt
~~~
Los permisos quedarían de la siguiente manera:
~~~
rwxr-xr-x
~~~

Para cambiar el propietario se utiliza **chown** change owner
~~~
chown root: file.txt
~~~

#### Conociendo las terminales linux

Terminales de uno a 6 **tty1-tty6** la 7 es para ambientes gráficos.

Comandos para el cambio de terminal.

~~~
Ctrl+Alt+Fx
~~~

Comando **chvt**
~~~
sudo chvt 3
~~~

* w: Cantidad de usuarios en el sistema
* who: para identificar quién esta en sesión.
* tty: terminal a la cual estoy conectado.
* ps: proceso del sistema operativo
* ps -ft tty1: identificar la terminal tyy1
* tyy: muestra la terminal que estas usando.
* kill: matar un proceso utilizando el process id **PID**

Matar las terminales abiertas.

#### Manejo y monitoreo de procesos y recursos del sistema

Tarea importante verificar procesos que se estan ejecutando en el SO.


* ps: proces status
* ps aux: 
* | : se utiliza para enlazar comandos-
* grep: busca en cadenas texto.
* ctrl+z: Si se tiene un editor abierto es posible detener el proceso con este comando.
* jobs: mostrar los procesos
* fg: for ground, regresar al proceso que se paro.
* &: ejecuta en background
* nohup: Ejecuta el proceso per creara una salida llamada nohup.out en donde se encuentra lo que ejecuta el proceso.

#### Monitoreo de recursos del sistema

Monitoreo de CPU, Memoria, HHD.

* top: Muestra información específica del sistema operativo.
* cat /proc/cpuinfo | grep "Processor" para incluir mayusculas y minúsculas en la búsqueda incluimos **-i**
* free: muestra el estado de la memoria.
* free -h: Formato para humanos.
* du: disk usage, Muestra información del disco duro.
* du -hsc path: nos muestra el peso del directorio/archivo.
* du -sm * : Muestra los archivos mas pesados.
* du -hs * | sort -nr | head -5
* ps auxf | sort -nr -k 3 | head -d: Listar los procesos que consumen más CPU **-k 3**.
* ps auxf | sort -nr -k 4 | head -d: Listar los procesos que consumen más RAM **-k 4**.

## Instalación y manejo de software.

#### Análisis de los parámetros de red

* Ip publica:

* Ip privada: solo se tiene acceso en mi propia red.

* ifconfig: configuración de la interfaz, se listan las tarjetas y direccionamientos.

* ip a: ip adress show, muestra la información de la red.

* ip -4 a: muestra las tarjetas que utilizan ipv 4.

* ip -6 a: muestra las tarjetas que utilizan ipv 6.

* hostname: muestra el nombre de host.

* route -n: muestra el gateway.

* nslookup: nslookup nombre de dominio, nos muestra toda información de red del dominio.

* curl: hace peticiones.

* wget: obtener información de internet y descarga de archivos.


#### Administración de paquetes acorde a la distribución.

* Red hat
  * .rpm
  * Repositorios yum

* Debian/Ubuntu
  * .deb
  * dpkg-reconfigure
  * repositorios apt

**Red Hat Package Management**
* Base de datos RPM almacenada en /var/lib/rpm
* rpm -qa: Listar todos los rpm instalados en la máquina.
* rpm -i package.rpm: instalar paquete
* rpm -e package.rpm: Remover paquete del sistema.

Comando yum 

* yum install package

**Debian package Management**
* Base de datos DPKG localizada en /var/dpkg
* dpkg -l: Lstar todos los debs instalados en la máquina.
* dpkg -i package.deb: Intalar paquete
* dpkg -r package.deb: Remover paquete.
* dpkg-reconfigure package: reconfigurar paquetes instalados.
* apt install package

#### Manejo de paquetes en sistemas basados en Debian

Todo lo que tiene que ver con actualizaciones se debe de tener permisos root.

* apt dist-upgrade: Modifica Kernel, live bash.
* apt search "mysql$"
* apt-cache search "mysql$"
* dpkg -l
* snap search aws: snap es el nuevo gestor de paquetes.
* snap install canonical-livepatch: instalamos este software para poder actualizar le kernel sin la necesidad de reiniciar


#### Administración de software con YUM y RPM para CentOS

* rpm -qa: muestra todos los paquetes instalados 
* rpm -qi bash: Mostrar la información del paquete bash.
*  rpm -qc bash: muestra todos los archivos que se contemplan en la configuración de bash.

* yum update: actualizar repositorios.

#### Nagios: Desempaquetado, descompresión, compilación e intalación de paquetes.
 * sudo apt install build-essential libgd-dev openssl libssl-dev unzip apache2 php gcc libdbi-perl libdbd-mysql-perl
 * sudo make all: ejecuta todos los archivos configurados
 * sudo male install
 * .tar: Empaquetado
 * .gz: comprimido

## Administración de usuarios
#### Los usuarios una tarea vital en proceso de administración.
comandos
* id: muestra id y grupo de usuario en sesión, debian inicia la creación desde 1000 en Centos desde 500 el usuario 0 es de root
* whoami: Quien soy yo :)
* /etc/passwd: Muestra información de usuario.
* /root:/bash : home
* etc/shadow: Contraseñas sombra

passwd root para activar el usuario.

#### Creando y manejando cuentas de usuarios.

* useradd bob: agregar usuarios, en este caso no tiene password, se debe configurar, no crea un home
* adduser bina: En est caso pide password, crea un home 
* userdel bina: Elimina nombre de usuario
* hitory: muestra el histórico de comandos ejecutados.
* !23 : En este caso ejecuta el comando 23.
* usermode: Modificar usuario.

**Nunca modificar el el archivo passwd con editor de texto.**

#### Entendiendo la membresía de los grupos

Comandos
* su: swith user
* sudo su - nodejs
* groups nodejs: Verificamos los grupos de nodejs, por defecto se asigna a mismo grupo nodejs.
* sudo gpasswd -a nodejs sudo: Agregamos al usuario nodejs al grupo sudo.
* gpasswd -d nodejs sudo: Eliminamos del grupo al usuarios nodejs
* usermod -aG sudo nodejs: comando para agreagr al grupo sudo
* groups nodejs: nos muestra el grupo al que pertenece el usuario.
* sudo -l: muestra los permisos del archivo sudores.

#### Usando PAM para el control de acceso de usuarios.

* /etc/pam.d/ : Carpeta Configuración
* /lib64/security/ : Carperta de Librerías
* /etc/security : Cambios de configuración.

* pwscore: Centos validar contraseña.
* ulimit: Listar permisos de usuaris
* ulimit -u 10: Solo tendra 20 procesos
* #!/bin/bash: Encabezado de archivo para script.
* etc/security/time.conf: Como configurar los usarios para que se logean en un horario predeterminado.
* sudo vi /etc/security/time.conf
* grupo wheel: grupo para ejecutar como sudo.

## Servicios en el sistema operativo.

#### Autenticción de clientes y servidores sobre SSH