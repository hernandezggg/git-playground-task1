# Predicciones

- Mañana el CI pasará a la primera (confianza: baja).
- Alguien olvidará hacer `git pull` antes de empezar a trabajar y tendrá un conflicto de merge.
- Este repo seguirá siendo un sandbox: ninguna de estas predicciones afectará producción.
- En seis meses `notes.js` tendrá más tests que líneas de código.

## Resumen de Claude (qué cambió y qué parece no intencional)

Pregunta: *"Summarize what I've changed, and flag anything that looks unintended."*

Resumen generado por Claude a partir del diff del commit `6967840`:

- **`README.md`** (modificado, +2 líneas): se añadió una línea en blanco y un comentario HTML al final del archivo: `<!-- el café sabe mejor cuando el merge no tiene conflictos -->`. No afecta al contenido renderizado ni al código de la app.
- **`notes.md`** (nuevo, +6 líneas): lista de cuatro predicciones.
- **Nada tocado en el código de la app**: `notes.js`, `lib/` y `scripts/` no tienen cambios.
- **Posible cambio no intencional:** ninguno que afecte al comportamiento. Lo único fuera de `notes.md` es el comentario en `README.md`, un archivo distinto al de las predicciones. Es inocuo pero no tiene relación con la funcionalidad, así que es el único candidato a "cambio perdido".

## Reflexión

Claude sí detectó el cambio "extra": señaló el comentario en `README.md` como el único cambio fuera de `notes.md` y lo clasificó como inocuo. Aun así, hay que ser honestos con el alcance: en este ejercicio no hubo ninguna edición accidental en código, así que Claude no tuvo que cazar un cambio sutil en `lib/` o `notes.js`, y la prueba de si detecta uno es débil. Además, mi predicción no mencionaba el comentario del README, por lo que la comparación predicción vs. resumen sí mostró una diferencia real.
