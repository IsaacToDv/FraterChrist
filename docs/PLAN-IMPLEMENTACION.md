# Plan de implementación

Este plan define el trabajo del MVP personal de FraterChrist. Cada etapa debe terminar con código verificable y, cuando corresponda, pruebas que demuestren su comportamiento.

## 1. Entorno y backend

**Issue #20**

Preparar Python, Django, Django REST Framework y PostgreSQL. Documentar la configuración local y crear una base de proyecto que pueda arrancar de forma reproducible.

## 2. Modelos

**Issue #21**

Definir los modelos de usuario, publicación y archivo; crear las migraciones y reflejar las tres reglas de visibilidad. El modelo de usuario debe definirse antes de la primera migración.

## 3. Autenticación y permisos

**Issue #22**

Implementar inicio de sesión y las reglas de acceso para visitantes, miembros y autores. Verificar las decisiones en el backend con pruebas para cada tipo de usuario.

## 4. API del Feed

**Issue #23**

Crear y listar publicaciones, consultar respuestas y responder directamente a una publicación raíz. Añadir paginación y errores claros.

## 5. Fotos y videos

**Issue #24**

Validar los archivos, guardarlos en almacenamiento privado y comprobar los permisos antes de servirlos. Mantener el binario fuera de PostgreSQL.

## 6. Interfaz web

**Issue #25**

Crear la interfaz mínima con React, TypeScript y Vite. Conectar la lectura del feed, autenticación, publicación y respuestas; representar estados de carga, vacío y error.

## 7. Calidad

**Issue #26**

Automatizar pruebas de API y los flujos básicos de interfaz. Añadir Ruff y GitHub Actions para detectar errores y regresiones.

## 8. Demostración de portafolio

**Issue #27**

Documentar instalación, decisiones principales, limitaciones y evidencia real del funcionamiento. Añadir capturas o una demo breve únicamente cuando los flujos estén implementados y comprobados.

## Evidencia que dejará el proyecto

- Código organizado y comprensible.
- Esquema de datos y decisiones de arquitectura documentados.
- Pruebas que cubran comportamiento y permisos.
- Instrucciones reproducibles y demo verificable.
- Lista explícita de limitaciones y funciones futuras.

Este plan describe objetivos de implementación; no afirma que el MVP ya esté terminado.
