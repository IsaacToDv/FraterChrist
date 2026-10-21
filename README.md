# FraterChrist

**Red social cristiana de código abierto para edificación, aprendizaje bíblico y colaboración.**  
**Proyecto personal de aprendizaje orientado a backend, APIs REST y PostgreSQL.**

> **Estado del proyecto:** fase de planificación y documentación. La API y las funcionalidades de producto aún no están implementadas como tal. En la carpeta /MVP estará una demostración de un MVP del proyecto que demuestra mi desempeño en Python, TS, API REST y SQL.

## ¿Qué quiero demostrar con este proyecto?

Soy estudiante de Ingeniería de Software y Datos en la IU Digital de Antioquia y aprendiz de Análisis y Desarrollo de Software (ADSO) en el SENA. Busco fortalecer mi perfil de desarrollo backend junior mediante incrementos progresivos de FraterChrist, documentando tanto los resultados como las decisiones y pruebas que los respaldan.

El objetivo de este proyecto y su MVP es demostrar mis bases sobre modelado relacional, construcción e implementación de APIs REST, validación de entradas, pruebas, seguridad básica y documentación técnica. Asimismo, la colaboración con otros developers voluntarios a contribuir en este proyecto.

## Problema y propuesta

Las comunidades cristianas siempre tienden a tener comuión unos con otros incluso desde los primeros siglos, por esta misma razón me cuestioné a cerca del porqué el cristianismo no tiene su propio "Reddit" en el cual pudieran usar para edificación mutua, este proyecto va orientado exclusivamente para la comunión entre hermanos incluyendo a personas inconversas. Esta propuesta que planteo construye un ecosistema monolito progresivo enfocado en hilos, recursos de estudio bíblico, cuaderno virtual, gaming y colaboración. FraterChrist propone reunir estas actividades en una plataforma OpenSource para la colaboración y crecimiento, adoptando la filosofia de la programación modular para una mejor calidad del producto.

### Módulos previstos

- **Feed:** publicaciones y conversaciones por hilos.
- **Mesa:** espacios colaborativos para devocionales, estudios bíblicos, ideas, programación y videojuegos.
- **Zona doctrinal:** preguntas y respuestas, plantillas de bosquejos y recursos.
- **Kit:** Biblia, cuaderno personal y herramientas complementarias.
- **Notificaciones:** correos de edificación y newsletters con suscripción voluntaria.
  
  Donde **Feed** será la prioridad inicial para ver mejor la trazabilidad del proyecto.

Nota. Estos módulos son solo la visión del producto, se implementarán según la hoja de ruta y las evidencias de cada etapa.

## Competencias y evidencias

| Competencia que quiero demostrar | Evidencia que encontrará el revisor |
|---|---|
| Python y programación orientada a objetos | Módulos de dominio pequeños, casos de uso y pruebas que pueda explicar. |
| SQL y PostgreSQL | Modelo relacional, migraciones, restricciones, consultas documentadas y pruebas de persistencia. |
| APIs REST | Endpoints con esquemas de entrada/salida, códigos HTTP adecuados, manejo de errores y documentación OpenAPI. |
| Modelado y arquitectura | Requisitos, diagramas UML cuando aporten valor y decisiones arquitectónicas justificadas. |
| Calidad del software | Pruebas unitarias e integración, criterios de aceptación y comprobaciones automatizadas. |
| Seguridad básica | Validación en servidor, secretos fuera del repositorio, autorización comprobada y revisión de casos negativos. |
| Git, GitHub, shell y Linux | Historial de cambios pequeños, issues, pull requests y pasos de ejecución reproducibles. |
| Trabajo asistido por IA | Registro de sugerencias relevantes y evidencia de revisión, pruebas y comprensión del código aceptado. |

La correspondencia detallada entre mi CV y las evidencias está en [docs/MAPA-CV-EVIDENCIAS.md](docs/MAPA-CV-EVIDENCIAS.md).

## Arquitectura prevista

Se empezará con un **backend Python organizado como monolito modular**. Cada módulo tendrá responsabilidades claras y se integrará mediante interfaces explícitas; no se crearán microservicios ni capas innecesarias para aparentar complejidad.

**Stack inicial propuesto:**

- Python 3.12 o superior, según compatibilidad comprobada del entorno.
- FastAPI para la API REST.
- Pydantic para validar y describir datos.
- PostgreSQL como base de datos relacional.
- SQLAlchemy 2 y Alembic para acceso a datos y migraciones.
- pytest para pruebas y Ruff para calidad estática/formato.
- Docker Compose para un entorno local reproducible.
- GitHub Actions para ejecutar comprobaciones automáticas.

Las herramientas se confirmarán al construir la primera versión ejecutable. El stack puede cambiar si una prueba técnica demuestra una alternativa mejor.

Consulta [docs/ARQUITECTURA.md](docs/ARQUITECTURA.md) y la decisión inicial [docs/decisions/ADR-001-architecture.md](docs/decisions/ADR-001-architecture.md).

## Cómo revisar el proyecto

Para un entrevistador o revisor técnico, sugiero este recorrido:

1. Leer [docs/REQUISITOS.md](docs/REQUISITOS.md) para entender el alcance y los criterios de aceptación.
2. Consultar [docs/PLAN-APRENDIZAJE.md](docs/PLAN-APRENDIZAJE.md) para ver el progreso por etapas y qué aprendizaje valida cada una.
3. Revisar [docs/MAPA-CV-EVIDENCIAS.md](docs/MAPA-CV-EVIDENCIAS.md) para relacionar competencias con pruebas concretas.
4. Abrir los issues, commits y pull requests vinculados a cada reto.
5. Seguir las instrucciones de ejecución y correr las pruebas cuando la etapa implementada las incluya.

Cada etapa completada debe indicar cómo reproducir su resultado. No se marcará una competencia como demostrada solo por mencionarla en este README.

## Estado de desarrollo

- [x] Definir el propósito, las secciones y el enfoque de aprendizaje.
- [x] Preparar la documentación inicial de requisitos y arquitectura.
- [x] Crear una plantilla para registrar aprendizajes y evidencias.
- [ ] Implementar la base ejecutable de la API.
- [ ] Conectar PostgreSQL y crear la primera migración.
- [ ] Entregar el primer caso de uso con pruebas.
- [ ] Publicar una demo reproducible de las funcionalidades implementadas.

## Desarrollo local

Todavía no existe una API funcional que ejecutar. Las instrucciones de instalación se añadirán y verificarán durante la **Etapa 1 — Esqueleto ejecutable**. No presentes los comandos como validados hasta que estén probados en un entorno limpio.

## Licencia

FraterChrist utiliza **GNU General Public License v3.0 (GPL-3.0-only)**. Consulta [LICENSE](LICENSE) y verifica la compatibilidad de cualquier dependencia, traducción bíblica, imagen o recurso externo que se incorpore.

## Contribuir

Lee [CONTRIBUTING.md](CONTRIBUTING.md). Se priorizan cambios pequeños, explicables, probados y documentados. Las contribuciones deben respetar la privacidad, la seguridad y el propósito comunitario del proyecto.
