# Requisitos — FraterChrist Core Feed

**Estado:** especificación propuesta. Un requisito se considera cumplido solo cuando hay código funcional y evidencia de verificación.

## Alcance

Aplicación web con cuentas, publicaciones de texto, feed cronológico, visibilidad pública/privada y respuestas directas. React consume una API REST. No se manejan archivos multimedia en esta fase.

## Requisitos funcionales

| ID | Requisito | Criterio de aceptación |
|---|---|---|
| RF-01 | Registro | Una persona puede crear una cuenta; los datos inválidos se rechazan con errores claros. |
| RF-02 | Sesión | Un usuario puede iniciar, consultar y cerrar sesión. Django gestiona las contraseñas. |
| RF-03 | Crear publicación | Una persona autenticada publica texto no vacío de hasta 5.000 caracteres y elige público o privado. |
| RF-04 | Feed | El feed lista solo publicaciones raíz visibles, ordenadas de más reciente a más antigua. |
| RF-05 | Visibilidad | Cualquiera puede leer publicaciones públicas; solo el autor puede leer sus publicaciones privadas. |
| RF-06 | Respuestas | Un usuario autenticado responde a una raíz visible. No se permiten respuestas anidadas. |
| RF-07 | Visibilidad del hilo | Las respuestas heredan la visibilidad de la raíz. |
| RF-08 | Edición y eliminación | Solo el autor puede editar o eliminar su propia publicación o respuesta. |
| RF-09 | Interfaz | La web permite registro, inicio de sesión, lectura del feed, publicación y respuestas mediante la API. |
| RF-10 | Estados de interfaz | Se muestran estados de carga, lista vacía, validación y error. |

## Requisitos no funcionales

| ID | Requisito | Criterio de aceptación |
|---|---|---|
| RNF-01 | Seguridad | La autorización se aplica en el backend para cada endpoint; ocultar elementos en React no cuenta como protección. |
| RNF-02 | CSRF | Las solicitudes que modifican datos usan sesiones de Django y protección CSRF. |
| RNF-03 | Secretos | No se suben credenciales, tokens o claves; la configuración sensible se suministra mediante variables de entorno. |
| RNF-04 | Integridad | Relaciones, campos obligatorios y reglas de visibilidad se validan en el backend y el modelo de datos. |
| RNF-05 | Mantenibilidad | Backend organizado en un monolito modular, sin microservicios innecesarios. |
| RNF-06 | Pruebas | Los flujos principales y los permisos tienen pruebas automatizadas reproducibles. |
| RNF-07 | Instalación | Otra persona puede configurar la base de datos, aplicar migraciones, ejecutar la app y correr las pruebas siguiendo la guía. |
| RNF-08 | Usabilidad | La interfaz es legible, usable con controles estándar y adaptable a pantallas comunes; no requiere diseño avanzado. |
| RNF-09 | Límites | El feed usa paginación básica y las publicaciones tienen una longitud máxima definida. |
| RNF-10 | Documentación | README, diagramas y código distinguen claramente lo planificado de lo implementado. |

## Reglas de visibilidad

- **Pública (public):** lectura anónima y autenticada.
- **Privada (private):** lectura exclusiva del autor.
- Crear, responder, editar y eliminar requiere autenticación.
- Las respuestas apuntan directamente a la publicación raíz y heredan sus permisos.
- Listados, detalles y respuestas deben comprobarse en el servidor.

## Fuera del Core

Fotos, videos, archivos adjuntos, acceso protegido a archivos, visibilidad para miembros, perfiles avanzados, likes, seguidores, búsqueda avanzada, mensajes directos, videollamadas, salas, pizarras y juegos.

## Definition of Done

Una tarea solo se cierra cuando el código existe, se puede ejecutar, satisface sus criterios de aceptación, sus pruebas relevantes pasan y la documentación coincide con el comportamiento real.
