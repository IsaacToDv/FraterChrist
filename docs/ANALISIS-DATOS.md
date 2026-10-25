# Análisis de datos — etapa posterior al MVP

Este documento describe una posible extensión, no un requisito para la primera entrega. El MVP se concentra en el Feed, los permisos y los archivos multimedia.

## Pregunta inicial propuesta

¿Cómo varía el volumen diario de publicaciones y qué proporción de publicaciones raíz recibe respuestas?

## Datos

Cuando haya un modelo estable, se podrá generar un conjunto de prueba con datos sintéticos. No se deben importar correos reales, exportaciones de redes sociales ni datos personales.

## Métricas candidatas

- Publicaciones raíz por día.
- Respuestas por día.
- Número de respuestas por hilo.
- Proporción de publicaciones raíz que reciben una o más respuestas.

Las consultas pueden escribirse primero en SQL y analizarse después con pandas solo si aporta valor. Cada métrica deberá incluir su definición, consulta y limitaciones.

No añadir un notebook, un dashboard ni una herramienta adicional de análisis hasta que el MVP esté terminado y exista una pregunta concreta que lo justifique.