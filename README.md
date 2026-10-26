<h1 align="center">FraterChrist</h1>

<p align="center"><strong>Proyecto personal para diseñar y construir el MVP de una red social cristiana.</strong></p>

<p align="center">
  <a href="LICENSE"><img alt="Licencia GPL-3.0" src="https://img.shields.io/badge/licencia-GPL--3.0-6F42C1?style=flat-square&logo=gnu&logoColor=white" /></a>
  <img alt="Proyecto personal" src="https://img.shields.io/badge/proyecto-personal-6F42C1?style=for-the-badge" />
  <img alt="Estado del MVP" src="https://img.shields.io/badge/estado-MVP%20en%20desarrollo-7C6F9B?style=for-the-badge" />
</p>

<blockquote>
  <p align="center"><em>Marcos 16:15 — «Id por todo el mundo y predicad el evangelio a toda criatura».</em></p>
</blockquote>

<p align="center">
  <a href="#proyecto-personal">Proyecto</a> ·
  <a href="#progreso">Progreso</a> ·
  <a href="#arquitectura">Arquitectura</a> ·
  <a href="#roadmap">Roadmap</a> ·
  <a href="#estructura-del-repositorio">Estructura</a>
</p>

<p align="center"><strong>Stack previsto</strong></p>
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
  <a href="https://vitest.dev/"><img alt="Vitest" src="https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white" /></a>
  <a href="https://github.com/features/actions"><img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" /></a>
</p>

*El stack está propuesto; las insignias no significan que esas tecnologías ya estén implementadas.*

---

## Proyecto personal

Este repositorio documenta el desarrollo individual de un **MVP de portafolio**: un feed con publicaciones, respuestas y controles de visibilidad. El objetivo es practicar y demostrar decisiones de arquitectura, desarrollo backend y frontend, modelado de datos, pruebas y manejo seguro de archivos.

**Estado actual:** el código de la aplicación aún está por desarrollar. Este repositorio no es la plataforma completa ni el repositorio principal de la futura iniciativa comunitaria.

## Progreso

<p align="center">
  <a href="Progreso/README.md"><img alt="Consultar progreso y aprendizaje" src="https://img.shields.io/badge/Progreso-bit%C3%A1cora%20de%20aprendizaje-6F42C1?style=for-the-badge&logo=github&logoColor=white" /></a>
</p>

La carpeta [`Progreso/`](Progreso/README.md) reúne el avance del MVP, los conceptos aprendidos, las dificultades resueltas y la evidencia de cada sesión. El registro distingue la planificación del trabajo realmente implementado.

- [Panel de progreso](Progreso/README.md)
- [Bitácora de aprendizaje](Progreso/REGISTRO.md)

## Alcance del MVP

- Publicaciones de texto, fotos y videos.
- Respuestas directas a publicaciones raíz.
- Registro e inicio de sesión.
- Tres niveles de visibilidad:

| Nivel | Quién puede leer |
|---|---|
| **Público** | Cualquier visitante, con o sin cuenta. |
| **Limitado a miembros** | Usuarios con sesión iniciada. |
| **Privado** | Solo el autor. |

Las respuestas y sus archivos heredan la visibilidad de la publicación raíz. Los permisos deben comprobarse en la API y al servir los archivos, no solo en la interfaz.

## Arquitectura

El MVP usará un **monolito modular**: Django REST Framework como API, React con TypeScript para la interfaz y PostgreSQL para los datos. Las fotos y los videos se guardarán fuera de PostgreSQL; la base conservará sus metadatos. Durante el desarrollo se utilizará almacenamiento local privado.

### Diagrama de componentes

~~~mermaid
flowchart TB
    Visitor["Visitor or member"]
    Web["Web client<br/>React · TypeScript · Vite"]
    API["REST API<br/>Django REST Framework"]
    Accounts["Accounts<br/>identity and sign-in"]
    Feed["Feed<br/>posts and replies"]
    Media["Media<br/>file validation and access control"]
    DB[("PostgreSQL<br/>users · posts · media metadata")]
    Storage[("Private file storage<br/>photos and videos")]

    Visitor --> Web
    Web <-->|HTTPS · JSON| API
    API --> Accounts
    API --> Feed
    API --> Media
    Accounts --> DB
    Feed --> DB
    Media --> DB
    Media --> Storage
~~~

### UML class diagram

