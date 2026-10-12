# Registro de cambios

Todos los cambios relevantes del proyecto se registran en este archivo. El formato sigue la guía [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/) y el versionado usa `vMAYOR.MENOR.PARCHE`.

## [0.1.0] - 2026-10-12

Versión inicial controlada: análisis y diseño del sistema.

### Añadido

1. **Repositorio y estructura base.** Se creó el repositorio con la estructura de carpetas y el archivo `.gitignore` (issue #6).
2. **Tablero Kanban.** Se configuró GitHub Projects con cinco columnas (Backlog, Por hacer, En progreso, En revisión y Finalizado) y seis tarjetas iniciales (issue #9).
3. **Requisitos.** Se documentaron los requisitos funcionales y no funcionales en `docs/requisitos.md`.
4. **Modelo de casos de uso.** Se elaboró el diagrama de casos de uso en `docs/uml/`.
5. **Arquitectura.** Se definió la arquitectura cliente-servidor en capas, con la separación entre frontend y backend, en `docs/arquitectura.md`.

### Cambiado

- **Ajuste en el modelo de casos de uso.** Se incorporó «Procesar pago» como caso de uso incluido en «Registrar venta», con el sistema de pagos como actor externo.
- **Reorganización de la documentación.** Los documentos técnicos pasaron a la carpeta `docs/` y el `README.md` se reescribió con objetivo, funcionalidades, arquitectura, herramientas y estado.

### Pendiente

Véase [`RELEASE_NOTES.md`](RELEASE_NOTES.md).
