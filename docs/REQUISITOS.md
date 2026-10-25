# Requisitos del MVP

**Estado:** alcance acordado para la primera versión; pendiente de implementación.

## Objetivo

Construir un Feed web donde las personas puedan leer publicaciones visibles, crear publicaciones de texto, fotos o videos y responder en hilos, con reglas de privacidad aplicadas en el servidor.

## Funcionalidades incluidas

1. Registro, inicio y cierre de sesión.
2. Lectura pública del Feed sin necesidad de una cuenta.
3. Publicación de texto, fotos y videos.
4. Respuestas dentro de un hilo.
5. Selección de visibilidad al crear una publicación.
6. Persistencia en PostgreSQL y almacenamiento separado para los archivos.
7. Interfaz web conectada a una API REST.
8. Pruebas automatizadas y una guía reproducible de instalación.

## Niveles de visibilidad

- **Pública:** cualquiera puede verla.
- **Limitada a miembros:** solo usuarios autenticados pueden verla.
- **Privada:** solo la ve su autor.

Para el MVP, las respuestas y los medios heredan el nivel de acceso de la publicación raíz. El frontend no es responsable de hacer cumplir estos permisos: la API debe rechazar lecturas no autorizadas incluso si se solicita directamente la URL del recurso.

La visibilidad limitada a seguidores, grupos específicos o listas de invitados no forma parte del MVP porque requiere relaciones y controles adicionales.

## Criterios de aceptación del MVP

- Un visitante sin cuenta puede leer publicaciones públicas, pero no las limitadas o privadas.
- Un usuario autenticado puede crear una publicación y elegir su visibilidad.
- Solo el autor puede leer una publicación privada.
- Las respuestas pertenecen al hilo correcto y respetan su visibilidad.
- Fotos y videos se pueden subir y mostrar; sus archivos no son accesibles saltándose la autorización.
- Las entradas y archivos no válidos se rechazan de forma controlada.
- Las pruebas automatizadas cubren autenticación y permisos.
- El proyecto puede ejecutarse siguiendo las instrucciones documentadas.

## Fuera de alcance

Perfiles avanzados, seguidores, likes, mensajes directos, búsqueda avanzada, recomendaciones, mesas de oración o estudio, videollamadas, pizarras, juegos educativos, dashboards y despliegue de producción.

Consulta las [Issues del MVP](https://github.com/IsaacToDv/FraterChrist/issues) para ver el orden de implementación.