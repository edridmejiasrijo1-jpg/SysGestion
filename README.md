# SysGestion

Sistema de gestión administrativa para pequeñas y medianas empresas: inventario, clientes y ventas en una sola interfaz.

**Versión actual:** `v0.1.0` · **Estado:** análisis y diseño completados, implementación pendiente · **Proyecto académico:** Ingeniería de Software I, UAPA

## Objetivo

Centralizar el control del inventario, de los clientes y de las ventas de un negocio mediante una aplicación web sencilla, con una interfaz clara y datos siempre disponibles para quien administra.

## Problema que resuelve

Muchos negocios pequeños llevan sus registros en cuadernos o en hojas de cálculo dispersas. Eso genera datos duplicados, errores de stock, ventas sin respaldo y dificultad para saber cómo va el negocio. SysGestion propone reunir esa información en un solo sistema, con acceso por roles y reportes de apoyo para la toma de decisiones.

## Funcionalidades principales

- Inicio y cierre de sesión con usuario y contraseña.
- Panel principal (dashboard) con resumen de la actividad del negocio.
- Gestión de inventario: registrar, consultar, editar y eliminar productos.
- Registro de ventas, con procesamiento de pago mediante un servicio externo.
- Gestión de clientes.
- Reportes de ventas e inventario.
- Administración de usuarios y roles (administrador y usuario).

## Arquitectura seleccionada

Arquitectura **cliente-servidor en capas**, con el frontend separado del backend:

```
Usuario --> Navegador (Frontend) --HTTPS / JSON--> API REST (Backend) --> Base de datos
```

Se eligió porque permite que un equipo pequeño trabaje en paralelo en la interfaz y en la lógica, facilita las pruebas de cada parte por separado y deja abierta la posibilidad de agregar otros clientes (por ejemplo, una app móvil) sin cambiar el backend. El detalle está en [`docs/arquitectura.md`](docs/arquitectura.md).

## Organización del sistema: frontend y backend

| Parte | Responsabilidad | Tecnología propuesta |
|---|---|---|
| **Frontend** | Mostrar la interfaz, validar los datos básicos de los formularios, guardar la sesión del usuario y consumir la API. No contiene reglas de negocio ni accede a la base de datos. | HTML, CSS y JavaScript (React) |
| **Backend** | Autenticar y autorizar por rol, aplicar las reglas de negocio (stock, totales de venta), validar los datos recibidos, acceder a la base de datos y conectarse con el servicio de pagos. | Node.js con Express |
| **Base de datos** | Guardar de forma persistente usuarios, productos, clientes y ventas. | PostgreSQL |

**Cómo se comunican.** El frontend envía peticiones HTTPS a la API REST del backend y recibe respuestas en formato JSON. Tras iniciar sesión, el backend entrega un token (JWT) que el frontend adjunta en la cabecera `Authorization` de cada petición. Por ejemplo, al registrar una venta:

1. El usuario completa el formulario de venta en el frontend.
2. El frontend valida los campos y envía `POST /api/ventas` con el token.
3. El backend comprueba el token y el rol, verifica el stock y calcula el total.
4. El backend guarda la venta en la base de datos y solicita el pago al servicio externo.
5. El backend responde con un JSON con el resultado y un código HTTP (`201` si se creó, `400` o `409` si hubo un error).
6. El frontend muestra la confirmación o el mensaje de error al usuario.

Los endpoints previstos se describen en [`docs/arquitectura.md`](docs/arquitectura.md).

## Herramientas utilizadas

| Herramienta | Uso |
|---|---|
| Git y GitHub | Control de versiones y repositorio del proyecto |
| GitHub Projects | Tablero Kanban para el seguimiento del avance |
| GitHub Issues | Registro de incidencias, riesgos, mejoras y tareas pendientes |
| Visual Paradigm Online | Modelado UML (diagrama de casos de uso) |
| Markdown | Documentación técnica del repositorio |

## Estado actual del proyecto

| Área | Estado |
|---|---|
| Requisitos | Completado ([`docs/requisitos.md`](docs/requisitos.md)) |
| Modelos UML | Completado: diagrama de casos de uso ([`docs/uml`](docs/uml)) |
| Arquitectura | Completado ([`docs/arquitectura.md`](docs/arquitectura.md)) |
| Gestión del avance | Completado: tablero e issues ([`docs/gestion`](docs/gestion)) |
| Documentación principal | Completado: README, changelog y nota de versión |
| Modelado de base de datos | En progreso |
| Diseño de la interfaz principal | En revisión (pendiente de validación del cliente) |
| Autenticación, inventario y reportes | Pendiente de implementación |

## Estructura del repositorio

```
SysGestion/
├── README.md
├── CHANGELOG.md
├── RELEASE_NOTES.md
├── .gitignore
└── docs/
    ├── requisitos.md
    ├── arquitectura.md
    ├── uml/
    │   └── casos-de-uso.png
    └── gestion/
        └── seguimiento.md
```

## Control de versiones

- La rama `main` guarda siempre la versión estable.
- Cada cambio se trabaja en una rama propia (`docs/...`, `feature/...`, `fix/...`) y se integra a `main` al terminar.
- Los commits siguen el formato `tipo: descripción corta` (`docs`, `feat`, `fix`, `chore`).
- Las versiones usan numeración `vMAYOR.MENOR.PARCHE` y se marcan con una etiqueta (tag). La versión actual es `v0.1.0`.
- Los cambios de cada versión se registran en [`CHANGELOG.md`](CHANGELOG.md) y se resumen en [`RELEASE_NOTES.md`](RELEASE_NOTES.md).

## Seguimiento y autoría

El avance se sigue en el tablero de **GitHub Projects** y en la pestaña **Issues**. Autor: Edrid Mejías Rijo · Universidad Abierta para Adultos (UAPA) · Ingeniería de Software I.
