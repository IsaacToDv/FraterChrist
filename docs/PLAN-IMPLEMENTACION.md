# Plan de implementación — Core Feed

Cada etapa debe terminar con código ejecutable y verificaciones observables. El alcance es texto, autenticación, visibilidad pública/privada y respuestas simples.

## Orden principal

1. **[#20 — Fundación técnica](https://github.com/IsaacToDv/FraterChrist/issues/20):** inicializar Django + DRF, PostgreSQL, variables de entorno y endpoint de salud.
2. **[#21 — Modelos](https://github.com/IsaacToDv/FraterChrist/issues/21):** usuario Django, publicaciones de texto, visibilidad, respuestas directas, migraciones y Django Admin.
3. **[#22 — Autenticación y permisos](https://github.com/IsaacToDv/FraterChrist/issues/22):** registro, sesiones, CSRF y autorización en el backend.
4. **[#23 — API REST](https://github.com/IsaacToDv/FraterChrist/issues/23):** crear, listar, consultar, editar y eliminar publicaciones; crear y listar respuestas.
5. **[#25 — Frontend mínimo](https://github.com/IsaacToDv/FraterChrist/issues/25):** conectar React/TypeScript y completar registro, login, feed, publicación y respuesta.
6. **[#26 — Pruebas y CI](https://github.com/IsaacToDv/FraterChrist/issues/26):** consolidar pruebas, comprobaciones de estilo y GitHub Actions. Las pruebas se escriben desde el inicio.
7. **[#27 — Demo y evidencia](https://github.com/IsaacToDv/FraterChrist/issues/27):** documentar la instalación, mostrar una demo real y registrar limitaciones.

## Fase de expansión — no bloquea el Core

- [#24 — Fotos, videos y acceso protegido a archivos](https://github.com/IsaacToDv/FraterChrist/issues/24).
- [#28 — Visibilidad para miembros](https://github.com/IsaacToDv/FraterChrist/issues/28).
- Perfiles avanzados, likes, seguidores, mensajería, recomendaciones, salas, videollamadas, pizarras y juegos.

## Criterio de progreso

No cierres una tarea solo por crear archivos o documentar una idea. Comprueba el comportamiento, ejecuta las pruebas relevantes y mantén commits pequeños con mensajes descriptivos.
