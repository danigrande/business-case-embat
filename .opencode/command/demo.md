---
description: Genera un mock HTML estático de una pantalla clave en output/demo.html
agent: build
---

Genera un prototipo estático de UNA pantalla clave de la solución.

1. Lee `templates/notes.md` (problem statement, solution/MVP),
   `frameworks/prototype-decision.md` y `research/embat-brand.md`.
2. Input adicional del usuario: $ARGUMENTS (qué pantalla construir; si no lo
   dice, elige la interacción más representativa del MVP).
3. Crea `output/demo.html`: un único archivo HTML estático, sin dependencias
   externas (CSS inline, sin JS externo, sin fuentes remotas), datos
   ficticios, textos en español.
4. **Estilo:** copia el contenido de `templates/embat-theme.css` dentro de una
   etiqueta `<style>` (la fuente Haffer va embebida). Usa el look & feel de
   embat.io: tema claro, navy `#050B2C`, gradiente de marca, tarjetas 12px,
   chips pill. Si la pantalla es la bandeja de excepciones, usa el componente
   `.mock` del theme y amplíalo con detalle.
5. Candidatos típicos en el dominio: dashboard de cash position/forecast,
   pantalla de conciliación (matching + excepciones), flujo de aprobación de
   pagos, bandeja de excepciones de pago.
6. Al terminar, resume en 2 líneas: qué pantalla es, qué problema ilustra y
   qué interacción muestra. No modifiques otros archivos.
