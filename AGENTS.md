# AGENTS.md — Instrucciones para los agentes de opencode

## Contexto

Este repo es un kit de preparación para un business case de **Principal Product
Manager en Embat** (TMS de tesorería: conectividad bancaria/ERP, cash
management, pagos a proveedores, conciliación y vuelcado al ERP).

Durante la sesión de 90 minutos el usuario trabaja en directo: toma notas en
`templates/notes.md` y genera entregables en `output/` con los comandos de
`.opencode/command/`.

## Reglas para los agentes

- **Idioma**: todo el contenido se escribe en español. Excepciones: términos PM
  estándar (Problem Statement, North Star Metric, MVP) y frases que el usuario
  quiera verbalizar en inglés.
- **Rapidez sobre exhaustividad**: en una sesión de 90 min, un entregable
  correcto en 3 minutos vale más que uno perfecto en 10. Sé conciso.
- **Decisiones, no ensayos académicos**: si el caso no necesita análisis de
  competidores o pricing, no los fuerces. Usa el orden de prioridad del guion:
  Problem Discovery → Strategic Fit → Solution → Metrics → Roadmap.
- **Siempre separar**: Facts (confirmados), Hypotheses (por validar) y Open
  questions (pendientes). No mezclarlos en los entregables.
- **Basarse en las notas del usuario** (`templates/notes.md`): no inventar datos
  del caso que no estén ahí. Si falta información clave, listarla como open
  question.
- **Conocimiento de dominio**: consultar `research/` (producto Embat,
  competidores, glosario de tesorería) antes de redactar soluciones para usar
  terminología correcta (pain.001, camt.053, EBICS, H2H, conciliación
  bidireccional ERP…).
- **Los entregables se escriben en `output/`** con el número de fase como
  prefijo (01-…, 02-…, etc.), nunca fuera de esa carpeta.
- **Documento vivo durante la sesión**: el usuario trabaja sobre
  `templates/notes.md`. No le hagas generar entregables separados a mitad de
  sesión; los comandos `/problem`, `/mvp`, `/roadmap`, `/metrics` son para el
  cierre o si el usuario los pide explícitamente. `/summary` es el único
  obligatorio al final. `/present` genera el deck HTML de cierre, `/runall`
  ejecuta la secuencia completa (02→06 + deck) y `/reset confirmar` vacía
  notas y `output/` para empezar de cero.
- **Prototipo**: solo si el caso lo pide o el usuario lo decide con
  `frameworks/prototype-decision.md`. `/demo` genera un único mock HTML
  estático en `output/demo.html` (sin dependencias externas, datos ficticios).
- **Build y plan**: build genera entregables; si el usuario pide retar una
  decisión (/retame), haz de abogado del diablo con preguntas de criterio, no
  con listas de teoría.

## Juicio de producto y disciplina de evidencia

El objetivo no es producir un documento completo ni una presentación bonita:
es demostrar criterio de producto bajo incertidumbre. Aplica esto toda la
sesión:

1. **Entender antes de resolver**: no propongas features hasta entender
   usuario, problema, workflow e impacto. En una sesión de 90 min, si la
   información no llega, márcalo y avanza — no bloquees la decisión.
2. **Separar evidencia de supuestos**: distingue siempre Facts, Hypotheses,
   Open questions. Los datos de `research/` son contexto y claims comerciales:
   nunca los trates como hechos del caso.
3. **Cuestionar el encuadre**: la descripción inicial del problema puede estar
   incompleta o sesgada; refórmulalo cuando la evidencia lo justifique.
4. **Preguntar lo que cambia decisiones**: no preguntes por completitud, sino
   por lo que alteraría problema, priorización o solución.
5. **Considerar alternativas**: mejorar capacidad existente, cambiar proceso,
   integrar un tercero o construir — antes de elegir construir.
6. **Evitar falsa precisión**: no inventes baselines, objetivos, costes,
   capacidades técnicas ni fechas. Etiqueta estimaciones e hipótesis.
7. **Recomendación condicional**: di qué evidencia validaría, cambiaría o
   invalidaría la recomendación ("recomiendo X si Y").

> La presentación es el resultado de las decisiones, no el objetivo del
> proceso. Vale más una recomendación corta y defendible que un documento
> exhaustivo sin sustento.
