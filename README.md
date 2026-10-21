# FraterChrist

**Una red social cristiana de código abierto para la comunión, el aprendizaje bíblico y la colaboración.**

FraterChrist busca reunir conversaciones, recursos y proyectos de la comunidad cristiana en un mismo lugar. Es un proyecto personal de aprendizaje; está en desarrollo y todavía no es una aplicación funcional.

## Módulos

- **Feed:** publicaciones y conversaciones por hilos.
- **Zona doctrinal:** preguntas, respuestas, bosquejos y recursos.
- **Mesa:** devocionales, estudios bíblicos, ideas, programación y videojuegos.
- **Kit:** Biblia, cuaderno y herramientas.
- **Notificaciones:** correos de edificación y newsletters voluntarios.

## Primer objetivo: un MVP pequeño

El primer prototipo estará en `MVP/` cuando comience su implementación. Empezará por el [**Feed**](#Módulos)
y servirá para demostrar conocimientos de **Python, TypeScript, APIs REST, SQL y PostgreSQL** mediante una funcionalidad real, pruebas y documentación.

**Estado actual:** documentación preparada. El directorio `MVP/` y la aplicación aún no existen en la rama `main`.

## Stack elegido para el MVP

| Parte | Tecnología |
|---|---|
| Backend y API | Python + FastAPI |
| Base de datos | PostgreSQL |
| Acceso a datos y migraciones | SQLAlchemy + Alembic |
| Interfaz web | React + TypeScript + Vite |
| Calidad | pytest, Ruff, Vitest y GitHub Actions |
| Entorno local | Docker Compose para PostgreSQL |

Este stack permite tener una API clara, una interfaz sencilla y una base de datos relacional sin dividir el proyecto en microservicios.

## Prioridades técnicas

- Código fácil de leer y modificar.
- Validación de datos y permisos en el backend.
- Pruebas para los casos importantes y los errores.
- Feed paginado y consultas SQL revisadas; los índices se añadirán cuando los patrones de consulta los justifiquen.
- Secretos fuera del repositorio en .gitignore.
- Sin cachés, colas ni servicios adicionales hasta que se valide el MVP o se manifieste una necesidad viable.

## Aprendizaje y documentación

- [Plan de aprendizaje](docs/PLAN-APRENDIZAJE.md)
- [Arquitectura y stack](docs/ARQUITECTURA.md)
- [Requisitos](docs/REQUISITOS.md)
- [Competencias y evidencias](docs/MAPA-CV-EVIDENCIAS.md)
- [Guía para la demo](docs/GUIA-DEMO.md)
- [Uso responsable de IA](docs/USO-RESPONSABLE-DE-IA.md)
- [Cómo contribuir](CONTRIBUTING.md)

Cada etapa terminada debe dejar una evidencia que se pueda revisar y ejecutar.

## Licencia

GNU General Public License v3.0 — consulta [LICENSE](LICENSE).
