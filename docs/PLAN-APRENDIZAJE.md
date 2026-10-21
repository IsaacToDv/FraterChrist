# Plan de aprendizaje y evidencias — FraterChrist

## Propósito
Construir FraterChrist por incrementos que demuestren competencias para prácticas: backend, APIs REST, SQL/PostgreSQL, calidad, seguridad y mantenibilidad. Cada reto termina con código o documentación, pruebas y una explicación reproducible. Aceptar código de IA no equivale a demostrar aprendizaje.

## Plantilla reutilizable por reto
- **Reto / estado / fecha:** Pendiente, En curso, Bloqueado o Completado; AAAA-MM-DD.
- **Issue / rama / PR:**
- **Competencia del CV:**
- **Problema y alcance:** necesidad, usuario, resultado observable y exclusiones.
- **Aprendizaje:** concepto principal, secundarios, qué puedo explicar sin ayuda y decisión técnica que puedo justificar.
- **Criterios de aceptación:** comportamiento comprobable, entradas inválidas, permisos, documentación y pruebas.
- **Evidencia:** archivos, commit/PR, comandos y resultados, esquema/endpoint/diagrama, demo si aporta valor.
- **Revisión crítica:** qué resolví, qué consulté, cómo verifiqué sugerencias, error encontrado y riesgo pendiente.
- **Preguntas de entrevista:** por qué este diseño, qué alternativa evalué, cómo sé que funciona, qué ocurre ante fallos y qué mejoraría.
- **Cierre:** puedo explicar el código; es reproducible; hay enlaces; no publiqué secretos; actualicé el estado.

## Hoja de ruta

### Etapa 0 — Repositorio y requisitos
**Objetivo:** punto de partida claro.
**Aprendizaje:** Git/GitHub, Markdown técnico, licencia, requisitos, alcance y decisiones arquitectónicas.
**Evidencia:** README, requisitos, arquitectura, plantilla y commits de documentación.

### Etapa 1 — Python y API mínima
**Objetivo:** aplicación FastAPI ejecutable con endpoint de salud.
**Aprendizaje:** entorno virtual, módulos, configuración por variables de entorno, HTTP, rutas, esquemas y OpenAPI.
**Evidencia:** instrucciones probadas desde entorno limpio, /health, lint y prueba automatizada.

### Etapa 2 — Dominio y POO
**Objetivo:** modelar un caso pequeño, como crear un borrador de publicación, antes de añadir persistencia.
**Aprendizaje:** responsabilidades, separación de reglas y HTTP, tipos y errores explícitos.
**Evidencia:** módulo probado con casos válidos e inválidos.

### Etapa 3 — PostgreSQL y modelo relacional
**Objetivo:** persistir un recurso con esquema y migraciones.
**Aprendizaje:** claves, relaciones, restricciones, transacciones, SQL y migraciones.
**Evidencia:** diagrama ER, migración, consultas y pruebas de integración.

### Etapa 4 — CRUD mediante API REST
**Objetivo:** crear, consultar, actualizar y eliminar publicaciones.
**Aprendizaje:** métodos HTTP, códigos, Pydantic, serialización, capas, paginación y errores.
**Evidencia:** contrato, ejemplos, pruebas y OpenAPI.

### Etapa 5 — Seguridad y permisos
**Objetivo:** proteger operaciones según identidad y propiedad.
**Aprendizaje:** secretos, autenticación mantenida, autorización en servidor y pruebas negativas.
**Evidencia:** matriz de permisos y pruebas de acceso permitido/denegado. No implementar criptografía propia.

### Etapa 6 — Feed con hilos
**Objetivo:** respuestas a publicaciones.
**Aprendizaje:** relaciones uno-a-muchos, integridad, ordenamiento, paginación y pruebas.
**Evidencia:** flujo ejecutable y casos límite.

### Etapa 7 — Zona doctrinal
**Objetivo:** preguntas, respuestas, etiquetas y recursos.
**Aprendizaje:** reutilización, filtros, relaciones y licencias de recursos.
**Evidencia:** endpoints, modelo, filtros probados y reglas documentadas.

### Etapa 8 — Mesa y Kit
**Objetivo:** espacios colaborativos y notas personales.
**Aprendizaje:** membresías, roles, permisos y privacidad.
**Evidencia:** pruebas de aislamiento entre usuarios.

### Etapa 9 — Notificaciones y entrega
**Objetivo:** correo y demo reproducible.
**Aprendizaje:** consentimiento, preferencias, baja, fallos, pruebas y CI.
**Evidencia:** GitHub Actions, pruebas, vídeo y guía de ejecución.

## Regla para avanzar
No basta con que funcione en mi máquina. Antes de cerrar una etapa debo explicar las decisiones, ejecutar pruebas y reproducir el resultado siguiendo la documentación.