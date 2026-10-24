# Requisitos del MVP

**Estado:** requisitos iniciales propuestos; sujetos a ajuste antes de codificar cada caso.

## Objetivo

Permitir que un usuario registrado publique un mensaje breve y responda a una publicación existente, con datos persistidos en PostgreSQL y un conjunto de métricas reproducibles construido solo con datos sintéticos.

## Requisitos funcionales

| ID | Requisito | Criterio de aceptación inicial |
|---|---|---|
| RF-01 | Registro | Un usuario puede registrarse con datos válidos; un correo normalizado no se registra dos veces. |
| RF-02 | Inicio de sesión | Una cuenta válida puede autenticarse; una contraseña incorrecta produce un error controlado sin revelar información innecesaria. |
| RF-03 | Crear publicación | Un usuario autenticado puede publicar texto dentro del límite definido; entradas vacías o demasiado largas se rechazan. |
| RF-04 | Consultar feed | La API devuelve publicaciones raíz en orden cronológico y con paginación limitada. |
| RF-05 | Responder | Un usuario autenticado puede responder a una publicación existente; una referencia inexistente se maneja con un error apropiado. |
| RF-06 | Consultar hilo | La API permite consultar las respuestas asociadas a una publicación. |
| RF-07 | Autoría y permisos | Las operaciones protegidas requieren identidad autenticada y no permiten acciones no autorizadas. |
| RF-08 | Persistencia | Los datos sobreviven al reinicio de la API y el esquema se puede crear con migraciones. |
| RF-09 | Calidad automática | Las pruebas y Ruff se ejecutan localmente y mediante GitHub Actions. |
| RF-10 | Análisis de datos | Un informe o notebook usa datos sintéticos y responde una pregunta analítica explícita con SQL/pandas. |

## Requisitos no funcionales

- **Seguridad:** contraseñas con hash seguro, secretos fuera del repositorio, validación, autorización y manejo prudente de errores.
- **Mantenibilidad:** módulos pequeños con responsabilidades entendibles; evitar abstracciones sin necesidad demostrada.
- **Reproducibilidad:** instrucciones probadas para preparar la base, aplicar migraciones, ejecutar pruebas y generar el análisis.
- **Calidad:** pruebas de casos válidos e inválidos para reglas importantes; formato y análisis estático automáticos.
- **Privacidad:** datos sintéticos únicamente para desarrollo, pruebas, notebooks y demostraciones.
- **Accesibilidad básica (fase 2):** formularios con etiquetas, mensajes comprensibles y navegación esencial con teclado.

## Límites explícitos del MVP

No incluye chat en tiempo real, reacciones, seguidores, perfiles extensos, multimedia, recomendaciones, IA integrada, moderación automatizada, aplicación móvil ni despliegue para producción. No se promete alta disponibilidad, escalabilidad de gran volumen ni cumplimiento de requisitos regulatorios de una plataforma operativa.

## Criterios de aceptación de la entrega

1. Una persona puede seguir la guía desde un entorno limpio.
2. Las migraciones construyen el esquema sin intervención manual no documentada.
3. Los tests cubren el flujo básico y los fallos relevantes y pasan.
4. La documentación distingue claramente entre funcionalidad implementada y planificada.
5. El análisis de datos define sus métricas, fuente sintética y limitaciones.