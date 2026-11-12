---
description: Resetea el documento de notas y output/ para empezar el caso desde cero (requiere "confirmar")
agent: build
---

Restaura el kit de preparación a su estado inicial.

1. **Seguridad:** si $ARGUMENTS no contiene exactamente la palabra
   `confirmar`, no hagas nada y responde: "Para resetear escribe: /reset confirmar".
2. Con `confirmar`:
   - Reescribe `templates/notes.md` con EXACTAMENTE el contenido de plantilla
     que se incluye al final de este archivo (entre las líneas de `@@@`).
   - Reescribe `templates/decision-log.md` con su contenido de plantilla
     (también al final de este archivo).
   - Borra TODOS los archivos de `output/` EXCEPTO `.gitkeep`.
3. No borres nada fuera de `output/` y de esas dos plantillas. No toques
   `research/`, `frameworks/`, `guide/` ni `.opencode/`.
4. Al terminar, confirma en 2 líneas qué se ha borrado y qué se ha restaurado.

---
@@@
# Documento de trabajo — business case Embat (sesión de 90 min)

> **Un único documento vivo.** Captura solo lo que condiciona decisiones.
> Usa `/notes` para actualizarlo durante la sesión. Los entregables separados
> se generan al cierre.

## Contexto y urgencia

- Contexto de negocio del caso:
- ¿Por qué es prioritario ahora?
- ¿Petición de clientes o iniciativa interna?

## Facts — Información confirmada

- 

## Hypotheses — Suposiciones por validar

- 

## Open questions — Preguntas pendientes

- 

## Problem statement (borrador)

> 

## Outcome target — ¿Qué resultado nos haría considerarlo un éxito?

> 

## Strategic opportunity / The Bet

> 

## Recommended solution / MVP

- Alternativas consideradas:
- Recomendada (por qué):
- MVP (in / out):

## Stakeholders & dependencies

- Equipos a involucrar:
- Dependencias de bancos/APIs de terceros:
- Compliance / quién valida:
- Posibles bloqueos:

## Risks

- 

## Metrics

- Métrica principal:
- KPIs (2–4):
- Baseline (o dato necesario para obtenerlo):

## Roadmap (borrador Now / Next / Later)

- NOW:
- NEXT:
- LATER:

## Decision log

| Decisión | Justificación | Incertidumbre |
| -------- | ------------- | ------------- |
|          |               |               |

## Reloj

| Fase | Timebox | Hora inicio |
| ---- | ------- | ----------- |
| Problem Discovery | 0–20 | |
| Strategic Fit | 20–30 | |
| Solution & MVP | 30–50 | |
| Metrics | 50–60 | |
| Roadmap | 60–70 | |
| Validation & Risks | 70–80 | |
| Executive Summary | 80–90 | |
@@@

---
@@@
# Decision log — registro de decisiones

> Durante la sesión, el decision log vive dentro de `templates/notes.md`
> (documento único). Este archivo sirve para consolidarlo al cierre y para el
> executive summary.

| # | Decisión | Alternativas descartadas | Trade-off asumido | Justificación (1 línea) | Incertidumbre |
| - | -------- | ------------------------ | ----------------- | ----------------------- | ------------- |
| 1 |          |                          |                   |                         |               |
| 2 |          |                          |                   |                         |               |
| 3 |          |                          |                   |                         |               |

## Uso

- Anotar cada decisión importante: solución elegida, scope MVP, métricas,
  priorización.
- La columna **Incertidumbre** (alta/media/baja) muestra qué decisiones
  revisarías si Alex aporta información nueva — señal de adaptabilidad.
- Sirve para defender las decisiones en el Executive Summary y detectar
  contradicciones antes de presentar.
@@@
