# Arquitectura y stack de FraterChrist

**Estado:** propuesta para el MVP. Se ajustará cuando haya código y mediciones reales.

## Decisión principal

Empezar con un **monolito modular**: una API y una aplicación web, con responsabilidades separadas dentro de un mismo proyecto. No usar microservicios ni añadir herramientas sin una necesidad concreta.

## Stack del MVP

| Área | Tecnología | Motivo |
|---|---|---|
| Backend | Python + FastAPI | API REST clara, validación y documentación automática. |
| Base de datos | PostgreSQL | Datos relacionales, restricciones e integridad. |
| Persistencia | SQLAlchemy | Facilita consultas sin ocultar el modelo SQL. |
| Migraciones | Alembic | Cambios de esquema versionados y reproducibles. |
| Frontend | React + TypeScript + Vite | Interfaz web tipada y desarrollo sencillo. |
| Pruebas backend | pytest | Pruebas unitarias y de integración. |
| Pruebas frontend | Vitest | Pruebas de la lógica de interfaz. |
| Calidad | Ruff | Formato y análisis estático de Python. |
| Entorno local | Docker Compose | Levantar PostgreSQL de forma reproducible. |
| Automatización | GitHub Actions | Ejecutar pruebas y verificaciones en cada cambio. |

Se fijarán versiones compatibles en los archivos de dependencias al implementar el MVP. No se añadirá una librería de estado, un sistema de caché, una cola de tareas ni una arquitectura de microservicios sin justificar su necesidad.

## Organización

- **Frontend:** páginas y componentes de interfaz.
- **API:** rutas HTTP, validación y respuestas.
- **Aplicación:** operaciones del usuario, por ejemplo crear una publicación.
- **Dominio:** reglas del feed y sus conversaciones.
- **Persistencia:** consultas y transacciones de PostgreSQL.

Esta separación es una guía práctica, no una obligación de crear capas o clases para cada función.

## Alcance inicial

El primer caso de uso será el Feed: crear y consultar publicaciones. Después se añadirán respuestas en hilos, validación de datos, paginación y permisos según el progreso.

## Calidad y rendimiento

- Medir antes de optimizar prematuramente.
- Paginar el Feed y limitar el tamaño de las peticiones.
- Diseñar consultas simples y revisar su plan cuando sea necesario.
- Añadir índices según consultas reales y restricciones, no por anticipación.
- Usar restricciones y transacciones de PostgreSQL para mantener datos consistentes.
- Probar casos correctos, entradas inválidas y accesos no autorizados.
- Mantener secretos fuera de Git.
- Automatizar pruebas y comprobaciones en CI.

## Decisiones pendientes

Autenticación, reglas de visibilidad, moderación, fuente bíblica y licencia, alojamiento y correo. Se decidirán cuando el alcance del MVP lo requiera.
