# Requisitos del MVP personal

**Estado:** alcance propuesto; pendiente de implementación.

## Objetivo

Construir un feed web que permita publicar texto, fotos o videos y responder a publicaciones, aplicando permisos de acceso verificables en el backend.

## Funcionalidades incluidas

1. Registro e inicio de sesión.
2. Lectura de publicaciones públicas sin cuenta.
3. Creación de publicaciones con texto, fotos o videos.
4. Respuestas directas a publicaciones raíz.
5. Selección de visibilidad por publicación.
6. PostgreSQL para datos y almacenamiento separado para archivos.
7. Interfaz React conectada a una API REST.
8. Pruebas automatizadas e instrucciones para ejecutar el proyecto.

## Visibilidad

- **Pública:** cualquier persona puede leerla.
- **Limitada a miembros:** solo usuarios autenticados pueden leerla.
- **Privada:** solo el autor puede leerla.

Las respuestas y los adjuntos heredan la visibilidad de la publicación raíz. Ocultar contenido en React no es una medida de seguridad: la API debe rechazar el acceso no autorizado incluso cuando se solicite directamente una ruta o archivo.

## Criterios de aceptación

- Un visitante puede consultar publicaciones públicas, pero no las limitadas o privadas.
- Un usuario autenticado puede crear publicaciones y elegir su visibilidad.
- Solo el autor puede consultar una publicación privada.
- Las respuestas se muestran dentro del hilo correcto y respetan su visibilidad.
- Los archivos multimedia se pueden cargar y mostrar sin saltarse los permisos.
- Los archivos inválidos o demasiado grandes se rechazan.
- Las pruebas cubren la autenticación, la visibilidad y el acceso a medios.
- El proyecto se puede ejecutar siguiendo las instrucciones del repositorio.

## Fuera del MVP personal

Perfiles avanzados, seguidores, likes, mensajes directos, búsqueda avanzada, recomendaciones, mesas de oración o estudio, videollamadas, pizarras, juegos educativos, dashboards y despliegue de producción.

El orden de implementación está en las [Issues #20–#27](https://github.com/IsaacToDv/FraterChrist/issues).
