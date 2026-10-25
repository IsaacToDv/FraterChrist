<h1 align="center">FraterChrist</h1>

<p align="center"><strong>Red social cristiana de código abierto para la comunión, el aprendizaje bíblico y la colaboración.</strong></p>

<p align="center">
  <a href="LICENSE"><img alt="Licencia GPL-3.0" src="https://img.shields.io/badge/Licencia%20GPL-3.0-blue?style=flat-square&logo=gnu&logoColor=white" /></a>
  <img alt="Proyecto en planificación" src="https://img.shields.io/badge/estado-MVP%20en%20planificaci%C3%B3n-yellow?style=for-the-badge" />
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

**Estado:** en planificación. FraterChrist todavía no está disponible para uso público.

<p align="center"><strong>Stack del MVP</strong></p>
<p align="center">
  <a href="https://www.python.org/"><img alt="Python" src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" /></a>
  <a href="https://www.djangoproject.com/"><img alt="Django" src="https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white" /></a>
  <a href="https://www.django-rest-framework.org/"><img alt="Django REST Framework" src="https://img.shields.io/badge/Django%20REST%20Framework-992E2E?style=flat-square&logo=django&logoColor=white" /></a>
  <a href="https://www.postgresql.org/"><img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" /></a>
  <a href="https://react.dev/"><img alt="React" src="https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB" /></a>
  <a href="https://www.typescriptlang.org/"><img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" /></a>
  <a href="https://vite.dev/"><img alt="Vite" src="https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white" /></a>
</p>
<p align="center">
  <a href="https://pytest-django.readthedocs.io/"><img alt="pytest-django" src="https://img.shields.io/badge/pytest--django-0A9EDC?style=flat-square&logo=pytest&logoColor=white" /></a>
  <a href="https://docs.astral.sh/ruff/"><img alt="Ruff" src="https://img.shields.io/badge/Ruff-D7FF64?style=flat-square&logo=ruff&logoColor=black" /></a>
  <a href="https://github.com/features/actions"><img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" /></a>
</p>

*Las tecnologías se adoptarán durante el desarrollo del MVP; las insignias no indican que ya estén implementadas.*

---

## Acerca de

FraterChrist es una propuesta de red social cristiana para compartir publicaciones y conversar en comunidad. Se desarrollará de forma abierta, priorizando una experiencia sencilla, privacidad por diseño y una arquitectura que permita añadir nuevas experiencias sin rehacer el Feed.

## MVP: el Feed

La primera versión se centrará en **publicaciones de texto, fotos y videos**, hilos de respuestas, cuentas de usuario y control de visibilidad.

| Visibilidad | Quién puede ver la publicación |
|---|---|
| **Pública** | Cualquier visitante, con o sin cuenta. |
| **Limitada a miembros** | Solo usuarios con sesión iniciada. |
| **Privada** | Solo el autor. |

En el MVP, las respuestas y los archivos adjuntos siguen la visibilidad de la publicación raíz. Las publicaciones limitadas no serán visibles para visitantes anónimos. La privacidad se valida en la API, no solo ocultando contenido en la interfaz.

## Arquitectura

El MVP usará un **monolito modular**: menos servicios que desplegar, una base de datos principal y límites claros entre módulos. Los archivos multimedia se guardarán fuera de PostgreSQL; la base de datos conservará sus metadatos. En desarrollo, el almacenamiento será privado y local; más adelante podrá cambiarse por uno compatible con S3.

### Diagrama de componentes

~~~mermaid
flowchart TB
    V["Visitante / miembro"]
    UI["Web: React + TypeScript + Vite"]
    API["API REST: Django REST Framework"]
    AUTH["Cuentas y permisos"]
    FEED["Feed: publicaciones e hilos"]
    MEDIA["Medios: validación y acceso protegido"]
    DB[("PostgreSQL<br/>usuarios · posts · metadatos")]
    FS[("Almacenamiento privado<br/>fotos y videos")]

    V --> UI
    UI <-->|HTTPS / JSON| API
    API --> AUTH
    API --> FEED
    API --> MEDIA
    AUTH --> DB
    FEED --> DB
    MEDIA --> DB
    MEDIA --> FS
