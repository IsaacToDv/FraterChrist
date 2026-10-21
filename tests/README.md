# Estrategia de pruebas

Las pruebas crecerán junto con la primera funcionalidad ejecutable. Cada reto debe definir cómo comprobar el comportamiento, incluidas entradas inválidas y errores relevantes.

- **Unitarias:** reglas de dominio aisladas.
- **Integración:** interacción con PostgreSQL y componentes reales.
- **API:** códigos HTTP, esquemas de petición/respuesta y errores.
- **Seguridad:** autorización y accesos denegados cuando exista identidad.
- **Extremo a extremo:** flujos completos cuando la aplicación alcance una etapa adecuada.

Los comandos se documentarán al crear el esqueleto ejecutable. No se afirmará que las pruebas pasan hasta ejecutarlas.