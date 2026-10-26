# Arquitectura del MVP personal

**Estado:** propuesta de diseño; la aplicación todavía no está implementada.

## Stack previsto

- **Backend:** Python, Django y Django REST Framework.
- **Frontend:** React, TypeScript y Vite.
- **Base de datos:** PostgreSQL.
- **Archivos:** almacenamiento local privado durante el desarrollo.
- **Arquitectura:** monolito modular; sin microservicios para el MVP.

## Estructura prevista

~~~text
backend/
├── manage.py
├── config/
└── apps/
    ├── accounts/
    ├── feed/
    └── media/

frontend/
└── src/
    ├── app/
    ├── features/
    │   ├── auth/
    │   └── feed/
    └── shared/
~~~

Esta estructura es una guía para la implementación, no una representación de código ya existente.

## Módulos

- **Accounts:** identidad de usuario y autenticación.
- **Feed:** publicaciones, listado cronológico e hilos.
- **Media:** metadatos, validación y acceso protegido a fotos y videos.

Los módulos comparten PostgreSQL. La API decide qué publicaciones y archivos puede consultar cada usuario.

## Modelo de datos previsto

| Modelo | Campos principales | Responsabilidad |
|---|---|---|
| `User` | `id`, `username`, `email`, `password`, `date_joined` | Cuenta. Django almacena un hash de contraseña en `password`. |
| `Post` | `id`, `author`, `content`, `visibility`, `parent_post`, `created_at`, `updated_at` | Publicación raíz o respuesta directa a una raíz. |
| `MediaFile` | `id`, `post`, `file`, `file_type`, `content_type`, `file_size`, `created_at` | Referencia y metadatos de una foto o video. |

El modelo de usuario debe definirse antes de crear la primera migración. El campo `parent_post` será opcional: vacío en publicaciones raíz y apuntando a la raíz en las respuestas. Las respuestas anidadas no forman parte del MVP.

Los binarios se almacenan fuera de PostgreSQL. `MediaFile.file` guarda la referencia al almacenamiento, y la base de datos conserva los metadatos.

## Reglas de visibilidad

| Valor | Acceso |
|---|---|
| `public` | Cualquier visitante. |
| `members` | Usuarios autenticados. |
| `private` | Solo el autor. |

En esta versión, las respuestas y sus archivos heredan la visibilidad de la publicación raíz. Cada consulta de publicaciones, respuestas o archivos debe verificar los permisos en el servidor.

## Flujo de archivos

1. La API autentica al usuario y valida el tipo y tamaño.
2. El archivo se guarda en almacenamiento privado.
3. PostgreSQL guarda el modelo `MediaFile` y su referencia.
4. Al leer el archivo, la API comprueba los permisos de la publicación asociada.

No se implementarán transcodificación, CDN, videollamadas ni procesamiento distribuido en el MVP.

## Alcance futuro

Perfiles avanzados, seguidores, mesas comunitarias, salas de voz o video, pizarras y juegos educativos quedan fuera de este repositorio personal. Podrán estudiarse en una etapa distinta sin anticipar complejidad en el MVP.

El diagrama de componentes y el UML del dominio se muestran en el [README](../README.md#arquitectura).
