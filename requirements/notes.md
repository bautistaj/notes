**Sistema Gestor de Exámenes para Laboratorios Clínicos**

Nombre descriptivo del proyecto
Aplicación web para la gestión de exámenes para laboratorios clínicos y sistemas médicos.

Descripción del proyecto a nivel funcional (requerimientos):
Esta aplicación cuenta con diferentes tipos de usuario y de acuerdo al rol permitirá realizar acciones que se verán reflejadas y directamente relacionadas con el flujo de trabajo de los demás tipos de usuario.

Según el tipo de usuario, las funcionalidades son:

**Paciente:**

El paciente puede visualizar en una tabla de manera gráfica la información sobre sus últimos exámenes clínicos realizados con fecha y la opción para verlos en línea.

El paciente puede descargar los resultados en formato PDF de manera individual o seleccionar varios y descargarlos en un mismo documento juntos.

Si los resultados de los exámenes aún no están disponibles, debe salirle el nombre de los exámenes que se ha realizado y están a la espera de resultados con un ícono inactivo de descarga y un mensaje que indique la no disponibilidad del resultado.

**Médico**

Este perfil es quien asigna los exámenes que un paciente se debe realizar y los asocia en el sistema.

El médico debe tener una vista principal donde puede buscar un paciente por su número de documento y visualizar su información de contacto principal y su historia clínica. En esta vista puede asociar exámenes clínicos a realizarse el paciente, para esto debe contar con una ventana que le permita seleccionar de una lista precargada los diferentes exámenes clínicos posibles y agregarlos uno a uno al paciente.

En el momento que el médico asocia exámenes clínicos a un paciente, el perfil de paciente ya debe poder visualizar estos exámenes en su vista principal aún si aún no están los resultados.

Si el paciente tiene su sesión abierta en el momento en que los exámenes se están asociando, debe recibir una notificación en tiempo real para recargar su vista y poder visualizarlos.

**Bacteriólogo**

El profesional de la salud cuenta con una interfaz gráfica que le permita buscar a un paciente a través de su número de identificación y abrir una ventana que le permita ingresar los resultados a los exámenes asociados al paciente seleccionado.

Una vez ingresados los resultados, deben estar inmediatamente disponibles para su descarga desde el lado del paciente.

Si el paciente tiene su sesión abierta en el momento en que los resultados de los exámenes están disponibles, debe recibir una notificación en tiempo real para recargar su vista y poder descargar sus resultados.

**Administrador**

Este perfil lo tendrá personal administrativo que podrá acceder a la información de todos los demás roles y podrá administrarlos (agregar nuevos, editar existentes y eliminarlos) a través de una vista principal tipo tabla donde podrá seleccionar el tipo de perfil que desea cargar y realizar búsquedas por identificación y nombre.

Es el único perfil que puede crear nuevos bacteriólogos, médicos y pacientes; incluso puede crear otros administradores y realizar las mismas acciones para todos.

Debe poder cargar información en grupos con una opción para leer archivos en formato .csv que guarde directamente la información de cualquier perfil, generando de manera automática usuario y contraseña para cada registro que será correspondiente a un nuevo usuario en el sistema.

Cuando se crea un nuevo usuario, debe llegar un correo electrónico a su cuenta con un mensaje de bienvenida y sus credenciales de acceso al sistema.

**Requerimientos generales**
Al crear un nuevo usuario, independientemente del perfil se debe proveer de manera obligatoria identificación numérica, nombre, apellido, correo electrónico y número de contacto, a partir de esta información se generará de forma automática un nombre de usuario con la estructura: nombre.apellido.ultimos4numerosdeidentificación. Por ejemplo: María Jaramillo con cédula 1234567 su usuario sería maria.jaramillo.4567.

Cada vez que se genere un nuevo nombre de usuario se debe validar que no exista otro igual, en caso de existir, se asignan los últimos dígitos de manera aleatoria y se conservan las dos primeras partes.

La contraseña debe estar cifrada y no puede generarse a partir de información personal del usuario.

El inicio de sesión debe ser el mismo para todos los usuarios e internamente se identificará el perfil al que corresponde y se cargará su información.

El acceso al sistema se debe realizar a través de la página web del laboratorio clínico que tendrá implícito el formulario de login.

Ningún usuario debe poder registrarse en ningún rol, todos deben estar creados desde el perfil del administrador pues no es un laboratorio público y por seguridad no todas las personas deben tener acceso a su sistema.

**Documentación requerida**
Organización del equipo (roles, actividades individuales).

Mockups del proyecto en web y móvil (si aplica), y de cada feature detallado.

Explicación escrita detallada de cada feature.

Diagrama de entidad relación del flujo de base de datos.

**Manual de uso para administradores.**

Toda la documentación anterior debe estar en inglés.

Elementos de seguimiento y planeación
Repositorio desde la etapa inicial del proyecto con toda la documentación de planeación.

Tablero kanban en el repositorio de GitHub, con las tareas y responsables asignados, configurado con tiempos de entrega por cada tarea y estado actual en tiempo real.

Readme del proyecto con el estado actual de la aplicación, actualizado hasta el cambio más reciente y en inglés.

Requerimientos técnicos para frontend
Estructura de maquetación debe ser 100% responsive.

El CSS debe ser implementado por un preprocesador y usar una metodología CSS.

Debe contar cumplir con todos los requerimientos de accesibilidad web.

Todos los elementos del frontend deben contar con pruebas unitarias y un average mínimo de 70%.

La maquetación no debe ser desarrollada bajo ningún framework prediseñado.

La estructura de los archivos debe respetar el principio de responsabilidad única.

Debe implementar buenas prácticas en la escritura de código y código limpio.

Se deben implementar mensajes para casos de error incluídos en la interfaz gráfica.

Todo el código debe estar en inglés, incluyendo documentación.

Requerimientos técnicos para backend
Debe implementar un patrón de diseño justificado que sea escalable y optimizado.

Se puede implementar más de una tecnología para backend pero debe justificarse por qué es una mejor opción.

El proyecto de backend debe estar separado al proyecto del frontend.

Cada feature debe contar con su propio test (average mínimo de 70% por feature).

Debe ser un sistema con estructura modular escalable.

La estructura de los archivos debe respetar el principio de responsabilidad única.

Debe implementar buenas prácticas en el código y código limpio (Eso incluye que bajo ninguna circunstancia se debe repetir código funcionalmente igual, no deben haber bloques de código comentados, toda función debe estar debidamente documentada).

Se deben implementar excepciones y códigos de error en caso de fallos desde el backend por cada feature (el frontend sólo debería recibirlos, no procesarlos).

Todo el código debe estar en inglés, incluyendo documentación.

**Requerimientos de base de datos**
Debe registrar un log de errores.

No se debe eliminar información definitivamente.

En caso de bases de datos relacionales, debe contar con todas las llaves primarias y llaves foráneas debidamente documentadas y configuradas.

Los registros deben ser consistentes a registros reales (simulaciones), no se admiten registros como: test, prueba1, probando, etc.

**Debe ser escalable.**

Deben cumplir con buenas prácticas en los nombres y estructuras.

Debe tener documentado su diseño y funcionamiento, en inglés.

**Entrega única final**
Documentación requerida completa al 100%.

Proyecto completo desplegado en un ambiente de producción.

Sustentación oral del proyecto a nivel estructural y técnico.

