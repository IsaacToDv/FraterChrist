# Arquitectura del MVP

**Estado:** diseño propuesto. La aplicación todavía no está implementada.

## Stack

- **Backend:** Python, Django y Django REST Framework.
- **Frontend:** React, TypeScript y Vite.
- **Datos:** PostgreSQL.
- **Archivos:** almacenamiento local privado durante el desarrollo; diseño preparado para migrar a un servicio compatible con S3.
- **Arquitectura:** monolito modular, sin microservicios para el MVP.

## Aplicaciones Django

- **`accounts`:** identidad de usuario, registro e inicio/cierre de sesión.
- **`feed`:** publicaciones, respuestas e implementación de las reglas de visibilidad.
- **`media`:** metadatos, validación y acceso protegido a fotos y videos.

Las aplicaciones comparten PostgreSQL en el MVP. Los permisos de lectura deben comprobarse desde la API en listados, detalles, respuestas y archivos; no se consideran una responsabilidad exclusiva del frontend.

## Modelo propuesto

| Modelo | Campos principales | Responsabilidad |
|---|---|---|
| `User` | `id`, `username`, `email`, `password`, `date_joined` | Cuenta y autenticación. Django almacena el hash en `password`. |
| `Post` | `id`, `author`, `content`, `visibility`, `parent_post`, `created_at`, `updated_at` | Publicación raíz o respuesta directa a una publicación raíz. |
| `MediaFile` | `id`, `post`, `file`, `file_type`, `content_type`, `file_size`, `created_at` | Referencia a un archivo multimedia y sus metadatos. |

Los nombres son propuestas para los modelos Django, no código ya implementado. El modelo de usuario debe definirse antes de crear la primera migración. Los archivos binarios no se guardarán en PostgreSQL; el campo `file` apunta al almacenamiento.

## Reglas de visibilidad

| Valor | Acceso |
|---|---|
| `public` | Cualquier visitante. |
| `members` | Usuarios autenticados. |
| `private` | Solo el autor. |

En el MVP, una respuesta directa a una publicación raíz y sus adjuntos heredan el nivel de visibilidad de esa publicación. Las respuestas anidadas no forman parte del MVP. Los archivos no pueden servirse mediante una URL estática que evite comprobar los permisos.

## Flujo de archivos

1. La API autentica al usuario y valida el tamaño y tipo de archivo.
2. El archivo se guarda en almacenamiento privado.
3. PostgreSQL conserva el modelo `MediaFile` y su referencia al archivo.
4. En cada lectura, la API comprueba la visibilidad de la publicación antes de servir el archivo.

La primera versión no necesita transcodificación, CDN, streaming adaptativo, colas ni videollamadas. Esos servicios se evaluarán cuando el Feed funcione.

## Fuera del MVP

Perfiles avanzados, seguidores, mesas comunitarias, videollamadas, pizarras y juegos educativos. Se podrán añadir como módulos futuros sin convertir toda la aplicación en microservicios.

Los diagramas de componentes y clases están en el [README](../README.md#arquitectura).
