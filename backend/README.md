# Backend

Backend del Core Feed previsto con Python, Django, Django REST Framework y PostgreSQL.

## Punto de partida

Comienza por la [Issue #20](https://github.com/IsaacToDv/FraterChrist/issues/20). La primera meta es levantar Django, conectar PostgreSQL y exponer GET /api/health/.

## Módulos previstos

```text
backend/
├── manage.py
├── config/
└── apps/
    ├── accounts/
    └── feed/
```

El Core no incluye archivos multimedia ni un módulo de almacenamiento. Consulta la [arquitectura](../docs/ARQUITECTURA.md) y los [requisitos](../docs/REQUISITOS.md).

**Estado:** esta carpeta todavía no contiene una API implementada.
