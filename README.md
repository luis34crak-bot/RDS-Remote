# RDS-Remote

Configuración de RemoteApp, RD Web Access, IIS y RADIUS

Práctica de laboratorio de la asignatura Seguridad de Redes (ITLA), enfocada en la publicación de aplicaciones remotas usando Remote Desktop Services (RDS) sobre Windows Server, un sitio web propio alojado en IIS, y la autenticación de un router contra un servidor RADIUS mediante AAA.

Índice


Descripción
Entorno y requisitos
Tecnologías configuradas
Flujo de la práctica
Comandos de verificación (RADIUS/AAA)
Evidencias
Contenido del repositorio
Autor


Descripción

Este repositorio contiene la documentación y evidencias de la Asignación 3, cuyo objetivo fue integrar varios servicios de Windows Server para permitir el acceso remoto a aplicaciones publicadas a través de un navegador, además de reforzar el acceso a un router mediante autenticación centralizada con RADIUS.

El laboratorio se dividió en dos grandes bloques:


Publicación de aplicaciones remotas: instalación de IIS, configuración de Remote Desktop Services (RDS), publicación de un navegador como aplicación RemoteApp y acceso a través del portal RD Web Access.
Autenticación centralizada (AAA/RADIUS): configuración de un router para autenticar el acceso mediante un servidor RADIUS, dejando además un usuario local como respaldo.


Entorno y requisitos


Windows Server (con los roles de IIS y Remote Desktop Services).
Un router con soporte para AAA (Cisco IOS/IOSv).
Un servidor/proceso RADIUS accesible desde el router.
Navegador web para las pruebas de acceso.
Dirección IP del servidor usada en las pruebas: 192.168.1.10.


Tecnologías configuradas


IIS (Internet Information Services) — alojamiento de una página web propia (index.html), usada como aplicación de prueba.
Remote Desktop Services (RDS) — instalación mediante el asistente Quick Start, que dejó configurados automáticamente:

RD Connection Broker
RD Web Access
RD Session Host



RemoteApp — publicación de un navegador web como aplicación remota, disponible desde el cliente sin necesidad de una sesión de escritorio completa.
RD Web Access — portal web (/RDWeb) desde donde el usuario final accede a las aplicaciones publicadas.
RADIUS (AAA) — autenticación, autorización y registro (logging) del acceso a un router mediante un servidor RADIUS.


Flujo de la práctica


Instalación del rol de IIS y creación de una página web básica en C:\inetpub\wwwroot.
Verificación del sitio desde el navegador (http://192.168.1.10).
Instalación de Remote Desktop Services mediante el asistente Quick Start.
Publicación del navegador como aplicación RemoteApp desde Server Manager:

Acceso a Server Manager.
Ingreso a Remote Desktop Services.
Selección de la colección creada.
Publicación del navegador como aplicación remota.



Acceso al portal RD Web (https://192.168.1.10/RDWeb) con el usuario .\Administrator.
Ejecución de la aplicación remota (navegador) y validación de que el sitio en IIS carga correctamente a través de RemoteApp.
Configuración de RADIUS en el router:

Creación de un usuario local en el router, como acceso de respaldo.
Configuración de AAA para que la autenticación se realice contra el servidor RADIUS.
Definición de una contraseña para el modo de configuración del equipo.
Habilitación de los registros de autenticación, autorización y RADIUS para poder monitorear el proceso.





Comandos de verificación (RADIUS/AAA)

Comandos usados en el router para depurar y confirmar el correcto funcionamiento de la autenticación RADIUS:

debug aaa authentication
debug aaa authorization
debug radius
show aaa servers
show aaa sessions


debug aaa authentication / debug aaa authorization — muestran en tiempo real el proceso de autenticación y autorización del usuario contra el servidor RADIUS.
debug radius — despliega el intercambio de paquetes RADIUS entre el router y el servidor.
show aaa servers — permite confirmar el estado del servidor RADIUS configurado (activo/inactivo, estadísticas de solicitudes).
show aaa sessions — lista las sesiones activas autenticadas mediante AAA.


Evidencias

El documento (.docx) incluye capturas de pantalla de:


Página web funcionando en IIS.
Acceso al portal RD Web.
Aplicaciones RemoteApp publicadas.
Ejecución de la aplicación remota.


Contenido del repositorio


LuisHanel_2024-0784_A3_parafraseado.docx — informe completo de la práctica, con introducción, desarrollo por cada servicio configurado (IIS, RDS, RemoteApp, RD Web Access, RADIUS), conclusión y evidencias.
README.md — este archivo, con el resumen y la guía de la práctica.


Autor

Luis Hanel Nuñez Perez — Matrícula 20241200
Materia: Seguridad de Redes
Instructor: Jonathan Rondon
Instituto Tecnológico de las Américas (ITLA)
