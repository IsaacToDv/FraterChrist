# Guía de desarrollo del MVP

Esta guía organiza el trabajo técnico en el mismo orden que las [Issues #20–#27](https://github.com/IsaacToDv/FraterChrist/issues). El objetivo es construir una entrega pequeña y reproducible antes de ampliar el producto.

## 1. Base técnica

**Issue #20**

Preparar Python, Django, Django REST Framework y PostgreSQL. Definir el modelo de usuario antes de la primera migración y documentar cómo ejecutar el proyecto en desarrollo.

## 2. Modelos y permisos

**Issues #21–#22**

Modelar usuarios, publicaciones, respuestas y adjuntos. Implementar los niveles de visibilidad: público, limitado a miembros y privado. Validar los permisos en la API, incluidas las lecturas de medios.

## 3. Feed y archivos

**Issues #23–#24**

Implementar listado cronológico, creación de publicaciones y respuestas. Añadir carga de fotos y videos con validación de tipo y tamaño y almacenamiento fuera de PostgreSQL.

## 4. Interfaz web

**Issue #25**

Crear la interfaz mínima con React, TypeScript y Vite. Conectar el Feed a la API, implementar los flujos principales y mostrar estados de carga, vacío y error.

## 5. Calidad y entrega

**Issues #26–#27**

Añadir pruebas automatizadas para los flujos y permisos, ejecutar controles con Ruff y GitHub Actions y documentar una instalación repetible.

## Principios de trabajo

- Entregar cambios pequeños y verificables.
- Leer documentación oficial cuando se introduce una tecnología.
- Usar datos sintéticos; no subir secretos ni datos personales.
- Utilizar la IA como apoyo, no como sustituto de comprender y comprobar la solución.
- Mantener fuera del MVP los perfiles avanzados, las mesas, las videollamadas y los juegos educativos.

La guía se actualizará si cambia el alcance acordado del MVP.