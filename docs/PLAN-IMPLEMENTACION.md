# Plan de implementación — Core Feed

Cada etapa debe terminar con código ejecutable y verificaciones observables. El alcance es texto, autenticación, visibilidad pública/privada y respuestas simples.

## Orden principal

1. **[Issue #20 — Fundación técnica](https://github.com/IsaacToDv/FraterChrist/issues/20)**  
   Inicializar Django + DRF, PostgreSQL, variables de entorno, endpoint de salud e instrucciones reproducibles. Este es el punto de partida.

2. **[Issue #21 — Modelos](https://github.com/IsaacToDv/FraterChrist/issues/21)**  
   Modelar usuario Django, publicaciones de texto, visibilidad y respuestas directas. Crear migraciones, registrar en Django Admin y probar las relaciones.

3. **[Issue #22 — Autenticación y permisos](https://github.com/IsaacToDv/FraterChrist/issues/22)**  
   Registro, sesión y CSRF; aplicar reglas de lectura y autoría en el servidor.

4. **[Issue #23 — API REST](https://github.com/IsaacToDv/FraterChrist/issues/23)**  
   Crear, listar, consultar, editar y eliminar publicaciones; crear y listar respuestas. Mantener el feed raíz en orden cronológico y paginado.

5. **[Issue #25 — Frontend mínimo](https://github.com/IsaacToDv/FraterChrist/issues/25)**  
   Conectar React/TypeScript a la API y completar registro, login, feed, publicación y respuesta sin diseño visual avanzado.

6. **[Issue #26 — Pruebas y CI](https://github.com/IsaacToDv/FraterChrist/issues/26)**  
   Consolidar pruebas del Core, comprobaciones de estilo y GitHub Actions. Escribir pruebas desde el inicio, junto a cada función.

7. **[Issue #27 — Demo y evidencia](https://github.com/IsaacToDv/FraterChrist/issues/27)**  
   Documentar ejecución, decisiones y límites; grabar una demostración real y reproducible.

## Fase de expansión — no bloquea el Core

- **[Issue #24 — Fotos, videos y acceso protegido a archivos](https://github.com/IsaacToDv/FraterChrist/issues/24).**
- **Visibilidad para miembros:** issue de expansión enlazada desde el [listado de issues](https://github.com/IsaacToDv/FraterChrist/issues).
- Perfiles avanzados, likes, seguidores, mensajería, recomendaciones, salas, videollamadas, pizarras y juegos.

## Criterio de progreso

No marques una tarea como terminada por haber creado archivos o escrito documentación. Debe ejecutarse, cumplir sus criterios de aceptación y tener pruebas o evidencia adecuada. Mantén commits pequeños, con un propósito claro y mensajes descriptivos.
