# Plan de análisis de datos

**Estado:** plan; no hay todavía datos ni resultados analíticos generados por la aplicación.

## Pregunta inicial

¿Cómo cambia el volumen de publicaciones por día y qué proporción de publicaciones raíz recibe al menos una respuesta?

La pregunta está deliberadamente limitada: permite practicar SQL, agregaciones, fechas y pandas sin construir un sistema de analítica complejo.

## Datos

El conjunto de trabajo se generará con datos sintéticos. Debe incluir un intervalo temporal pequeño, usuarios ficticios, publicaciones raíz y respuestas relacionadas por identificadores. La generación debe ser reproducible con una semilla configurada.

No importar listas de correos reales, exportaciones de redes sociales ni datos personales de congregaciones o personas.

## Métricas propuestas

- **Publicaciones raíz por día:** número de publicaciones con `parent_post_id IS NULL`, agrupadas por fecha.
- **Respuestas por día:** número de publicaciones con `parent_post_id IS NOT NULL`, agrupadas por fecha.
- **Proporción de publicaciones con respuestas:** publicaciones raíz que tienen una o más respuestas divididas por el total de publicaciones raíz del período. Si el denominador es cero, reportar el resultado como no definido, no como cero.
- **Tamaño de hilo:** número de respuestas asociadas a cada publicación raíz.

Cada métrica deberá documentar su definición, consulta SQL, período y limitaciones. Evitar presentar métricas de ejemplo como comportamiento de usuarios reales.

## Entregable mínimo

Un notebook o informe breve con:

1. Pregunta analítica y motivación.
2. Descripción del conjunto sintético y cómo reproducirlo.
3. Consultas SQL que producen las métricas.
4. Limpieza o transformación con pandas solo cuando sea necesaria.
5. Una visualización sencilla si mejora la respuesta.
6. Dos o tres conclusiones limitadas a los datos generados y una sección de limitaciones.

No añadir Power BI, Tableau ni una colección de dashboards hasta que el análisis sencillo sea correcto y explicable. Un dashboard podrá ser una extensión posterior si responde una pregunta adicional concreta.