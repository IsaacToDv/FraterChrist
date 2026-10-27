# Registro de progreso y aprendizaje

Este archivo documenta el desarrollo real del Core Feed. Separa el trabajo realizado de la planificación y no afirma que una función exista sin evidencia.

## 2026-10-27 — Delimitación del Core Feed

**Tipo:** planificación y documentación; no es una funcionalidad implementada.

**Objetivo:** definir un MVP terminable y demostrable que cubra análisis, modelado, API REST, autenticación, permisos, frontend y calidad.

**Decisiones:**
- El Core incluye registro/sesión, publicaciones de texto, feed cronológico, visibilidad pública/privada y respuestas directas.
- El modelo se reduce a usuario Django y publicación con relación opcional a una raíz.
- Las respuestas no pueden anidarse y heredan la visibilidad de la raíz.
- La interfaz será mínima; la autorización pertenece al backend.
- Fotos, videos y visibilidad para miembros se posponen a una fase de expansión.
- El trabajo se ordena en las issues #20–#27; #20 es el punto de partida.

**Estado verificable:** alcance, requisitos, arquitectura, diagramas y backlog documentados. La aplicación aún no está implementada.

---

## Plantilla para la próxima sesión

### AAAA-MM-DD — Título breve

- **Issue / objetivo:**
- **Qué hice:**
- **Qué aprendí:**
- **Problema encontrado:**
- **Cómo lo resolví:**
- **Verificación:** pruebas, comandos, capturas, commit o enlace.
- **Pendiente / siguiente paso:**
