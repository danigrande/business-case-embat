---
description: Ejecuta la secuencia completa de entregables (problem→mvp→roadmap→metrics→summary→present)
agent: build
---

Ejecuta en orden todos los entregables de cierre a partir de `templates/notes.md`.

1. Lee `templates/notes.md` una vez y mantenlo como fuente de verdad. No
   inventes datos del caso; lo que falte va a open questions o se marca como
   hipótesis.
2. Input adicional del usuario: $ARGUMENTS (permite excluir pasos, p. ej.
   "sin presentacion" o "sin roadmap"; si viene vacío, haz la secuencia completa).
3. Genera los entregables en este orden, aplicando las instrucciones de cada
   comando (lee `.opencode/command/<nombre>.md` y síguelas al pie de la letra):
   1. `output/02-problem-statement.md` (reglas de `.opencode/command/problem.md`)
   2. `output/03-solucion-mvp.md` (reglas de `.opencode/command/mvp.md`)
   3. `output/04-roadmap.md` (reglas de `.opencode/command/roadmap.md`)
   4. `output/05-metricas.md` (reglas de `.opencode/command/metrics.md`)
   5. `output/06-resumen-ejecutivo.md` (reglas de `.opencode/command/summary.md`)
   6. `output/presentacion.html` (reglas de `.opencode/command/present.md`)
4. Coherencia entre entregables: misma apuesta, misma solución recomendada,
   mismos umbrales de métricas y gates del roadmap, mismo alcance MVP.
5. Si un archivo anterior ya existe, regenéralo igualmente (el estado de
   `notes.md` manda). No borres otros archivos de `output/`.
6. Al terminar, resume en 3 líneas: qué archivos se generaron, qué decisión
   principal contienen y qué se presenta primero.
