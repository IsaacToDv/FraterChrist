# Arquitectura propuesta

**Estado:** propuesta de diseño; no describe componentes implementados.

## Decisión principal

Comenzar con un **monolito modular pequeño**. Una sola API y una base de datos son suficientes para el objetivo de aprendizaje. No se necesitan microservicios, colas, caché ni infraestructura distribuida para este MVP.

## Vista lógica

```text
Fase 1
Cliente de prueba (Swagger / Postman)
               |
               v
         FastAPI / HTTP
               |
               v
     Esquemas y validación
          (Pydantic)
               |
               v
       Lógica de aplicación
               |
               v
     SQLAlchemy / consultas
               |
               v
          PostgreSQL

Fase 2
Interfaz React + TypeScript
               |
          API HTTP/JSON
               v
      La misma API FastAPI
```

## Responsabilidad de las partes

- **Rutas FastAPI:** reciben peticiones HTTP, validan entradas mediante esquemas y entregan respuestas con códigos apropiados.
- **Esquemas Pydantic:** definen las entradas y salidas públicas de la API; no sustituyen las restricciones de la base de datos.
- **Lógica de aplicación:** concentra reglas como longitud de publicación, relación de respuestas y permisos.
- **Persistencia:** SQLAlchemy y PostgreSQL guardan usuarios y publicaciones. Alembic versiona los cambios estructurales.
- **Pruebas:** pytest cubre reglas de dominio y API. Los datos de prueba son sintéticos.
- **Análisis:** consultas SQL producen métricas definidas; pandas puede explorar y presentar los resultados en un notebook acotado.
- **Interfaz (fase 2):** consume la API pública; no accede directamente a PostgreSQL.

La separación debe mantenerse simple. Crear una capa o archivo nuevo solo cuando aclare una responsabilidad real.

## Modelo de datos inicial propuesto

### `users`

- `id`: clave primaria.
- `display_name`: nombre visible, con longitud limitada.
- `email`: identificador de inicio de sesión, único y normalizado.
- `password_hash`: hash de contraseña, nunca la contraseña original.
- `created_at`: fecha de creación.
- `is_active`: indicador básico de estado.

### `posts`

- `id`: clave primaria.
- `author_id`: clave foránea hacia `users.id`.
- `parent_post_id`: referencia opcional a otra publicación; nulo para una publicación raíz y no nulo para una respuesta.
- `content`: texto de longitud limitada.
- `created_at` y `updated_at`: fechas de auditoría básicas.

Este diseño permite un feed cronológico y respuestas con un modelo más pequeño que una tabla distinta por tipo de mensaje. Los detalles de integridad, borrado y límites de profundidad deben quedar definidos en los requisitos antes de implementar.

## API objetivo del MVP

Los paths son orientativos hasta completar la implementación:

- `GET /health`: comprobar que la API responde.
- `POST /auth/register`: registrar una cuenta.
- `POST /auth/login`: autenticar una cuenta.
- `GET /posts`: listar publicaciones raíz de forma paginada.
- `POST /posts`: crear una publicación raíz autenticada.
- `GET /posts/{post_id}/replies`: consultar respuestas de un hilo.
- `POST /posts/{post_id}/replies`: responder a una publicación con permisos adecuados.

No son endpoints existentes. Deben implementarse, documentarse y probarse antes de presentarlos como funcionales.

## Seguridad mínima desde la fase 1

- Almacenar contraseñas con un algoritmo de hash dedicado y una configuración apropiada; nunca cifrado reversible ni texto plano.
- Guardar secretos en variables de entorno locales ignoradas por Git; incluir únicamente valores de ejemplo no sensibles.
- Validar longitud y contenido de entradas, usar consultas parametrizadas/ORM y limitar paginación.
- Comprobar la identidad y autorización en las operaciones protegidas.
- No registrar contraseñas, tokens ni contenido sensible en logs.
- Ejecutar pruebas de entradas inválidas y accesos no autorizados.

La revisión de la fase 2 profundiza estos controles; no reemplaza la seguridad básica del MVP.

## Entorno reproducible

Docker Compose podrá levantar PostgreSQL para desarrollo. Las migraciones deben ser la forma documentada de construir el esquema; no depender de cambios manuales en una base local. La aplicación no debe declararse lista mientras no exista una guía verificada de instalación, migración, ejecución y pruebas.