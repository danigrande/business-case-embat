---
description: Genera la solución y el alcance MVP en output/03-solucion-mvp.md
agent: build
---

Genera el entregable de solución y MVP del business case de Embat.

1. Lee `templates/notes.md` y `frameworks/solution-mvp.md`.
2. Revisa `research/` (producto Embat, glosario) para usar terminología
   correcta (pain.001, camt.053, EBICS, H2H, conciliación bidireccional ERP).
3. Input adicional del usuario: $ARGUMENTS.
4. Redacta en español:
   - Value hypothesis (comportamiento a cambiar, resultado esperado, por qué,
     evidencia).
    - Evaluación build/buy/improve/process antes de decidir construir.
    - Viabilidad técnica y economía operativa: reutilización, dependencias,
      coste operativo, fiabilidad, build/buy y **esfuerzo relativo del MVP
      (bajo/medio/alto, como hipótesis a validar con engineering) con lo que
      se desplaza por capacidad**.
    - Workflow To-Be en 5–8 pasos (marcar automático vs. humano + fallback).
    - 2–3 alternativas comparadas (valor, coste/complejidad, riesgo) y una
      recomendada con justificación y qué evidencia la validaría o cambiaría.
    - MVP con MoSCoW (Must/Should/Could/Won't) y segmento piloto, especificando
      qué incertidumbre resuelve el MVP y aclarando que "Won't" es por
      capacidad/riesgo/secuencia, no por falta de valor.
   - 5–6 criterios de aceptación (dado/cuando/entonces).
   - Dependencias y riesgos con mitigación (técnica, datos, compliance) y
     failure scenarios (sin datos, banco no responde, error operativo, audit
     trail).
   - Out-of-scope explícito.
5. Escribe en `output/03-solucion-mvp.md`. Si el usuario no ha tomado una
   decisión, recomiéndala tú y márcala como recomendación pendiente de validar.