~~~

### Modelo UML del dominio

~~~mermaid
classDiagram
    direction LR

    class User {
        +UUID id
        +string username
        +string email
        +string password_hash
        +datetime created_at
    }

    class Post {
        +UUID id
        +text content
        +Visibility visibility
        +datetime created_at
        +datetime updated_at
        +UUID author_id
        +UUID parent_post_id
    }

    class MediaAsset {
        +UUID id
        +MediaType media_type
        +string storage_key
        +string mime_type
        +bigint size_bytes
        +datetime created_at
    }

    class Visibility {
        <<enumeration>>
        PUBLIC
        MEMBERS
        PRIVATE
    }

    class MediaType {
        <<enumeration>>
        IMAGE
        VIDEO
    }

    User "1" --> "0..*" Post : publica
    Post "0..1" --> "0..*" Post : hilo y respuestas
    Post "1" --> "0..*" MediaAsset : adjunta
    Post --> Visibility : nivel de acceso
    MediaAsset --> MediaType : formato
~~~

El diagrama representa el diseño previsto, no modelos implementados. Los permisos se comprobarán tanto al consultar publicaciones como al servir sus archivos.

## Hoja de ruta del MVP

El orden de trabajo se refleja en las [Issues #20–#27](https://github.com/IsaacToDv/FraterChrist/issues).

1. **Base técnica** — [#20](https://github.com/IsaacToDv/FraterChrist/issues/20): Django, DRF, PostgreSQL y entorno reproducible.
2. **Modelo y privacidad** — [#21](https://github.com/IsaacToDv/FraterChrist/issues/21) y [#22](https://github.com/IsaacToDv/FraterChrist/issues/22): usuarios, publicaciones, hilos, medios, autenticación y permisos.
3. **Feed y multimedia** — [#23](https://github.com/IsaacToDv/FraterChrist/issues/23) y [#24](https://github.com/IsaacToDv/FraterChrist/issues/24): publicar, responder, listar y adjuntar fotos o videos.
4. **Interfaz usable** — [#25](https://github.com/IsaacToDv/FraterChrist/issues/25): conectar la web y completar los flujos principales.
5. **Verificación y entrega** — [#26](https://github.com/IsaacToDv/FraterChrist/issues/26) y [#27](https://github.com/IsaacToDv/FraterChrist/issues/27): pruebas de privacidad, CI y demo reproducible.

**Fuera del MVP:** perfiles avanzados, seguidores, mesas de oración o estudio, videollamadas, pizarras, juegos educativos, recomendaciones, dashboards y despliegue de producción. Se evaluarán cuando el Feed esté funcionando.

## Cómo colaborar

1. Abre una [Issue](https://github.com/IsaacToDv/FraterChrist/issues) o elige una tarea existente.
2. Haz **Fork** del repositorio y clónalo, reemplazando `TU-USUARIO` por tu usuario de GitHub:

~~~bash
git clone https://github.com/TU-USUARIO/FraterChrist.git
cd FraterChrist
git switch -c feat/mi-cambio
~~~

3. Haz tus cambios y súbelos:

~~~bash
git add .
git commit -m "feat: describe el cambio"
git push -u origin feat/mi-cambio
~~~

4. Abre un Pull Request desde tu fork hacia la rama `main` de FraterChrist.

Consulta las [pautas de contribución](CONTRIBUTING.md) antes de enviar cambios.

## Documentación

- [Arquitectura propuesta](docs/ARQUITECTURA.md)
- [Requisitos](docs/REQUISITOS.md)
- [Seguridad](SECURITY.md)

## Licencia

FraterChrist se distribuye bajo la licencia **GNU GPL v3.0**. Consulta [LICENSE](LICENSE).
