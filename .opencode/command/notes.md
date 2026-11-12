---
description: Actualiza el documento vivo de notas (templates/notes.md)
agent: build
---

Actualiza el documento vivo de la sesión: `templates/notes.md`.

1. Lee `templates/notes.md`.
2. Con el input del usuario ($ARGUMENTS), actualiza las secciones que
   correspondan, sin borrar contenido previo salvo que el usuario lo pida:
   - Contexto y urgencia
   - Facts (confirmados) / Hypotheses (por validar) / Open questions
   - Problem statement (borrador)
   - Outcome target (qué resultado = éxito)
   - The Bet
   - Solution / MVP (alternativas, recomendada, in/out)
   - Stakeholders & dependencies
   - Risks
   - Metrics
   - Roadmap (Now / Next / Later)
   - Decision log (decisión / justificación / incertidumbre)
3. Reglas: español; siempre separar Facts/Hypotheses/Open questions; no
   inventar datos del caso (lo que falte va a Open questions); conciso
   (listas cortas, frases directas). No generar archivos nuevos en output/.
