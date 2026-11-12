# Framework — Solution & MVP

> La solución es una apuesta, no una conclusión. Antes de definir el MVP,
> justifica por qué esta apuesta y no otra.

## 0. Value hypothesis (antes de construir)

- ¿Qué comportamiento del usuario queremos cambiar?
- ¿Qué resultado esperamos conseguir para el cliente?
- ¿Por qué creemos que esta solución lo conseguirá?
- ¿Qué evidencia tenemos (y cuál es la incertidumbre principal)?

## 1. Build vs. buy vs. improve (evaluar antes de decidir construir)

En un TMS, la conectividad bancaria, los datos y las integraciones pueden
hacer que una solución "sencilla" sea muy costosa. Considerar por orden:

1. **Improve:** ¿una capacidad existente de Embat resuelve el 80% (p. ej.
   validación previa, estados de pago, ERP bidireccional)?
2. **Process:** ¿se resuelve cambiando el proceso o la experiencia, sin nueva
   tecnología?
3. **Buy/integrate:** ¿un tercero lo cubre mejor (API bancaria, proveedor de
   datos) con menos riesgo?
4. **Build:** construir solo lo que ninguna de las anteriores resuelve.

## 1.1 Viabilidad técnica y economía operativa (transversal)

Preguntas que toda solución financiera debe responder antes de comprometerse:

- **Technical feasibility:** ¿qué capacidades e integraciones existentes
  reutilizamos?
- **Bank / third-party dependencies:** ¿qué depende de cada proveedor (bancos,
  APIs) y de sus formatos, latencias o coberturas?
- **Operational cost:** ¿qué cuesta mantener y monitorizar estas integraciones
  a largo plazo (no solo construirlas)?
- **Reliability:** ¿cómo gestionamos información incompleta, duplicada,
  retrasada o incorrecta?
- **Build vs. buy:** ¿qué construir internamente y qué adquirir/integrar?
- **Esfuerzo relativo y capacidad:** ¿el MVP es bajo/medio/alto en sprints y
  equipos? Marcar como hipótesis a validar con engineering, y decir qué se
  desplaza por capacidad (coste de oportunidad).
- **Seguridad y auditabilidad:** si afecta a operaciones financieras, permisos,
  trazabilidad y auditoría desde el diseño, no como añadido.

> No es un análisis de arquitectura: son preguntas para detectar riesgos y
> costes que cambien la decisión. Las que no cambien nada, se omiten.

## 1.2 IA en la solución (si aplica)

Si la solución incluye IA o agentes:

- **Gate de evals obligatorio:** antes de lanzar, definir escenarios de
  validación con input congelado, decisión esperada (escalar / responder /
  actuar / cerrar) y **claims prohibidos** (lo que nunca puede decirse). El
  dataset se construye con casos reales donde antes se falló.
- **Human-in-the-loop por defecto:** la IA explica y sugiere; el humano decide
  y ejecuta. "Actuar sin permiso" es un fallo del sistema, no una opción.
- **Coste como hipótesis:** anclar el coste por operación y sus palancas
  (caching de contexto, herramientas acotadas por agente, consultas
  optimizadas) como hipótesis a validar, nunca como cifra inventada.
- **Métricas de calidad, no solo de uso:** exactitud sobre el dataset de
  evals, ratio de escalados y feedback humano como guardrails.

> Referencia de dominio (pública, no dato del caso): Embat mantiene agentes
> internos con evals por equipo, auto-escalado cuando fallan y coste por
> investigación de ~€0,70. Ver `research/embat-ai-engineering.md`.

## 2. Workflow To-Be (futuro)

```
[Entrada de datos] → [Validación] → [Procesado automático] → [Excepción humana]
     → [Salida/Asientos de vuelta]
```

Describir el flujo futuro en 5–8 pasos, marcando qué pasos son automáticos y
cuáles requieren intervención humana. Incluir el **fallback** (qué pasa cuando
el dato no llega o es incorrecto).

## 3. Alternativas de solución (2–3)

| Alternativa | Descripción (1 línea) | Valor | Coste/Complejidad | Riesgo |
| ----------- | --------------------- | ----- | ----------------- | ------ |
| A           |                       |       |                   |        |
| B           |                       |       |                   |        |
| C           |                       |       |                   |        |

