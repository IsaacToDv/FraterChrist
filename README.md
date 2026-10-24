<h1 align="center">FraterChrist</h1>

<p align="center"><strong>Red social cristiana de código abierto para la comunión, el aprendizaje bíblico y la colaboración.</strong></p>

<p align="center">
  <a href="LICENSE"><img alt="Licencia GPL-3.0" src="https://img.shields.io/badge/Licencia%20GPL-3.0-blue?style=flat-square&logo=gnu&logoColor=white" /></a>
  <img alt="Proyecto en planificación" src="https://img.shields.io/badge/estado-en%20planificaci%C3%B3n-yellow?style=for-the-badge" />
  <img alt="Open source · contribuciones bienvenidas" src="https://img.shields.io/badge/open%20source-contribuciones%20bienvenidas-2ea44f?style=for-the-badge&logo=github&logoColor=white" />
</p>

<blockquote>
  <p align="center"><em>Marcos 16:15 — «Id por todo el mundo y predicad el evangelio a toda criatura».</em></p>
</blockquote>

<p align="center">
  <strong>¿Quieres colaborar?</strong>
  <a href="CONTRIBUTING.md">Lee las pautas</a> ·
  <a href="https://github.com/IsaacToDv/FraterChrist/issues">Explora las tareas</a> ·
  <a href="https://github.com/IsaacToDv/FraterChrist/issues/new">Propón una mejora</a>
</p>

**Estado: en planificación. La aplicación todavía no es ejecutable.** Este repositorio es un proyecto personal de aprendizaje de desarrollo de software y análisis de datos; no es un servicio disponible para usuarios.

<p align="center"><strong>Stack previsto · Fase 1: backend y datos</strong></p>
<p align="center">
  <a href="https://www.python.org/"><img alt="Python" src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" /></a>
  <a href="https://fastapi.tiangolo.com/"><img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" /></a>
  <a href="https://docs.pydantic.dev/"><img alt="Pydantic" src="https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white" /></a>
  <a href="https://www.postgresql.org/"><img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" /></a>
  <a href="https://www.sqlalchemy.org/"><img alt="SQLAlchemy" src="https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white" /></a>
  <a href="https://alembic.sqlalchemy.org/"><img alt="Alembic" src="https://img.shields.io/badge/Alembic-migrations-59666C?style=flat-square" /></a>
</p>

<p align="center"><strong>Calidad, entorno y análisis</strong></p>
<p align="center">
  <a href="https://pytest.org/"><img alt="pytest" src="https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white" /></a>
  <a href="https://docs.astral.sh/ruff/"><img alt="Ruff" src="https://img.shields.io/badge/Ruff-D7FF64?style=flat-square&logo=ruff&logoColor=black" /></a>
  <a href="https://github.com/features/actions"><img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" /></a>
  <a href="https://www.docker.com/"><img alt="Docker Compose" src="https://img.shields.io/badge/Docker%20Compose-2496ED?style=flat-square&logo=docker&logoColor=white" /></a>
  <a href="https://pandas.pydata.org/"><img alt="pandas" src="https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white" /></a>
  <a href="https://faker.readthedocs.io/"><img alt="Faker" src="https://img.shields.io/badge/Faker-datos%20sint%C3%A9ticos-59666C?style=flat-square" /></a>
</p>

<p align="center"><strong>Fase 2 · Interfaz web</strong></p>
<p align="center">
  <a href="https://react.dev/"><img alt="React" src="https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB" /></a>
  <a href="https://www.typescriptlang.org/"><img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" /></a>
  <a href="https://vite.dev/"><img alt="Vite" src="https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white" /></a>
  <a href="https://vitest.dev/"><img alt="Vitest" src="https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white" /></a>
</p>

*Las insignias representan tecnologías previstas; no indican que ya estén implementadas.*

---

## Objetivo del proyecto

Construir un feed pequeño donde usuarios registrados puedan publicar y responder en conversaciones. El proyecto se desarrollará por etapas, priorizando fundamentos, pruebas y resultados reproducibles en lugar de acumular módulos.

## Alcance en dos fases

### Fase 1 — Backend, PostgreSQL y análisis reproducible

La prioridad es construir y entender una base funcional antes de crear una interfaz web.

- Fundamentos de Python aplicados a una publicación: reglas de validación, modelo y pruebas.
- PostgreSQL, SQL, relaciones, índices y migraciones con Alembic.
- API REST con FastAPI y validación con Pydantic.
- MVP de backend: registro e inicio de sesión, crear y consultar publicaciones, responder en un hilo y permisos mínimos.
- Pruebas con pytest, formato y análisis estático con Ruff, e integración continua con GitHub Actions.
- Datos sintéticos para consultas SQL y un análisis acotado con pandas. No se usarán datos personales reales.

**Resultado para cerrar la fase:** una API documentada y probada, base de datos que pueda crearse desde cero con migraciones, feed de publicaciones y respuestas, pruebas automáticas y un análisis reproducible que responda una pregunta concreta.

### Fase 2 — Interfaz web y revisión de seguridad

Comenzará cuando la API y las pruebas de la primera fase sean reproducibles.

