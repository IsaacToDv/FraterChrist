# Arquitectura inicial de FraterChrist

**Estado:** propuesta que debe contrastarse con la primera implementación.

## Estilo
Monolito modular con diseño componible: una aplicación desplegable, dividida en módulos con responsabilidades claras e interfaces explícitas. Aquí «Composable Architecture» es un principio de diseño modular, no la biblioteca TCA de Swift/Apple.

## Stack propuesto
- Python 3.12+ (versión fijada tras validar compatibilidad)
- FastAPI y Pydantic para API REST y validación
- PostgreSQL
- SQLAlchemy 2 y Alembic
- pytest y Ruff
- Docker Compose
- GitHub Actions para CI

No se añadirá frontend completo antes de probar un caso de uso backend.

## Responsabilidades
1. **API/routers:** HTTP, códigos de estado y esquemas.
2. **Aplicación/casos de uso:** coordinar operaciones.
3. **Dominio:** reglas de negocio comprobables sin HTTP ni base de datos.
4. **Repositorios:** consultas, persistencia y transacciones.
5. **Infraestructura:** configuración, conexiones y adaptadores.

Estas capas son una guía, no una obligación de crear clases para cada operación.

## Módulos previstos
- `identity`: cuentas, perfiles y preferencias.
- `feed`: publicaciones y respuestas.
- `doctrine`: preguntas, bosquejos y recursos.
- `mesa`: espacios y membresías.
- `kit`: notas privadas y herramientas bíblicas.
- `notifications`: avisos y correo voluntario.
- `moderation`: reportes y bloqueos.

Crear módulos cuando una etapa los necesite; no mantener directorios vacíos para simular progreso.

## Seguridad y mantenibilidad
Validar entradas; comprobar autenticación y autorización en servidor; mantener secretos fuera de Git; usar restricciones relacionales y consultas parametrizadas; definir transacciones; probar fallos y accesos denegados; evitar microservicios, colas o cachés sin una necesidad medible.

## Decisiones pendientes
Autenticación, visibilidad, moderación, fuente/licencia bíblica, archivos, búsqueda/paginación, correo y despliegue. Registrar decisiones importantes como ADR.