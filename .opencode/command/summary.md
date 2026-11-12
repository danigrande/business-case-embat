---
description: Genera el resumen ejecutivo final en output/06-resumen-ejecutivo.md
agent: build
---

Genera el resumen ejecutivo final del business case de Embat.

1. Lee `templates/notes.md`, `templates/decision-log.md` y los entregables
   previos en `output/` (si existen) y `frameworks/exec-summary.md`.
2. Input adicional del usuario: $ARGUMENTS.
3. Redacta en español los 8 puntos del framework:
   problema → por qué importa → oportunidad (The Bet) → solución recomendada
   → MVP (incluido y fuera) → riesgos → métricas → próximos pasos.
4. Revisa coherencia: cada punto conecta con el anterior; decisiones con
   trade-offs; cerrado con siguiente paso accionable.
5. Escribe en `output/06-resumen-ejecutivo.md`. Debe poder presentarse en
   2 minutos.
