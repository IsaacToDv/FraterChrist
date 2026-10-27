# Requisitos — FraterChrist Core Feed

**Estado:** especificación propuesta. Los requisitos no se consideran cumplidos hasta que exista implementación y evidencia de prueba.

## Alcance del Core

Aplicación web con cuentas, publicaciones de texto, feed cronológico, visibilidad pública/privada y respuestas directas. El frontend consume una API REST. No se admiten archivos multimedia en esta fase.

## Requisitos funcionales

| ID | Requisito | Criterio de aceptación |
|---|---|---|
| RF-01 | Registro de usuarios | Una persona puede crear una cuenta con los campos requeridos; los datos inválidos se rechazan con un error claro. |
| RF-02 | Sesión | Un usuario puede iniciar, consultar y cerrar sesión. Las contraseñas se gestionan con el sistema de autenticación de Django. |
| RF-03 | Crear publicación | Una persona autenticada puede publicar texto no vacío, con máximo inicial de 5.000 caracteres, y seleccionar público o privado. |
| RF-04 | Feed cronológico | El feed lista publicaciones raíz visibles, de la más reciente a la más antigua; las respuestas no aparecen como raíces independientes. |
| RF-05 | Lectura por visibilidad | Los visitantes pueden leer publicaciones públicas. Solo el autor puede leer sus publicaciones privadas. |
| RF-06 | Respuestas | Una persona autenticada puede responder a una publicación raíz visible. Las respuestas anidadas no se permiten. |
| RF-07 | Herencia de visibilidad | Una respuesta adopta la visibilidad de su publicación raíz y no puede ampliar quién accede al hilo. |
| RF-08 | Edición y eliminación | Solo el autor puede editar o eliminar su propia publicación o respuesta. |
| RF-09 | Interfaz web | La interfaz permite registrarse, iniciar sesión, leer el feed, crear publicaciones y responder usando la API. |
| RF-10 | Feedback de interfaz | La aplicación muestra estados de carga, lista vacía, validación y error de forma comprensible. |

## Requisitos no funcionales

| ID | Requisito | Criterio de aceptación |
|---|---|---|
| RNF-01 | Seguridad por servidor | Los permisos se aplican en cada endpoint de la API; ocultar elementos en React no se considera control de acceso. |
| RNF-02 | Protección de solicitudes | El MVP usa sesiones de Django y protección CSRF para operaciones que modifican datos. |
| RNF-03 | Contraseñas y secretos | Las contraseñas nunca se almacenan en texto plano. Credenciales y claves se configuran mediante variables de entorno; no se suben secretos al repositorio. |
| RNF-04 | Integridad de datos | Las relaciones, campos obligatorios y reglas de visibilidad se validan en el backend y en el esquema de datos. |
| RNF-05 | Mantenibilidad | El backend se organiza por responsabilidad en un monolito modular; no se introducen microservicios para el Core. |
| RNF-06 | Verificabilidad | Los flujos esenciales, especialmente la privacidad, tienen pruebas automatizadas reproducibles. |
| RNF-07 | Instalación reproducible | Un desarrollador puede preparar la base, aplicar migraciones, arrancar backend/frontend y ejecutar pruebas siguiendo la documentación. |
| RNF-08 | Usabilidad básica | La interfaz es legible, adaptable a pantallas comunes y usable con formularios y controles estándar; no se exige diseño visual avanzado. |
| RNF-09 | Respuestas acotadas | Las operaciones de listado usan paginación básica y límites razonables; el contenido tiene un máximo definido. |
| RNF-10 | Claridad documental | README, diagramas, rutas y código deben distinguir las funciones implementadas de las propuestas. |

## Reglas de visibilidad

- **Pública (`public`):** lectura anónima y autenticada.
- **Privada (`private`):** lectura exclusiva del autor.
- Las operaciones de crear, responder, editar o eliminar requieren autenticación.
- Las respuestas heredan la visibilidad de la publicación raíz.
- El backend debe filtrar listados y comprobar el permiso de lectura al consultar una publicación o sus respuestas.

## Fuera de alcance

Fotos, videos, archivos adjuntos, controles de acceso a multimedia, visibilidad para miembros, perfiles avanzados, likes, seguidores, recomendaciones, búsqueda avanzada, mensajes directos, videollamadas y cualquier funcionalidad comunitaria más amplia.

## Definition of Done

Una funcionalidad solo se marca como terminada cuando:
1. El código existe y puede ejecutarse.
2. Los criterios de aceptación aplicables se verifican.
3. Las pruebas relevantes pasan.
4. La documentación coincide con el comportamiento real.
