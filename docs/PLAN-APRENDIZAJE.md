# Plan de aprendizaje de FraterChrist

## Propósito

Aprender construyendo un único proyecto, con entregables pequeños y comprobables. La prioridad no es terminar una red social completa rápidamente, sino entender cada pieza, probarla y documentar cómo se reproduce.

## Ritmo y planificación

La rutina actual planteada es de **2 horas al día, 5 días por semana (aproximadamente 10 horas semanales)**. El PDF visual conservado en este repositorio refleja una versión anterior del plan de 1 hora al día y 5 horas por semana. Por eso, las duraciones del PDF son orientativas y no deben tomarse como fechas prometidas. Avanzar según los criterios de salida, no por calendario.

## Fase 1 — Backend y datos reproducibles

### Nodo 1. Requisitos y Python base

**Aprender:** variables y tipos, condicionales, bucles, funciones, estructuras de datos, clases y validación de entradas.

**Entregable:** función que valide una publicación desde consola y un modelo sencillo de publicación, con casos válidos e inválidos.

**Criterio de salida:** explicar la función línea por línea y demostrar sus reglas con pruebas manuales y automatizadas.

### Nodo 2. Pruebas y hábitos de Git

**Aprender:** pytest básico, organización simple del código, commits pequeños, ramas y lectura de errores.

**Entregable:** pruebas automatizadas de las reglas de publicación y README con los comandos para ejecutarlas.

**Criterio de salida:** las pruebas pasan en un entorno limpio y el autor entiende por qué fallaría cada caso inválido.

### Nodo 3. SQL y PostgreSQL

**Aprender:** SELECT, INSERT, UPDATE, DELETE, filtros, JOIN, agrupaciones, claves foráneas, índices y transacciones; luego SQLAlchemy y Alembic.

**Entregable:** modelo inicial para usuarios y publicaciones con respuestas; migraciones y consultas SQL documentadas.

**Criterio de salida:** se puede crear la base desde cero con migraciones y ejecutar consultas reproducibles sin depender de datos reales.

### Nodo 4. API REST con FastAPI

**Aprender:** HTTP, métodos, códigos de respuesta, diseño REST, validación con Pydantic y documentación OpenAPI.

**Entregable:** endpoint `/health` y endpoint para validar una publicación. Documentar y probar las peticiones desde `/docs` y/o Postman.

**Criterio de salida:** explicar qué problema resuelve cada endpoint, sus entradas, respuestas y errores previsibles.

### Nodo 5. Backend mínimo del feed

**Aprender:** conectar API y PostgreSQL, registro e inicio de sesión, hash seguro de contraseñas, autorización básica, manejo de errores y pruebas de API.

**Entregable:** crear y listar publicaciones y responder a una publicación desde la API; mantener la autoría y los permisos mínimos.

**Criterio de salida:** probar flujos correctos e incorrectos, verificar permisos y no guardar secretos en el repositorio.

### Nodo 6. Calidad, datos y demo

**Aprender:** Ruff, GitHub Actions, datos sintéticos con Faker, consultas SQL analíticas y pandas.

**Entregable:** workflow de pruebas y análisis; conjunto de datos sintéticos documentado; notebook o informe breve que responda una pregunta sobre actividad del feed; guía de demo reproducible.

**Pregunta analítica inicial sugerida:** ¿cómo cambia el volumen de publicaciones por día y qué proporción de publicaciones recibe respuestas?

**Criterio de salida:** otra persona puede repetir las pruebas y el análisis; cada métrica tiene definición y consulta o código trazable; las conclusiones no se presentan como datos reales.

## Fase 2 — Interfaz y seguridad aplicada

### Nodo 7. Interfaz mínima

**Aprender:** HTML/CSS necesarios, JavaScript, TypeScript, React, Vite y consumo de APIs con `fetch`.

**Entregable:** pantalla sencilla para consultar el feed, crear una publicación y responder a un hilo a través de la API existente.

**Criterio de salida:** los flujos esenciales funcionan y los casos clave están probados con Vitest. No construir un diseño grande antes de conectar el flujo real.

### Nodo 8. Revisión de seguridad y entrega

**Aprender:** controles básicos de OWASP, validación, autorización, gestión de secretos y logs sin información sensible.

**Entregable:** lista de comprobación de seguridad aplicada al código existente, hallazgos corregidos dentro del alcance y pasos de ejecución desde cero.

**Criterio de salida:** revisar entradas inválidas, accesos no autorizados, errores y exposición accidental de secretos; documentar limitaciones pendientes.

## Práctica transversal semanal

- Reservar tiempo para leer documentación y escribir breves notas con palabras propias.
- Realizar commits pequeños que representen cambios entendibles.
- Usar la IA como apoyo para aclarar conceptos o revisar hipótesis, no como sustituto de entender el código.
- Ante un error, registrar síntoma, causa, solución y prueba que demuestra la corrección.
- No añadir módulos por moda: toda tarea debe contribuir a un criterio de aceptación del MVP.

## Fuera de alcance por ahora

Mensajería en tiempo real, likes, seguidores, subida de archivos, recomendaciones con IA, aplicación móvil, múltiples roles administrativos, microservicios y despliegue de producción. Solo reevaluarlos cuando el MVP y su análisis estén terminados y explicables.