- Prototipo y luego interfaz mínima con React, TypeScript y Vite.
- Conexión de la interfaz a la API para leer publicaciones, crear una publicación y responder.
- Pruebas de interfaz con Vitest para los flujos esenciales.
- Revisión práctica de controles básicos: validación de entradas, permisos, gestión de secretos, errores y logs. La autenticación básica se desarrolla desde la fase 1; esta fase no la pospone.

**Resultado para cerrar la fase:** una demo pequeña que otra persona pueda ejecutar con la guía del repositorio, con pruebas y una revisión de seguridad documentada.

## Tecnologías previstas

- **Backend:** Python, FastAPI y Pydantic.
- **Datos:** PostgreSQL, SQL, SQLAlchemy y Alembic.
- **Calidad:** pytest, Ruff y GitHub Actions.
- **Entorno reproducible:** Docker Compose.
- **Análisis:** SQL, datos sintéticos con Faker y pandas; un notebook o informe breve antes de considerar un dashboard.
- **Frontend, fase 2:** React, TypeScript, Vite y Vitest.

Estas son tecnologías previstas, no componentes ya implementados. Se podrán revisar si una decisión técnica dificulta el aprendizaje o no aporta al MVP.

## Hoja de ruta

Las casillas describen el estado del trabajo del proyecto, no el avance de cursos externos. Cerrar una tarea exige código o documentación verificable y una explicación que el autor pueda dar sin depender de la IA.

### Preparación

- [x] Documentación inicial y planificación del backlog en Issues, según el plan inicial del proyecto.
- [x] Incorporar el roadmap visual original en `docs/roadmap-fraterchrist-v5.pdf`.
- [ ] Revisar las tareas del backlog contra este roadmap y mantener un único alcance vigente.

### Fase 1 — Backend y datos

- [ ] **Nodo 1 · Requisitos y Python base:** definir reglas de una publicación y validarla desde consola. Referencias del roadmap: Issues #1 y #3.
- [ ] **Nodo 2 · Pruebas del modelo:** escribir pruebas pytest para casos válidos e inválidos; explicar el código y los resultados.
- [ ] **Nodo 3 · SQL y PostgreSQL:** diseñar el modelo de usuarios y publicaciones/respuestas; crear migraciones reproducibles. Referencia: Issue #6.
- [ ] **Nodo 4 · API REST:** preparar FastAPI con `/health`, esquemas Pydantic y documentación OpenAPI. Referencia: Issue #2.
- [ ] **Nodo 5 · Backend del feed:** registro, inicio de sesión, permisos mínimos, crear/listar publicaciones y responder en hilos. Referencias: Issues #5, #7, #8 y #10.
- [ ] **Nodo 6 · Calidad y datos:** ejecutar pruebas y Ruff en GitHub Actions; documentar una demo; analizar actividad con datos sintéticos usando SQL y pandas. Referencias: Issues #11 y #12; el análisis se concretará en un Issue cuando corresponda.
- [ ] Verificar que las migraciones crean la base desde cero y que todas las pruebas se pueden repetir siguiendo el README.

### Fase 2 — Interfaz y seguridad aplicada

- [ ] Prototipar el flujo mínimo del feed. Referencia prevista en el roadmap: Issue #4.
- [ ] Conectar React + TypeScript con la API y probar los flujos principales. Referencia prevista: Issue #9.
- [ ] Documentar una revisión de seguridad y la gestión de secretos; corregir los hallazgos dentro del alcance del MVP.
- [ ] Publicar instrucciones de demo que otra persona pueda seguir desde un entorno limpio.

> Los números de Issue son referencias del roadmap entregado por el autor; este paquete ZIP no consulta ni modifica GitHub. Antes de cerrar tareas, verifica en el repositorio que los Issues existan y que sus descripciones sigan correspondiendo al alcance.

## Criterios para considerar una tarea terminada

1. Cumple un criterio de aceptación observable.
2. Incluye pruebas cuando el comportamiento lo requiere y las pruebas pasan.
3. El autor puede explicar la solución y sus decisiones sin depender de una respuesta generada por IA.
4. Los pasos para reproducir el resultado están documentados.
5. No incluye datos personales reales, contraseñas ni tokens.

## Documentación

- [Plan de aprendizaje](docs/PLAN-APRENDIZAJE.md)
- [Arquitectura propuesta](docs/ARQUITECTURA.md)
- [Requisitos del MVP](docs/REQUISITOS.md)
- [Plan de análisis de datos](docs/ANALISIS-DATOS.md)
- [Declaración de uso de IA](docs/USO-DE-IA.md)
- [Roadmap visual original (PDF)](docs/roadmap-fraterchrist-v5.pdf)
- [Contribución](CONTRIBUTING.md)
- [Seguridad](SECURITY.md)

## Datos y privacidad

Todo dato de ejemplo, prueba o análisis debe ser sintético. No cargar información personal, contraseñas reales, correos de otras personas ni registros extraídos de servicios reales. El proyecto no está listo para producción.

## Cómo contribuir y licencia

Las propuestas deben ser pequeñas, explicar el problema, indicar criterios de aceptación y aportar evidencia verificable. Consulta [CONTRIBUTING.md](CONTRIBUTING.md). El proyecto se ofrece bajo la licencia **GNU GPL v3.0**; ver [LICENSE](LICENSE).