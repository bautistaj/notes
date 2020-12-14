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