**Recomendada:** [A/B/C] — justificación en 1–2 frases (mayor valor con menor
complejidad, reutiliza capacidad existente X…). Marcar qué evidencia la
validaría o la cambiaría.

## 4. MVP — Priorización (MoSCoW) + aprendizaje

| Must have | Should have | Could have | Won't have (ahora) |
| --------- | ----------- | ---------- | ------------------ |
|           |             |            |                    |

> La columna **Won't have (ahora)** no significa "sin valor": es **fuera por
> capacidad, riesgo o secuencia**. Explicitar qué se desplaza y por qué — es
> la decisión de coste de oportunidad del MVP.

**Segmento piloto:** ¿quién la prueba primero y por qué?

**MVP orientado a aprendizaje:** el MVP también debe especificar qué
incertidumbre resuelve:

| Elemento | Pregunta |
| -------- | -------- |
| Usuario piloto | ¿Con quién validamos? |
| Hipótesis | ¿Qué creemos que ocurrirá? |
| Experiencia mínima | ¿Qué necesita poder hacer el usuario? |
| Aprendizaje | ¿Qué queremos descubrir? |
| Criterio de éxito | ¿Qué resultado justifica continuar? |

## 4.1 Adopción y confianza

- ¿Cómo se integra la solución en el workflow actual del usuario, sin añadir
  otra pantalla o tarea manual?
- ¿Qué nivel de control mantiene el usuario sobre las acciones sugeridas?
- ¿Cómo explicamos las acciones recomendadas y su porqué?
- ¿Qué trazabilidad ofrecemos (quién hizo qué, cuándo, con qué resultado)?
- ¿Cómo gestionamos los casos en los que no podemos determinar la causa?
- ¿Cómo generamos confianza en la nueva experiencia durante las primeras
  semanas?

> En operaciones financieras, **no automatizar una acción cuando no hay
> certeza suficiente suele ser mejor producto que automatizarla mal**.

## 5. Criterios de aceptación

- Dado [situación], cuando [acción], entonces [resultado].
- (máx. 5–6 criterios medibles)

## 6. Dependencias, riesgos y failure scenarios

| Tipo | Dependencia/Riesgo | Mitigación |
| ---- | ------------------ | ---------- |
| Técnica |                 |            |
| Datos   |                 |            |
| Compliance/seguridad | |            |
| Operativa |               |            |

**Failure scenarios (crítico en pagos — fiabilidad y trazabilidad no son
detalles):**

- ¿Qué pasa cuando no hay datos o el banco no responde?
- ¿Qué pasa cuando la información bancaria es incorrecta o llega tarde?
- ¿Qué operaciones requieren intervención humana sí o sí?
- ¿Qué consecuencias tendría un error (doble pago, pago no ejecutado)?
- ¿Cómo se audita quién hizo qué y cuándo (audit trail)?

## 7. Out-of-scope explícito (para verbalizar)

- Queda fuera: …

## Frases a usar

> "I would rather deliver a smaller solution that solves the core customer
> problem reliably than a broader solution that introduces unnecessary
> complexity."

## Checklist de calidad

- [ ] La solución ataca la causa raíz del problem statement, no el síntoma
- [ ] Value hypothesis explícita (qué comportamiento y qué resultado)
- [ ] Se evaluó improve/process/buy antes de decidir build
- [ ] Viabilidad técnica y economía operativa revisadas (reutilización,
      dependencias, coste de operar, fiabilidad)
- [ ] Adopción y confianza: encaje en el workflow, control del usuario,
      trazabilidad y gestión de causas desconocidas
- [ ] Se reutilizan capacidades existentes de Embat (conectividad, TellMe,
      ERP bidireccional) antes de construir nuevas
- [ ] MVP = mínimo que resuelve el problema para un segmento concreto y
      responde una pregunta de aprendizaje
- [ ] Out-of-scope explícito
- [ ] Excepciones/fallos gestionados (qué pasa cuando algo falla)
- [ ] Si hay IA: gate de evals, human-in-the-loop y coste como hipótesis
