# Requisitos iniciales de FraterChrist

**Estado:** borrador de planificación; se refinará mediante implementación y pruebas.

## Objetivo
Construir una red social cristiana de código abierto para conversación, aprendizaje bíblico y colaboración, mientras se demuestran competencias de backend, API REST, SQL/PostgreSQL, pruebas y seguridad.

## Usuarios previstos
- Miembros que publican y participan en conversaciones.
- Personas que comparten preguntas y recursos doctrinales.
- Participantes de espacios colaborativos.
- Moderadores de la comunidad.

## Requisitos funcionales
| ID | Requisito | Prioridad |
|---|---|---|
| RF-01 | Registro, inicio y cierre de sesión. | Alta, tras la API base |
| RF-02 | Consultar y gestionar perfil básico. | Media |
| RF-03 | Crear y consultar publicaciones. | Alta |
| RF-04 | Responder publicaciones y consultar hilos. | Alta |
| RF-05 | Editar o eliminar contenido propio según reglas. | Alta |
| RF-06 | Preguntas, respuestas, bosquejos y recursos doctrinales. | Media |
| RF-07 | Espacios colaborativos con miembros y permisos. | Media |
| RF-08 | Notas privadas y herramientas bíblicas con licencias compatibles. | Media |
| RF-09 | Correo con consentimiento, preferencias y baja. | Posterior al MVP |
| RF-10 | Reportes, bloqueos y moderación antes de abrir a usuarios. | Alta |

## Requisitos técnicos iniciales
- RT-01: iniciar la aplicación siguiendo instrucciones documentadas.
- RT-02: exponer endpoint de salud y un endpoint de ejemplo documentado.
- RT-03: validar entradas y devolver códigos HTTP coherentes.
- RT-04: automatizar pruebas del comportamiento y casos inválidos.
- RT-05: añadir PostgreSQL y migraciones cuando se implemente persistencia.
- RT-06: ejecutar verificaciones automáticamente mediante CI.
- RT-07: mantener secretos fuera del código versionado.

## Requisitos no funcionales
Seguridad y autorización en servidor; privacidad por defecto; módulos mantenibles; accesibilidad al añadir interfaz; instrucciones portables verificadas; calidad comprobable; priorizar herramientas libres sin asumir que todo alojamiento será gratuito.

## Fuera del alcance inicial
Microservicios, app móvil nativa, ActivityPub, recomendaciones complejas y newsletters sin consentimiento.

## Aceptación
Cada requisito implementado tendrá criterios verificables, pruebas cuando corresponda y enlaces a issues, commits o PR. No se marcará como completado sin evidencia reproducible.