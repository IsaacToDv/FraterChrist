<h1 align="center">FraterChrist</h1>

<p align="center"><strong>Red social cristiana · MVP personal de portafolio</strong></p>

<p align="center">
  <a href="LICENSE"><img alt="Licencia GPL-3.0" src="https://img.shields.io/badge/licencia-GPL--3.0-6F42C1?style=flat-square&logo=gnu&logoColor=white" /></a>
  <img alt="Alcance" src="https://img.shields.io/badge/MVP-Core%20Feed-6F42C1?style=flat-square" />
  <img alt="Estado" src="https://img.shields.io/badge/estado-en%20desarrollo-777777?style=flat-square" />
</p>

> <p align="center"><em>Marcos 16:15 — «Id por todo el mundo y predicad el evangelio a toda criatura».</em></p>

## Core Feed

El primer objetivo es una aplicación web pequeña y funcional que permita:
- Registrar usuarios e iniciar/cerrar sesión.
- Crear publicaciones de **texto** y consultar un feed cronológico.
- Elegir visibilidad **pública** o **privada**.
- Responder a publicaciones con comentarios simples.
- Editar o eliminar únicamente el contenido propio.
- Consumir la API REST desde una interfaz web mínima.

**Estado actual:** alcance y diseño documentados; la aplicación todavía no está implementada. Este repositorio distingue las decisiones de diseño de las funciones verificadas.

## Stack previsto

- **Backend:** Python, Django y Django REST Framework.
- **Datos:** PostgreSQL.
- **Frontend:** React, TypeScript y Vite.
- **Calidad:** pruebas automatizadas, Ruff y GitHub Actions.

## Punto de partida

Empieza por la [Issue #20 — preparar el entorno](https://github.com/IsaacToDv/FraterChrist/issues/20). El trabajo está ordenado en las issues del Core:

1. [#20 Fundación técnica](https://github.com/IsaacToDv/FraterChrist/issues/20)
2. [#21 Modelos y relaciones](https://github.com/IsaacToDv/FraterChrist/issues/21)
3. [#22 Autenticación y permisos](https://github.com/IsaacToDv/FraterChrist/issues/22)
4. [#23 API de publicaciones y respuestas](https://github.com/IsaacToDv/FraterChrist/issues/23)
5. [#25 Frontend mínimo](https://github.com/IsaacToDv/FraterChrist/issues/25)
6. [#26 Pruebas y CI](https://github.com/IsaacToDv/FraterChrist/issues/26)
7. [#27 Demo y evidencia](https://github.com/IsaacToDv/FraterChrist/issues/27)

Las pruebas se desarrollan junto con cada funcionalidad, aunque la issue #26 consolida la cobertura y la integración continua.

## Documentación

- [Requisitos funcionales y no funcionales](docs/REQUISITOS.md)
- [Arquitectura y diagramas](docs/ARQUITECTURA.md)
- [Plan de implementación](docs/PLAN-IMPLEMENTACION.md)
- [Bitácora de progreso](Progreso/README.md)

## Fuera del Core

La multimedia y su almacenamiento protegido están pospuestos en la [Issue #24](https://github.com/IsaacToDv/FraterChrist/issues/24). La visibilidad **solo para miembros** queda para una fase posterior; consulta las [issues de expansión](https://github.com/IsaacToDv/FraterChrist/issues).

Likes, seguidores, mensajes directos, recomendaciones, videollamadas, salas, pizarras y juegos también quedan fuera de esta primera versión.

## Estructura prevista

```text
FraterChrist/
├── backend/     # Django + API REST
├── frontend/    # React + TypeScript
├── docs/        # Requisitos, arquitectura y plan
└── Progreso/    # Bitácora de aprendizaje y evidencias
```

## Licencia

Este proyecto se distribuye bajo la licencia **GNU GPL v3.0**. Consulta [LICENSE](LICENSE).
