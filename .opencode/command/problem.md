---
description: Genera el Problem Statement en output/02-problem-statement.md
agent: build
---

Genera el Problem Statement del business case de Embat.

1. Lee `templates/notes.md` y el framework `frameworks/problem-statement.md`.
2. Input adicional del usuario: $ARGUMENTS.
3. Redacta en español siguiendo el framework (3 niveles):
   - Problem statement en 1–3 frases (nivel 3), con versión en inglés lista
     para verbalizar y su nivel de confianza (alta/media/baja).
   - Tabla de Problem framing (usuario afectado, comprador, stakeholders,
     contexto, tarea/workflow As-Is, workaround, fricción, frecuencia y
     severidad, outcome deseado).
   - Evidencia: qué sabemos y qué falta por comprobar; causa raíz solo si hay
     evidencia, si no como hipótesis.
   - Facts / Hypotheses / Open questions separados.
   - Impacto cuantificado solo si hay dato; si no, marcado como hipótesis.
4. Escribe en `output/02-problem-statement.md`. No inventes datos del caso;
   lo que falte, a open questions. El statement es provisional y puede
   evolucionar en la sesión.
