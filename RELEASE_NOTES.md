# Nota técnica de versión: v0.1.0

**Fecha:** 12/10/2026 · **Tipo:** versión inicial controlada (análisis y diseño)

## Contenido de la versión

- `README.md` actualizado: objetivo, problema, funcionalidades, arquitectura, organización frontend/backend, herramientas y estado.
- `docs/requisitos.md`: 8 requisitos funcionales y 5 no funcionales.
- `docs/uml/casos-de-uso.png`: diagrama de casos de uso con dos actores internos y un sistema de pagos externo.
- `docs/arquitectura.md`: arquitectura cliente-servidor en capas.
- `docs/gestion/seguimiento.md`: estado del tablero y de los issues de seguimiento.
- `CHANGELOG.md` con el registro de cambios.

Esta versión **no incluye código de la aplicación**: documenta lo necesario para iniciar la implementación con una base clara.

## Cambios controlados

Se controlaron cinco cambios mediante Git (ramas, commits con formato `tipo: descripción` y la etiqueta `v0.1.0`): creación del repositorio, configuración del tablero, documentación de requisitos, modelo de casos de uso (con el ajuste de «Procesar pago») y definición de la arquitectura. El detalle está en `CHANGELOG.md`.

## Aspectos pendientes

- Implementar el backend (API REST) y el frontend.
- Terminar el modelo de base de datos (en progreso).
- Corregir la validación del formulario de inicio de sesión del prototipo (#12).
- Agregar el filtro de productos por categoría en el inventario (#15).
- Revisar el contraste de colores del dashboard (#18).
- Definir la estructura final de la tabla de reportes (#20).
- Obtener la validación del cliente sobre el flujo de navegación del dashboard.

## Próximo paso técnico

Crear la estructura base del backend con el endpoint `POST /api/auth/login` y el esquema inicial de la base de datos, en la rama `feature/autenticacion`, enlazando los commits con el issue #12. Esto dará lugar a la versión `v0.2.0`.
