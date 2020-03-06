# Curso de PWA con ReactJS

#### ¿Qué es una PWA?

¿Cómo es la web hoy?
* No funciona muy bien
* Malas conexiones
* La UX no solamente es el diseño de nuestra app.

Importancia
* 50% de usuarios abandonan sitio en 3 segundos
* cada segundo cuesta entre 5-10%


**PWA es un Estándar de calidad en nuestras aplicaciones**.

Palabras claves:
* Performance
* Instalable Homescreen
* Dar soporte Offline


#### Progressive Web App vs. Native App

Depende de las funcionalidades que necesitemos.

#### proyecto

#### Google Lighthouse

Permite hacer diagnostico de performance de nuestra app.
Notas
* Lighthose no sustituye pruebas con dispositivos reales.
* Diagnostico First meaningful Paint y First interactive:
    * First meaningful Paint: tiempo que tarda en renderizar la primera pantalla debe de pasar de 1 y 2
    * First to intercative: Cuando ya se cargo React y podemos interactuar con la app.

Para bajar los tiempos se debe de utilizar Server rendering (First meaningful Paint)

Depende del framework que estamos utilizando (First intercative), este tiene que ser de almenos de 5 segundos.

#### Creando un Web Manifest
* short_name: Es el nombre que se utiliza en la Homescreen.
* name: Es el nombre de nuestra aplicación.
* icons: Especifica un array de imágenes que servirán como iconos de la aplicación. Cambiaremos el “favicon.ico” por “icon.png”, especificamos el tamaño a 512x512 y el tipo a “image/png”.
* start_url: Nos indica en que página comienza nuestra aplicación, por compatibilidad siempre conviene que sea “/” en lugar de “./index.html”.
* display: Define el modo de visualización para la aplicación. Standalone significa que la aplicación puede correr por si misma.
* theme_color: Define qué color vamos a usar en la barra de tareas de Android para que combine con nuestra aplicación.
* related_applications: Sirve si queremos que Chrome en el Add to Homescreen recomiende una aplicación del Store.

~~~json
{
  "short_name": "Recetas",
  "name": "Platzi Recetas",
  "icons": [
    {
      "src": "/icon.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ],
  "start_url": "/",
  "scope": "/",
  "display": "standalone",
  "theme_color": "#ffa500",
  "background_color": "#ffffff",
  "related_applications": [],
  "prefer_related_applications": false
}
~~~


## Servir Worker
#### ¿Qué es un Service Worker?
* Soporte Offlien
* Proxy in browser

Es una de las características más importantes de las PWA, es lo que hace las las PWA funcionen, es un script que se ejecuta detrás de un navegador y esto no puede tocar a nuestro DOM.
Se puede tener control absoluto a nivel de red de nuestra aplicación.

#### Introducción a workbox

* Los service Workers solo funcionan en producción.
* Limpiar la información del sitio.
* No conviene escribir nuestros services workers debido a la complejidad del manejo del cache.
* react-app-rewired: para evitar hacer [eject](https://medium.com/curated-by-versett/dont-eject-your-create-react-app-b123c5247741) se va utilizar  react-app-rewired
* config-overrides.js: Sobre escribir configuraciones
* precacheAndRoute: archivos js los va aguardad en background
* Cambiar react-scripts por react-app-rewired

**Buena práctica es limpiar la cache del navegador**

#### Implementando Workbox
Estrategias de carga con Workbox

* workbox toma una lista de assets para precargarlos y si la ruta coincide exactamente con un asset entonces lo tomara de cache.
* registerNavigationRoute: se encarga de hacer el funcionamiento de un service worker y sino encuentra una url se dirige a index para que se encargue de mostrar
* Estrategias de carga:
  *  Network Only: se encarga de checar si hay internet, si hay hace la petición de lo contrario se rompe la aplicación, útil para cuando manejamos datos en tiempo real.
  * Network First: hace petición y si no hay red toma datos en cache, utilizar  cuando se quiere la última versión y tener soporte en cache.

#### Aplicando Estrategias de Carga
* Cache First: Busca recursos en cache, si no están estos recursos, entonces hace petición y guarda recurso y muestra datos, utilizar en caso de recursos estáticos tales como imágenes o fuentes.
* Stale While Revalidate: va a cache y a red al mismo tiempo y la que llegue más rápido lo muestra, en este caso siempre van a ser datos en cache, una vez que concluye la petición sustituye el recurso.

Si se requiere un regla por defecto, esta debe de escribirse hasta el final del archivo.

#### Google Analytics Offline

* Para la implementación vamos a configurar react-ga: plugin el cual permite correr google analytics en React.
* Cambiar BrowserRouter por router común para poder extender a los métodos de Router
* Desactivar AdBlocker para desarrollo para no bloquear Google Analytics.
* Workbox ya cuenta con con método para Google Análytics de forma Offline, captura todas las peticiones realizadas con react-ga, y cuando se retome la conexión a internet se enviaran las peticiones.

## Fucnionalidades Avanzadas
#### Web Share API
Nos permite usar un share nativo del sistema operativo.

Web Share API solo funciona con HTTPS y para android

#### Trabajando Offline

Para saber si estamos offline utilizamos **Navigator.onLine**, este siempre marca online cuando no estemos offline lo que significa es que si tenemos una mala conexión va a marcar como offline.

Lo mas correcto es utilizar window, "offline" y "online".

#### Notificaciones

Permisos para las notificaciones:
* Estado por defecto: No sabemos si debemos enviar notificaciones por lo que debemos preguntar al usuario.
* Granted: El usuario a concedido enviarle permisos.
* Denieded: el usuario deniega mandarle permisos.

Identificar si nuestro navegador puede mandar notificaciones.

* Validar si hay notificaciones y serviceWorker para poder enviar la notificaciones.
* Validar permisos de lo contraio solicitarlo.

#### Notas

#### ¿Cuándo usar Network Only?
Por defecto si no queremos cache o manejamos información en tiempo real.
**Network First** es otra estrategia de carga, se encarga mandar la petición a internet, si la conexión a internet esta caída entonces tomara la información que tenga almacenada en cache.

#### ¿Cuándo usar Network First?
Cuando queremos la última versión de un asset y tener soporte offline.

**Cache First**: es una estrategia de carga que lo primero que hace es ir al cache y si encuentra el recurso lo sirve directamente. En caso de no encontrarlo va a ir a red, guardar la información en cache y servir esa versión.

Esta estrategia puede ser peligrosa y solo es recomendable cuando queremos máxima velocidad y estamos manejando un recurso que nunca cambia, como una imagen o alguna fuente.

**Stale While Revalidate**: esta es una estrategia de carga muy particular y que mejor funciona a la hora de mejorar el rendimiento. Lo que hace es ir a cache y a red al mismo tiempo, toma la versión más rápida que siempre será la de cache y en cuanto recibe la de red va a actualizar la versión de cache.

Es recomendable esta estrategia cuando queremos mucha velocidad y estamos manejando un recurso que puede estar levemente desactualizado.