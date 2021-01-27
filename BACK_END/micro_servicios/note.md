# Micro servicios.

Es un enfoque de desarrollo basado en servicios, en vez de tener un monolito se tiene varios servicios independientes.

## Características
* Autónomos
* Expecializados
* Registro y auto-descibrimiento de servicios
* Escalado flexible
* Tolerancia a fallos
* Balanceo de carga
* Configuración centralizada
* Libertad de tecnologia
* Agilidad, equipos más pequeños
* Ciclo de desarrollo más cortos
* Código reutilizable

## Micro servicios
Son un conjunto de componentes pequeños y autónomos que colaboran entre si.

Aplicación monolitica es la que hace todo.

### Características
* Función única
* Independientes: Los servicios no conocen las demas implementaciones.
* Registro y auto-decubrimiento: desacoplado de la app.
* Auto escalado y agilidad.
* Confiabilidad y tolerancia a fallos: Hystrinx eviatr errores en cascada.
* Balanceo de cargas: Districbución de cargas de forma equitatitava: Ribbon.
* Configuración centralizada: Spring cloud config, git.

### Ventajas
* Nueva tecnolía y adopción de procesos.
* Reducción de costo
* Ciclos de liberación más rapidos.
* Equipos de desarrollo más pequeños.

## Implementación de Servicios.
Si tenemos dos servicios que implementan la misma interface lo que podemos hacer es utilizar.
* @Primary: Colocar esta anotación en el servicio pricipal.
* @Qualifier(name = "serviceName")



