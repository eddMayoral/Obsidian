# Actividades realizadas del 15 al 21
## Edgar Mayoral
- Junta Nefropolis USA
- Junta asesoria KPIS
- Protipo documentos atuomaticos  [[Prop-AutoDoc]]
- Junta [[Sesion-Odoo-SegimientoComercializadora]]
- Junta [[Plan de Capacitacion Odoo]]
- Seguimiento capacitacion tecnica
- Borrador gantt NewLetter
- Desarrollo prototipo Webinar [[Prop-Webinar]]
- [[Resumen semanal del 8-14 junio 2022]]

## Diego Trinidad

Nefropolis:  

- Se agrego el Google tag manager al sitio.
-I magen para OGP (En duda si quedará esa o hay que cambiarla)
- Se agrego landing page para la sucursal Lite de León.

  
NefroApp:  

-   Se añadió nuevo componente para los pedidos, nefro-admin/orders con su respectiva tabla (En el readme viene la instalación de la libreria) y los requerimientos necesarios.
-   Se agrego un modal para editar los permisos de administración del sitio.
-   Filtros ordenables en la tienda.

## Juan Sandoval  
Se hizo un pequeño ajuste en la sesión del usuario en el React, lo que permitirá empezar a trabajar con los módulos de los clientes y restringir los módulos del dashboard a admins si cuenta con los privilegios o no.  
  
Ya se pueden crear, editar y/o eliminar administradores desde el módulo correspondiente (nefro-admin/admins). Se cuenta con 5 privilegios básicos, acceso a:  

-   Productos
-   Cupones
-   Clientes
-   Pedidos
-   Administradores

Estos permisos no se han implementado. Se añadirá esta tarea a Asana, que incluye que únicamente [admin@nefropolis.com](mailto:admin@nefropolis.com) (administrador principal) pueda agregar más administradores.  
  
Se implementó la lógica básica para añadir comentarios a productos, lo que permite que usuarios iniciados puedan añadir un comentario (sin imágenes).
