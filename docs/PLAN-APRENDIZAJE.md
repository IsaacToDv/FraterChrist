# Plan de aprendizaje y evidencias — FraterChrist

## Cómo usar este plan

FraterChrist se construye aprendiendo mediante entregables pequeños. **GitHub Issues es la unidad de trabajo**: cada Issue debe resolver un problema, enseñar un concepto útil y dejar evidencia comprobable.

- Trabaja en **un Issue principal a la vez**. Puedes tener uno pequeño de diseño en paralelo si no bloquea el aprendizaje.
- Prioriza el MVP del Feed; la Zona doctrinal, Mesa, Kit y notificaciones quedan fuera hasta validar el primer flujo.
- No conviertas cada tema de teoría en una Issue. Abre una cuando exista un resultado útil para el producto o un experimento delimitado.
- Los laboratorios (por ejemplo, consola Python) sirven para practicar; no deben introducir código temporal en producción sin una razón.
- El orden del backlog es orientativo y las dependencias de cada Issue mandan.

## Flujo de trabajo

1. Escoge el Issue prioritario y lee sus criterios de aceptación.
2. Investiga solo lo necesario para avanzar. Anota conceptos que no entiendas.
3. Divide el trabajo si no puedes explicar o comprobar el resultado en una sesión razonable.
4. Implementa una parte pequeña; usa una rama con nombre descriptivo.
5. Ejecuta las pruebas y verifica también errores y entradas inválidas.
6. Abre un Pull Request enlazando el Issue; explica cambios, pruebas, aprendizaje y límites.
7. Cierra el Issue únicamente cuando los criterios estén satisfechos y la evidencia sea reproducible.

## Plantilla de aprendizaje para cada reto

- **Problema y resultado esperado:** ¿qué necesidad resuelvo?
- **Concepto principal:** ¿qué estoy aprendiendo?
- **Alcance y exclusiones:** ¿qué no voy a construir todavía?
- **Criterios de aceptación:** comportamientos verificables.
- **Evidencia:** archivos, pruebas, comandos, commit/PR, diagrama o prototipo.
- **Comprensión:** ¿puedo explicar el código y justificar las decisiones sin depender de una respuesta generada?
- **Revisión:** error que resolví, ayuda consultada, cómo verifiqué la solución y riesgo pendiente.
- **Cierre:** instrucciones reproducibles, pruebas ejecutadas, enlaces actualizados y ningún secreto publicado.

No hace falta rellenar todos los apartados con párrafos largos: escribe solo lo necesario para dejar claro el resultado.

## Orden inicial de Issues

### Etapa 1 — Aprender y preparar la base
1. [Issue #1: Validar una publicación desde consola con Python](https://github.com/IsaacToDv/FraterChrist/issues/1)
2. [Issue #2: Preparar el esqueleto de FastAPI con endpoint /health](https://github.com/IsaacToDv/FraterChrist/issues/2)
3. [Issue #3: Modelar una publicación y sus validaciones en Python](https://github.com/IsaacToDv/FraterChrist/issues/3)
4. [Issue #4: Prototipar en Figma el flujo mínimo del Feed](https://github.com/IsaacToDv/FraterChrist/issues/4) — puede avanzar en paralelo.

### Etapa 2 — Decisiones y datos
5. [Issue #5: Decidir autenticación y permisos mínimos del MVP](https://github.com/IsaacToDv/FraterChrist/issues/5)
6. [Issue #6: Diseñar el modelo de PostgreSQL y las migraciones iniciales](https://github.com/IsaacToDv/FraterChrist/issues/6)

### Etapa 3 — Primer flujo funcional
7. [Issue #7: Implementar identidad y acceso básico](https://github.com/IsaacToDv/FraterChrist/issues/7)
8. [Issue #8: Crear y consultar publicaciones mediante FastAPI y PostgreSQL](https://github.com/IsaacToDv/FraterChrist/issues/8)
9. [Issue #9: Conectar la interfaz mínima del Feed con la API](https://github.com/IsaacToDv/FraterChrist/issues/9)
10. [Issue #10: Implementar respuestas y consulta de hilos](https://github.com/IsaacToDv/FraterChrist/issues/10)

### Etapa 4 — Calidad y demostración
11. [Issue #11: Ejecutar pruebas y Ruff automáticamente en GitHub Actions](https://github.com/IsaacToDv/FraterChrist/issues/11)
12. [Issue #12: Documentar una demo reproducible del Feed MVP](https://github.com/IsaacToDv/FraterChrist/issues/12)

Los números identifican Issues, no una obligación de ejecutarlos estrictamente en ese orden. Lee las dependencias antes de empezar.

## Qué queda fuera del primer MVP

- Zona doctrinal, Mesa, Kit y newsletters.
- Chats en tiempo real, microservicios, caché, colas y recomendaciones.
- OAuth 2.0, inicio de sesión social u otros flujos avanzados sin una necesidad definida.
- Optimización prematura. Mide antes de añadir índices o infraestructura adicional.

## Regla de avance

No basta con que funcione en mi máquina. Antes de dar una etapa por terminada, debo poder explicar la solución, demostrar las pruebas y reproducir el resultado siguiendo la documentación. Una biblioteca utilizada o código generado por IA no demuestra por sí solo dominio técnico.
