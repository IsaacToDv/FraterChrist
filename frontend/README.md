# Frontend

Frontend previsto: React, TypeScript y Vite. Su objetivo es consumir la API REST del Core Feed, no sustituir sus controles de seguridad.

## Alcance mínimo

- Registro, inicio y cierre de sesión.
- Feed cronológico de publicaciones visibles.
- Formulario de publicación de texto con visibilidad pública/privada.
- Respuestas simples a publicaciones raíz.
- Estados de carga, vacío, validación y error.

La autenticación se hará con sesión de Django y protección CSRF. Configura el proxy de desarrollo de Vite cuando se implemente la interfaz.

Consulta la [Issue #25](https://github.com/IsaacToDv/FraterChrist/issues/25), los [requisitos](../docs/REQUISITOS.md) y la [arquitectura](../docs/ARQUITECTURA.md).

**Estado:** esta carpeta todavía no contiene una interfaz implementada.
