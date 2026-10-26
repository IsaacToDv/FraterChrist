<h1 align="center">FraterChrist</h1>

<p align="center"><strong>Red social cristiana de código abierto para la comunión, el aprendizaje bíblico y la colaboración.</strong></p>

<p align="center">
  <a href="LICENSE"><img alt="Licencia GPL-3.0" src="https://img.shields.io/badge/Licencia%20GPL-3.0-blue?style=flat-square&logo=gnu&logoColor=white" /></a>
  <img alt="Proyecto en planificación" src="https://img.shields.io/badge/estado-MVP%20en%20planificaci%C3%B3n-6F42C1?style=for-the-badge" />
  <img alt="Open source · contribuciones bienvenidas" src="https://img.shields.io/badge/open%20source-contribuciones%20bienvenidas-6F42C1?style=for-the-badge&logo=github&logoColor=white" />
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
  <a href="https://vitest.dev/"><img alt="Vitest" src="https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white" /></a>
  <a href="https://github.com/features/actions"><img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" /></a>
</p>

*Las tecnologías se adoptarán durante el desarrollo del MVP; las insignias no indican que ya estén implementadas.*

---

<p align="center">
  <a href="#mvp">MVP</a> ·
  <a href="#arquitectura">Arquitectura</a> ·
  <a href="#roadmap">Roadmap</a> ·
  <a href="#contribuir">Contribuir</a> ·
  <a href="#licencia">Licencia</a>
</p>

---

## MVP

FraterChrist comienza con un **Feed para publicaciones de texto, fotos y videos**, respuestas en hilos y control de visibilidad.

| Visibilidad | Quién puede leer |
|---|---|
| **Pública** | Cualquier visitante, con o sin cuenta. |
| **Limitada a miembros** | Usuarios con sesión iniciada. |
| **Privada** | Solo el autor. |

Las respuestas y sus archivos adjuntos heredan la visibilidad de la publicación raíz. La API debe validar los permisos en cada lectura; ocultar contenido en la interfaz no es suficiente.

## Arquitectura

El MVP usa un **monolito modular** con Django REST Framework, React y PostgreSQL. Los archivos multimedia se almacenan fuera de la base de datos y PostgreSQL conserva sus metadatos. El almacenamiento local será privado durante el desarrollo, con opción de migrar después a un servicio compatible con S3.

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
    Post "0..1" --> "0..*" Post : parent / replies
    Post "1" --> "0..*" MediaFile : attached files
    Post --> Visibility : visibility
    MediaFile --> FileType : file type
~~~

<details>
<summary><strong>Cómo leer el UML</strong></summary>

- **User → Post:** una cuenta puede crear muchas publicaciones; cada publicación tiene un autor.
- **Post → Post:** `parent_post` es opcional. Una publicación raíz no tiene padre; una respuesta apunta a la publicación raíz. Las respuestas anidadas quedan fuera del MVP.
- **Post → MediaFile:** una publicación puede tener cero o varios archivos adjuntos.
- **Visibility:** `public` permite leer sin sesión, `members` requiere iniciar sesión y `private` solo permite leer al autor.
- **FileType:** identifica si el archivo es una imagen o un video.

`User.password` es el campo de Django que almacena un hash de contraseña, no la contraseña original. `MediaFile.file` guarda una referencia al almacenamiento; el binario no se guarda en PostgreSQL.

Este UML describe el diseño previsto. No representa modelos que ya estén implementados.
</details>

## Roadmap

<p align="center">
  <a href="docs/roadmap-fraterchrist.pdf"><img alt="Abrir roadmap visual en PDF" src="https://img.shields.io/badge/ROADMAP-Abrir%20PDF-6F42C1?style=for-the-badge&logo=adobeacrobatreader&logoColor=white" /></a>
</p>

<p align="center">
  <a href="docs/roadmap-fraterchrist.pdf">Ver roadmap visual original (PDF)</a> ·
  <a href="docs/roadmap-fraterchrist.pdf">Abrir o descargar PDF</a>
</p>

<p align="center"><em>El PDF conserva el roadmap visual; las Issues enlazadas son la referencia de trabajo del MVP.</em></p>

<details open>
<summary><strong>1 · Base técnica</strong> — Issue #20</summary>

Preparar Django, Django REST Framework, PostgreSQL y el entorno local reproducible.

[Ver Issue #20](https://github.com/IsaacToDv/FraterChrist/issues/20)
</details>

<details>
<summary><strong>2 · Modelos y privacidad</strong> — Issues #21–#22</summary>

Definir usuarios, publicaciones, respuestas y archivos. Implementar registro, sesión y permisos para publicaciones públicas, limitadas y privadas.

[Issue #21 · Modelos](https://github.com/IsaacToDv/FraterChrist/issues/21) · [Issue #22 · Autenticación y permisos](https://github.com/IsaacToDv/FraterChrist/issues/22)
</details>

<details>
<summary><strong>3 · Feed y multimedia</strong> — Issues #23–#24</summary>

Crear el listado cronológico, publicar y responder en hilos, y añadir fotos y videos con acceso protegido.

[Issue #23 · Feed](https://github.com/IsaacToDv/FraterChrist/issues/23) · [Issue #24 · Multimedia](https://github.com/IsaacToDv/FraterChrist/issues/24)
</details>

<details>
<summary><strong>4 · Interfaz web</strong> — Issue #25</summary>

Conectar React y TypeScript a la API y completar los flujos básicos: leer, iniciar sesión, publicar y responder.

[Ver Issue #25](https://github.com/IsaacToDv/FraterChrist/issues/25)
</details>

<details>
<summary><strong>5 · Pruebas y entrega</strong> — Issues #26–#27</summary>

Comprobar la privacidad y los flujos principales, automatizar pruebas y linting, y documentar cómo ejecutar el MVP desde cero.

[Issue #26 · Pruebas y CI](https://github.com/IsaacToDv/FraterChrist/issues/26) · [Issue #27 · Documentación y demo](https://github.com/IsaacToDv/FraterChrist/issues/27)
</details>

**Después del MVP:** perfiles avanzados, seguidores, mesas de oración o estudio, videollamadas, pizarras y juegos educativos.

## Contribuir

Las contribuciones son bienvenidas. Empieza por una [Issue abierta](https://github.com/IsaacToDv/FraterChrist/issues), haz un fork y crea una rama:

~~~bash
git clone https://github.com/TU-USUARIO/FraterChrist.git
cd FraterChrist
git switch -c feat/mi-cambio
~~~

Después, realiza y sube tus cambios:

~~~bash
git add .
git commit -m "feat: describe el cambio"
git push -u origin feat/mi-cambio
~~~

Abre un Pull Request desde tu fork hacia la rama `main` de FraterChrist. Consulta las [pautas de contribución](CONTRIBUTING.md) antes de enviar cambios.

## Documentación

[Arquitectura](docs/ARQUITECTURA.md) · [Requisitos del MVP](docs/REQUISITOS.md) · [Guía de desarrollo](docs/GUIA-DESARROLLO-MVP.md) · [Seguridad](SECURITY.md)

## Licencia

FraterChrist se distribuye bajo la licencia **GNU GPL v3.0**. Consulta [LICENSE](LICENSE).
