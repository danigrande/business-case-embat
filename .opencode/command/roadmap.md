---
description: Genera el roadmap Now/Next/Later en output/04-roadmap.md
agent: build
---

Genera el roadmap del business case de Embat.

1. Lee `templates/notes.md` y `frameworks/roadmap.md`.
2. Input adicional del usuario: $ARGUMENTS.
3. Redacta en español una tabla Now / Next / Later con:
   - Objetivo de resultado por horizonte (no solo features).
   - Qué se entrega en cada horizonte.
   - Hitos de validación medibles.
4. Añade criterios go/pivot/kill concretos (umbrales, si los sabes; si no,
   propónlos como hipótesis).
5. Escribe en `output/04-roadmap.md`. Ordena respetando dependencias
   (datos → validación → automatización).
