# Arquitectura de SysGestion

## Estilo seleccionado

Arquitectura **cliente-servidor en capas**, con tres capas bien separadas:

| Capa | Componente | Función |
|---|---|---|
| Presentación | Frontend web | Interfaz del usuario y consumo de la API |
| Lógica de negocio | Backend (API REST) | Autenticación, reglas de negocio, validación y acceso a datos |
| Datos | Base de datos relacional | Almacenamiento persistente |

```
Usuario --> Navegador (Frontend) --HTTPS / JSON--> API REST (Backend) --> Base de datos
                                                          |
                                                          +--> Servicio de pagos (externo)
```

## Por qué se eligió

- Un equipo pequeño puede trabajar en paralelo en la interfaz y en la lógica.
- Cada capa se puede probar por separado.
- Se pueden agregar otros clientes (por ejemplo, una app móvil) sin cambiar el backend.
- Es una estructura sencilla de explicar, mantener y desplegar.

## Responsabilidades

**Frontend:** mostrar pantallas, validar datos básicos de los formularios, guardar la sesión y llamar a la API. No contiene reglas de negocio ni accede a la base de datos.

**Backend:** autenticar y autorizar por rol, aplicar las reglas de negocio (stock y totales de venta), validar los datos recibidos, acceder a la base de datos y conectarse con el servicio de pagos.

## Comunicación

- Protocolo: HTTPS.
- Formato: JSON.
- Autenticación: token (JWT) enviado en la cabecera `Authorization: Bearer <token>`.
- Errores: códigos HTTP (`400` datos inválidos, `401` sin sesión, `403` sin permiso, `409` conflicto de stock).

## Endpoints previstos

| Método | Ruta | Uso |
|---|---|---|
| `POST` | `/api/auth/login` | Iniciar sesión |
| `GET` | `/api/productos` | Listar productos |
| `POST` | `/api/productos` | Crear producto |
| `POST` | `/api/ventas` | Registrar venta |
| `GET` | `/api/clientes` | Listar clientes |
| `GET` | `/api/reportes/ventas` | Datos del reporte de ventas |
