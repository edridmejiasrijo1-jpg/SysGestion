# Requisitos de SysGestion

## Requisitos funcionales

| ID | Requisito | Prioridad |
|---|---|---|
| RF-01 | El sistema permitirá iniciar y cerrar sesión con usuario y contraseña. | Alta |
| RF-02 | El sistema permitirá al administrador gestionar usuarios y asignarles un rol. | Media |
| RF-03 | El sistema permitirá registrar, consultar, editar y eliminar productos del inventario. | Alta |
| RF-04 | El sistema permitirá registrar ventas y descontar el stock de los productos vendidos. | Alta |
| RF-05 | El sistema procesará el pago de cada venta mediante un servicio externo. | Media |
| RF-06 | El sistema permitirá registrar y consultar clientes. | Media |
| RF-07 | El sistema generará reportes de ventas e inventario. | Media |
| RF-08 | El sistema mostrará un panel principal con el resumen de la actividad del negocio. | Alta |

## Requisitos no funcionales

| ID | Requisito | Categoría |
|---|---|---|
| RNF-01 | La interfaz será clara e intuitiva y usará colores con contraste suficiente para su lectura. | Usabilidad |
| RNF-02 | Las contraseñas se guardarán cifradas, la comunicación usará HTTPS y el acceso dependerá del rol. | Seguridad |
| RNF-03 | Las consultas habituales deberán responder en menos de 3 segundos en condiciones normales (meta de diseño). | Rendimiento |
| RNF-04 | El frontend y el backend estarán separados y la API tendrá documentación. | Mantenibilidad |
| RNF-05 | La aplicación funcionará en los navegadores modernos y se adaptará a pantallas pequeñas. | Compatibilidad |
