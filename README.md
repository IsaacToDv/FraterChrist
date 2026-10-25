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

FraterChrist es una red social cristiana de código abierto para compartir publicaciones y conversar en comunidad. El MVP se centra en el Feed; los perfiles avanzados, las mesas y las salas interactivas se incorporarán más adelante.

## MVP: el Feed

La primera versión incluirá publicaciones de texto, fotos y videos, hilos de respuestas, cuentas y tres niveles de visibilidad.

| Visibilidad | Quién puede leer |
|---|---|
| **Pública** | Cualquier visitante, con o sin cuenta. |
| **Limitada a miembros** | Usuarios con sesión iniciada. |
| **Privada** | Solo el autor. |

Las respuestas y los archivos adjuntos heredan la visibilidad de la publicación raíz. La API comprobará los permisos en cada lectura; ocultar contenido en la interfaz no es suficiente.

## Arquitectura

El MVP usa un **monolito modular**: una aplicación Django con módulos separados, una API REST y PostgreSQL. Los archivos multimedia se almacenan fuera de la base de datos. En desarrollo, se usará almacenamiento local privado; se podrá sustituir por almacenamiento compatible con S3 más adelante.

### Componentes

~~~mermaid
flowchart TB
    Visitor["Visitor or member"]
    Web["Web client<br/>React · TypeScript · Vite"]
    API["REST API<br/>Django REST Framework"]
    Accounts["Accounts<br/>sign-in and user identity"]
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
        +content: text
        +visibility: Visibility
        +created_at: datetime
        +updated_at: datetime
    }

    class MediaFile {
        +id: integer
        +file: file_path
        +file_type: FileType
        +content_type: string
        +file_size: integer
        +created_at: datetime
    }

    class Visibility {
        <<enumeration>>
        PUBLIC
        MEMBERS
        PRIVATE
    }

    class FileType {
        <<enumeration>>
        IMAGE
        VIDEO
    }

    User "1" --> "0..*" Post : author
    Post "0..1" --> "0..*" Post : parent_post / replies
    Post "1" --> "0..*" MediaFile : attached_files
    Post --> Visibility : visibility
    MediaFile --> FileType : file_type
~~~

The UML uses the proposed Django model names and fields. `User.password` is managed by Django and stores a password hash, never the original password. `Post.parent_post` is optional: it is empty for a root post and points to the parent post for a reply. `MediaFile.file` stores a path or storage reference, not the binary data in PostgreSQL. These are planned models, not implemented code.

## Hoja de ruta del MVP

El orden activo está en las [Issues #20–#27](https://github.com/IsaacToDv/FraterChrist/issues).

1. **Base técnica** — [#20](https://github.com/IsaacToDv/FraterChrist/issues/20): Django, Django REST Framework y PostgreSQL.
2. **Modelos y privacidad** — [#21](https://github.com/IsaacToDv/FraterChrist/issues/21) y [#22](https://github.com/IsaacToDv/FraterChrist/issues/22): usuarios, publicaciones, adjuntos, autenticación y permisos.
3. **Feed y multimedia** — [#23](https://github.com/IsaacToDv/FraterChrist/issues/23) y [#24](https://github.com/IsaacToDv/FraterChrist/issues/24): listar, publicar, responder y cargar fotos o videos.
4. **Interfaz web** — [#25](https://github.com/IsaacToDv/FraterChrist/issues/25): conectar React con la API.
5. **Calidad y entrega** — [#26](https://github.com/IsaacToDv/FraterChrist/issues/26) y [#27](https://github.com/IsaacToDv/FraterChrist/issues/27): pruebas de privacidad, integración continua y guía de ejecución.

**Después del MVP:** perfiles avanzados, seguidores, mesas de oración o estudio, videollamadas, pizarras y juegos educativos.

## Cómo colaborar

1. Elige una [Issue abierta](https://github.com/IsaacToDv/FraterChrist/issues) o crea una propuesta.
2. Haz un **Fork** y clónalo. Sustituye `TU-USUARIO` por tu usuario de GitHub:

~~~bash
git clone https://github.com/TU-USUARIO/FraterChrist.git
cd FraterChrist
git switch -c feat/mi-cambio
~~~

3. Haz los cambios y súbelos:

~~~bash
git add .
git commit -m "feat: describe el cambio"
git push -u origin feat/mi-cambio
~~~

4. Abre un Pull Request desde tu fork hacia la rama `main` de FraterChrist.

Lee las [pautas de contribución](CONTRIBUTING.md) antes de enviar cambios.

## Documentación

- [Arquitectura del MVP](docs/ARQUITECTURA.md)
- [Requisitos del MVP](docs/REQUISITOS.md)
- [Seguridad](SECURITY.md)

## Licencia

FraterChrist se distribuye bajo la licencia **GNU GPL v3.0**. Consulta [LICENSE](LICENSE).
