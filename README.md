<h1 align="center">FraterChrist</h1>

<p align="center"><strong>Core Feed · MVP de una red social cristiana</strong></p>

<p align="center">
  <a href="LICENSE"><img alt="Licencia GPL-3.0" src="https://img.shields.io/badge/licencia-GPL--3.0-6F42C1?style=flat-square&logo=gnu&logoColor=white" /></a>
  <img alt="Alcance Core Feed" src="https://img.shields.io/badge/MVP-Core%20Feed-6F42C1?style=flat-square" />
  <img alt="Estado en desarrollo" src="https://img.shields.io/badge/estado-en%20desarrollo-777777?style=flat-square" />
</p>

<p align="center">
  <a href="#core-feed">Alcance</a> ·
  <a href="#punto-de-partida">Punto de partida</a> ·
  <a href="#documentación">Documentación</a>
</p>

> <p align="center"><em>Marcos 16:15 — «Id por todo el mundo y predicad el evangelio a toda criatura».</em></p>

<p align="center"><strong>Stack previsto</strong></p>
<p align="center">
  <a href="https://www.python.org/"><img alt="Python" src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" /></a>
  <a href="https://www.djangoproject.com/"><img alt="Django REST Framework" src="https://img.shields.io/badge/Django%20REST-092E20?style=flat-square&logo=django&logoColor=white" /></a>
  <a href="https://www.postgresql.org/"><img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" /></a>
  <a href="https://react.dev/"><img alt="React" src="https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB" /></a>
  <a href="https://www.typescriptlang.org/"><img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" /></a>
</p>

*El stack y los diagramas describen el diseño previsto; no significan que la aplicación ya esté implementada.*

---

## Core Feed

Una primera versión pequeña y demostrable para practicar análisis, modelado, API REST y desarrollo frontend:

- Registro, inicio y cierre de sesión.
- Publicaciones **solo de texto** y feed cronológico.
- Visibilidad **pública** o **privada**.
- Respuestas simples a publicaciones raíz.
- Edición y eliminación únicamente por parte del autor.
- Interfaz mínima que consume la API.

## Punto de partida

**Empieza por [Issue #20 — preparar Django, DRF y PostgreSQL](https://github.com/IsaacToDv/FraterChrist/issues/20).** Implementa cada etapa y verifica el resultado antes de avanzar.

```mermaid
flowchart LR
    A["#20 · Entorno"] --> B["#21 · Modelos"]
    B --> C["#22 · Auth y permisos"]
    C --> D["#23 · API del Feed"]
    D --> E["#25 · Frontend"]
    E --> F["#26 · Pruebas y CI"]
    F --> G["#27 · Demo"]
```

### Modelo mínimo del Core

```mermaid
classDiagram
    direction LR
    class User {
        usuario de Django
    }
    class Post {
        contenido de texto
        visibilidad public o private
        fecha de creación
        parent_post opcional
    }
    User "1" --> "0..*" Post : autor
    Post "0..1" <-- "0..*" Post : publicación raíz y respuestas
```

Una publicación sin padre es una raíz; una respuesta apunta directamente a esa raíz. Las respuestas heredan su visibilidad. La API, no la interfaz, aplica los permisos.

## Documentación

- [Requisitos funcionales y no funcionales](docs/REQUISITOS.md)
- [Arquitectura y diagramas](docs/ARQUITECTURA.md)
- [Plan de implementación](docs/PLAN-IMPLEMENTACION.md)
- [Progreso y bitácora de aprendizaje](Progreso/README.md)

## Fuera del Core

- **Issue #24:** fotos, videos y acceso protegido a archivos.
- **Issue #28:** visibilidad para miembros.
- Perfiles avanzados, likes, seguidores, mensajes, recomendaciones, salas, videollamadas, pizarras y juegos.

Estas funciones se retoman en fases futuras, después de completar y probar el Core.

## Estructura prevista

```text
FraterChrist/
├── backend/     # Django + API REST
├── frontend/    # React + TypeScript
├── docs/        # Requisitos, arquitectura y plan
└── Progreso/    # Bitácora y evidencia verificable
```

## Licencia

Este proyecto se distribuye bajo la licencia **GNU GPL v3.0**. Consulta [LICENSE](LICENSE).
