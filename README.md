# FraterChrist

**Red social cristiana de código abierto para la comunión, el aprendizaje bíblico y la colaboración entre hermanos.**

> Marcos 16:15 — «Id por todo el mundo y predicad el evangelio a toda criatura».

FraterChrist es un proyecto personal de aprendizaje y colaboración. **Todavía está en etapa de planificación; la aplicación no es funcional.**

## Primer objetivo: un Feed pequeño

El MVP empezará con publicaciones y respuestas en conversaciones. La meta es construirlo por incrementos y demostrar cada avance con código, pruebas y documentación reproducible.

## Stack previsto

| Área | Tecnología |
|---|---|
| Backend y API | Python + FastAPI |
| Datos | PostgreSQL + SQLAlchemy + Alembic |
| Interfaz | React + TypeScript + Vite |
| Calidad | pytest, Ruff, Vitest y GitHub Actions |
| Desarrollo local | Docker Compose para PostgreSQL |

La arquitectura inicial será un monolito modular. Se evitarán servicios y dependencias adicionales hasta que exista una necesidad real.

## Cómo avanzar

El trabajo se organiza en [GitHub Issues](https://github.com/IsaacToDv/FraterChrist/issues): cada reto tiene un objetivo, criterios de aceptación y evidencia esperada. Trabaja en un Issue principal a la vez; revisa las dependencias y enlaza el Issue con su Pull Request.

- [Plan de aprendizaje e Issues](docs/PLAN-APRENDIZAJE.md)
- [Arquitectura y stack](docs/ARQUITECTURA.md)
- [Requisitos](docs/REQUISITOS.md)
- [Mapa de competencias y evidencias](docs/MAPA-CV-EVIDENCIAS.md)
- [Guía para la demo](docs/GUIA-DEMO.md)
- [Uso responsable de IA](docs/USO-RESPONSABLE-DE-IA.md)
- [Cómo contribuir](CONTRIBUTING.md)

## Estado actual

- [ ] MVP ejecutable
- [x] Documentación inicial y backlog de aprendizaje preparados

Las funciones descritas en la documentación son objetivos, no funciones ya implementadas.

## Licencia

GNU General Public License v3.0 — consulta [LICENSE](LICENSE).