~~~mermaid
classDiagram
    direction LR

    class User {
        +id: integer
        +username: string
        +email: string
        +password: string
        +date_joined: datetime
    }

    class Post {
        +id: integer
        +author: User
        +content: text
        +visibility: Visibility
        +parent_post: Post
        +created_at: datetime
        +updated_at: datetime
    }

    class MediaFile {
        +id: integer
        +post: Post
        +file: FileField
        +file_type: FileType
        +content_type: string
        +file_size: integer
        +created_at: datetime
    }

    class Visibility {
        <<enumeration>>
        public
        members
        private
    }

    class FileType {
        <<enumeration>>
        image
        video
    }

    User "1" --> "0..*" Post : author
    Post "0..1" <-- "0..*" Post : parent / replies
    Post "1" <-- "0..*" MediaFile : attached files
    Post --> Visibility : visibility
    MediaFile --> FileType : file type
~~~

<details>
<summary><strong>How to read the UML</strong></summary>

- **User → Post:** one user can create many posts; each post has one author.
- **Post → Post:** `parent_post` is optional. A root post has no parent; a reply points directly to the root post. Nested replies are outside this MVP.
- **Post → MediaFile:** a post can have zero or more attachments; each file belongs to one post.
- **Visibility:** `public` allows anonymous reading, `members` requires a signed-in user, and `private` is readable only by the author.
- **FileType:** indicates whether the attachment is an image or video.

Django's `User.password` stores a password hash, never the original password. `MediaFile.file` is a storage reference; the binary file is not stored in PostgreSQL.

This is a proposed design, not implemented code.
</details>

## Roadmap

<p align="center">
  <a href="docs/roadmap-fraterchrist.pdf"><img alt="Abrir roadmap visual en PDF" src="https://img.shields.io/badge/ROADMAP-Abrir%20PDF-6F42C1?style=for-the-badge&logo=adobeacrobatreader&logoColor=white" /></a>
</p>

<p align="center"><a href="docs/roadmap-fraterchrist.pdf">Ver roadmap visual original (PDF)</a></p>

<details open>
<summary><strong>1 · Base técnica</strong> — Issue #20</summary>

Preparar Django, Django REST Framework, PostgreSQL y el entorno de desarrollo.

[Issue #20](https://github.com/IsaacToDv/FraterChrist/issues/20)
</details>

<details>
<summary><strong>2 · Modelos y privacidad</strong> — Issues #21–#22</summary>

Modelar usuarios, publicaciones y archivos; definir autenticación y permisos de lectura.

[Issue #21 · Modelos](https://github.com/IsaacToDv/FraterChrist/issues/21) · [Issue #22 · Permisos](https://github.com/IsaacToDv/FraterChrist/issues/22)
</details>

<details>
<summary><strong>3 · Feed y multimedia</strong> — Issues #23–#24</summary>

Implementar el feed cronológico, las respuestas y la carga protegida de fotos y videos.

[Issue #23 · Feed](https://github.com/IsaacToDv/FraterChrist/issues/23) · [Issue #24 · Multimedia](https://github.com/IsaacToDv/FraterChrist/issues/24)
</details>

<details>
<summary><strong>4 · Interfaz web</strong> — Issue #25</summary>

Conectar React y TypeScript con la API y completar los flujos principales.

[Issue #25 · Frontend](https://github.com/IsaacToDv/FraterChrist/issues/25)
</details>

<details>
<summary><strong>5 · Pruebas y evidencia de portafolio</strong> — Issues #26–#27</summary>

Automatizar pruebas, verificar permisos y documentar cómo ejecutar y demostrar el MVP.

[Issue #26 · Pruebas](https://github.com/IsaacToDv/FraterChrist/issues/26) · [Issue #27 · Portafolio](https://github.com/IsaacToDv/FraterChrist/issues/27)
</details>

**Fuera del MVP:** perfiles avanzados, seguidores, mesas de oración o estudio, videollamadas, pizarras y juegos educativos. Esas funcionalidades pertenecen a una posible etapa futura.

## Estructura del repositorio

~~~text
FraterChrist/
├── backend/        # API Django REST Framework
├── frontend/       # React + TypeScript + Vite
├── docs/           # Arquitectura, requisitos y plan
├── Progreso/       # Bitácora de aprendizaje y evidencias
├── .gitignore
├── LICENSE
└── README.md
~~~

## Documentación

[Arquitectura](docs/ARQUITECTURA.md) · [Requisitos](docs/REQUISITOS.md) · [Plan de implementación](docs/PLAN-IMPLEMENTACION.md)

## Licencia

Este proyecto se distribuye bajo la licencia **GNU GPL v3.0**. Consulta [LICENSE](LICENSE).
