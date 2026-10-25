# Arquitectura del MVP

**Estado:** diseño propuesto; todavía no hay una aplicación implementada.

## Decisión

- **Backend:** Python, Django y Django REST Framework.
- **Frontend:** React, TypeScript y Vite.
- **Base de datos:** PostgreSQL.
- **Medios:** archivos privados fuera de PostgreSQL; la base conserva metadatos.
- **Arquitectura:** monolito modular, no microservicios.

## Módulos iniciales

- **Accounts:** registro, sesión y autenticación.
- **Feed:** publicaciones, listado cronológico e hilos.
- **Permissions:** reglas de visibilidad aplicadas en el servidor.
- **Media:** carga, validación y entrega de fotos y videos protegidos.

Los módulos comparten una base PostgreSQL durante el MVP. La lógica de un módulo no debe depender de detalles internos de los demás más allá de contratos claros.

## Visibilidad

| Nivel | Acceso |
|---|---|
| \`public\` | Cualquier persona, incluso sin iniciar sesión. |
| \`members\` | Solo usuarios autenticados. |
| \`private\` | Solo el autor. |

En esta primera versión las respuestas y los adjuntos heredan la visibilidad de la publicación raíz. Los permisos deben aplicarse en la API al listar, recuperar y servir medios; ocultar elementos en React no es un control de seguridad.

## Modelo inicial

- **User:** identidad de la cuenta.
- **Post:** autor, contenido, visibilidad, fecha y referencia opcional a una publicación padre.
- **MediaAsset:** tipo de medio, clave de almacenamiento, MIME, tamaño y publicación asociada.

Una publicación puede contener texto, uno o varios adjuntos, o ambos según las reglas de validación. Los binarios no se guardan en PostgreSQL.

## Flujo multimedia

En desarrollo, utilizar almacenamiento local privado y un endpoint que verifique permisos antes de entregar el archivo. Validar tipo, tamaño y nombre; no confiar solo en la extensión proporcionada por el cliente. Más adelante, la interfaz de almacenamiento podrá usar un servicio compatible con S3.

El MVP no requiere transcodificación, CDN, streaming adaptativo, colas ni un servidor de video en directo. Se evaluarán cuando las necesidades del producto lo justifiquen.

## Roadmap posterior

Perfiles avanzados, seguidores, mesas comunitarias y salas de voz/video, pizarras y juegos educativos se mantienen fuera del MVP. Se pueden integrar luego como módulos independientes dentro del mismo monolito y separar solo si existe una necesidad demostrable.

El diagrama de componentes y el modelo UML visibles en el [README](../README.md#arquitectura) representan esta propuesta.