# Requisitos del MVP

**Estado:** alcance acordado para la primera versión; pendiente de implementación.

## Objetivo

Crear un Feed web donde se puedan leer publicaciones visibles, publicar texto, fotos o videos y responder en hilos, aplicando los permisos en el servidor.

## Funcionalidades incluidas

1. Registro, inicio y cierre de sesión.
2. Lectura de publicaciones públicas sin cuenta.
3. Publicaciones de texto, fotos y videos.
4. Respuestas dentro de un hilo.
5. Selección de visibilidad por publicación.
6. Persistencia en PostgreSQL y almacenamiento independiente de archivos.
7. Interfaz React conectada a una API REST.
8. Pruebas automatizadas y guía para ejecutar el MVP.

## Visibilidad

- **Pública:** cualquiera puede leerla.
- **Limitada a miembros:** solo usuarios autenticados pueden leerla.
- **Privada:** solo el autor puede leerla.

En la primera versión, las respuestas y los archivos adjuntos heredan la visibilidad de la publicación raíz. La API es la autoridad para decidir el acceso; ocultar contenido en React no es un control de seguridad.

La visibilidad limitada a seguidores, grupos específicos o listas de invitados no forma parte del MVP.

## Criterios de aceptación

- Un visitante puede leer publicaciones públicas, pero no las limitadas o privadas.
- Una persona autenticada puede crear publicaciones y elegir su visibilidad.
- Solo el autor puede leer una publicación privada.
- Las respuestas se muestran dentro del hilo correcto y respetan su visibilidad.
- Las fotos y los videos se pueden subir y mostrar sin permitir acceso no autorizado al archivo.
- Los datos y archivos inválidos se rechazan de forma controlada.
- Las pruebas cubren la autenticación y los permisos.
- Otra persona puede levantar el proyecto siguiendo la documentación.

## Fuera del MVP

Perfiles avanzados, seguidores, likes, mensajes directos, búsqueda avanzada, recomendaciones, mesas de oración o estudio, videollamadas, pizarras, juegos educativos, dashboards y despliegue de producción.

El orden de trabajo se mantiene en las [Issues #20–#27](https://github.com/IsaacToDv/FraterChrist/issues).
