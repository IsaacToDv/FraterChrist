# ADR-001: Monolito modular

- **Estado:** Aceptado provisionalmente.
- **Contexto:** desarrollo incremental por una persona y recursos limitados.
- **Decisión:** separar dominios en módulos dentro de una aplicación desplegable.
- **Consecuencias positivas:** despliegue y depuración sencillos, pruebas locales y bajo costo inicial.
- **Consecuencias negativas:** requiere disciplina para evitar dependencias cruzadas; podría necesitar separación futura.
- **Revisión:** reconsiderar solo ante una necesidad concreta de escalado, aislamiento o despliegue independiente.