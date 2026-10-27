# Lesson 1 — let Claude read your repo

## Mi predicción (de memoria, antes de pedir el resumen)

Cambié el mensaje de uso de `add` en `notes.js`, añadí una función `count()` en `lib/store.js` y puse un comentario al final de `README.md`.

## Resumen de Claude

Pregunta: *"Summarize what I've changed, and flag anything that looks unintended."*

Resumen generado por Claude a partir de `git diff` (cambios sin commitear en `notes.js`, `lib/store.js`, `lib/config.js`):

- **`notes.js`**: el mensaje de uso del comando `add` pasó de `<your note>` a `<text of your note>`. Cambio de texto, sin efecto en la lógica.
- **`lib/store.js`**: función nueva `count()` que devuelve `load().notes.length`, añadida a `module.exports`. Es aditiva y nadie la usa todavía.
- **`lib/config.js`**: `SESSION_TIMEOUT_MINUTES` pasó de `15` a `5`.

**Marcado como posiblemente no intencional:** el cambio en `lib/config.js`. Es el único que altera comportamiento: el bloqueo de sesión por inactividad baja de 15 a 5 minutos, y `notes.js` imprime ese valor en el mensaje de ayuda. No encaja con los otros dos cambios (texto de usuario y un helper nuevo) y es el tipo de edición que se cuela por accidente.

## Reflexión

Claude sí detectó el cambio perdido: señaló `lib/config.js` como el sospechoso, explicó por qué (es el único con efecto en comportamiento) y no lo mezcló con los cambios triviales. Mi predicción de memoria lo omitía, así que la comparación predicción vs. resumen mostró justo la diferencia que el ejercicio busca. Para ser honestos: `node` no está instalado en este equipo, así que no se ejecutó `scripts/check.js` ni la app; el resumen se basa solo en leer el diff.
