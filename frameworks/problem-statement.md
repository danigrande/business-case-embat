# Framework — Problem Statement

> **El problem statement es provisional y evoluciona durante la sesión.**
> No rellenes campos que no conoces: lo que falte va a Open questions o se
> marca como hipótesis. Inventar datos aquí contamina todo lo demás.

## Nivel 1 — Problem framing (sin presuponer causa ni solución)

| Campo | Respuesta |
| ----- | --------- |
| **Usuario afectado** | ¿Quién sufre el problema? (Treasurer, AP, Contable…) |
| **Comprador / decisor** | ¿Quién decide la compra? (puede no ser el usuario) |
| **Otros stakeholders** | CS, soporte, compliance, IT del cliente… |
| **Contexto** | Tipo de empresa, entidades, bancos, volumen |
| **Tarea / workflow As-Is** | ¿Qué hace hoy, paso a paso? ¿Qué es manual? |
| **Workaround** | ¿Cómo lo resuelve hoy (Excel, portales, soporte)? |
| **Fricción observada** | ¿Qué se observa? (errores, retrasos, fricción) |
| **Frecuencia y severidad** | ¿Cada cuánto? ¿A quién le duele más? (si no hay dato: open question) |
| **Outcome deseado** | ¿Qué debería mejorar para el cliente, sin mencionar solución? |

## Nivel 2 — Evidence (qué sabemos y qué falta)

- **Qué sabemos** y qué evidencia lo respalda (datos de Alex, casos, tickets).
- **Qué falta por comprobar** para confirmar causa raíz, frecuencia e impacto.
- **Causa raíz**: solo se afirma con evidencia suficiente. Antes, es hipótesis.
  Distingue síntoma (pagos fallidos sin explicación) de causa (datos/estados
  incompletos, integración, UX, proceso).

## Nivel 3 — Problem statement (provisional)

> **[Segmento/usuario]** en **[situación/contexto]** tarda **[X, si se conoce]**
> en **[tarea]** de forma **[manual/poco fiable]** a causa de **[causa raíz, si
> hay evidencia]**, lo que provoca **[impacto cuantificado o cualitativo]**.

- **Nivel de confianza:** (alta / media / baja) según la evidencia del nivel 2.
- Si la causa raíz o el impacto no están confirmados, escríbelo como hipótesis:
  "la causa más probable es…, por confirmar con…".

### Clasificación

- **Facts:** (confirmados por Alex)
- **Hypotheses:** (por validar)
- **Open questions:** (pendientes de preguntar)

## Checklist de calidad

- [ ] Concreto (usuario, tarea, contexto), no genérico.
- [ ] Distingue síntoma de causa raíz (y dice si esta está confirmada o no).
- [ ] Impacto acotado; cuantificación solo si hay dato, si no marcada como hipótesis.
- [ ] Sin solución todavía (no dice "falta de feature X").
- [ ] Basado en Facts de las notas; lo dudoso va a Hypotheses/Open questions.
- [ ] Identifica qué información falta y qué pregunta la resolvería.
