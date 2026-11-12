# Guion de 90 minutos — orden de prioridad

Framework de decisión para la sesión. No es una checklist: usa cada
herramienta cuando aporte a la decisión, y no la uses si no aporta. La
capacidad de selección es parte de lo que se evalúa.

## Qué estás demostrando (capacidades de Principal PM)

Cada fase y cada entregable debe servir para evidenciar al menos una de estas
cinco capacidades. La presentación es el vehículo, no el objetivo:

| Capacidad | Qué evidencia en la sesión |
| --------- | -------------------------- |
| **Customer understanding** | Sabes cómo trabaja realmente el equipo financiero: workflow, workaround, excepciones. |
| **Product judgment** | Identificas qué problema merece resolverse, refinas el encuadre y distingues síntoma de causa raíz. |
| **Business thinking** | Conectas valor para el usuario con retención, expansión y eficiencia (cadena producto → cliente → negocio). |
| **Technical awareness** | Entiendes implicaciones de integraciones, datos, fiabilidad y escalabilidad sin sustituir a ingeniería. |
| **Strategic prioritization** | Decides qué construir ahora, qué después y qué evidencia necesitas para avanzar, parar o pivotar. |

**Regla de oro:** un Principal PM demuestra seniority cuando sabe qué NO
necesita construir todavía y qué pregunta hay que responder antes de decidir.

## Timeline

> **Formato real de la entrevista:** Alex presenta el caso en directo y tú le
> preguntas antes de preparar la propuesta. La fase 1 (Problem Discovery) es
> entonces **diálogo activo de ~12–25 min** (20–30% del total); las fases 2–6
> se condensan en el tiempo restante. Los timeboxes de abajo son orientativos
> para el flujo completo de 90 min.

| # | Fase | Tiempo | Prioridad |
| - | ---- | ------ | --------- |
| 1 | Problem Discovery | 0–20 | Crítica |
| 2 | Strategic Fit | 20–30 | Crítica |
| 3 | Solution & Prioritization | 30–50 | Crítica |
| 4 | Success Metrics | 50–60 | Alta |
| 5 | Roadmap | 60–70 | Alta |
| 6 | Validation, Economics & Risks | 70–80 | Según caso |
| 7 | Executive Summary & Discussion | 80–90 | Crítica |

**Dimensiones transversales:** Competitors, Moat y Economics **no son una fase
cerrada**: se investigan cuando afectan a una decisión concreta (sobre todo en
las fases 2, 3 y 6). Si un competidor ya resuelve bien el problema, la
oportunidad puede ser mejorar experiencia o coste; si el coste por transacción
es alto, cambia el modelo de automatización. Si no condicionan la decisión,
no fuerces su inclusión.

**Documento de trabajo:** durante la sesión usa `/notes` como documento único
vivo. Los entregables separados se generan al cierre (ver fase 7).

---

## 1. Problem Discovery (0–20 min; en formato live, 12–25 min de diálogo)

**Objetivo:** identificar el problema real, el usuario afectado y el impacto.

**Cómo preguntar en el formato live:** prioriza usuario y proceso As-Is, un
ejemplo real reciente, frecuencia e impacto, causa raíz con evidencia y
restricciones; no propongas features hasta entender el problema.

**Primera pregunta, antes de profundizar:**
> "What's the business context behind this case, and why is it a priority
> right now?"
> (En español: ¿cuál es el contexto de negocio y por qué es prioritario ahora?)

### Preguntas clave

**Contexto y urgencia**
- ¿Por qué abordamos este problema ahora?
- ¿Lo han pedido los clientes directamente o lo hemos identificado internamente?

**Usuario**
- ¿Quién sufre el problema? ¿CFO, Treasurer, Finance Manager, Accountant?
- ¿Quién usa la funcionalidad? ¿Quién decide la compra?
- ¿Tipo y tamaño de empresa? ¿General o de un segmento?

**Problema**
- ¿Cuál es el workflow actual (As-Is)? ¿Qué partes son manuales?
- ¿Cómo lo resuelven hoy (workaround)?
- ¿Dónde están los errores, retrasos o fricciones? ¿Con qué frecuencia?
- ¿Cuáles son las principales **excepciones** del workflow?
- ¿Qué ocurre en el escenario ideal y en el peor escenario?
- ¿Causa raíz: tecnología, datos, procesos, integraciones o UX?

**Impacto**
- ¿Cuánto tiempo/dinero cuesta al cliente? ¿Qué % de operaciones afecta?
- ¿Hay datos, feedback o evidencias? ¿Afecta a retención/adopción?

### Tareas
1. Mapear workflow As-Is.
2. Separar síntomas de causas raíz.
3. Cuantificar frecuencia e impacto.
4. **Identificar qué información falta para confirmar la causa raíz.**
5. Clasificar en Facts / Hypotheses / Open questions.
6. Redactar el Problem Statement.

**Resultado:** problem statement concreto (plantilla:
`frameworks/problem-statement.md`).

---

## 2. Strategic Fit (20–30 min)

**Objetivo:** por qué importa para Embat y qué apuesta representa.

### Preguntas clave
- ¿Qué papel juega Payments & Banking en la estrategia de Embat?
- ¿Qué objetivos de negocio persigue esta iniciativa?
- ¿Es estratégica, demanda recurrente de clientes o necesidad competitiva?
- ¿Qué otras iniciativas compiten por los mismos recursos?
- ¿Qué ventaja o capacidad existente de Embat podemos aprovechar?
- ¿Qué tendría que ser cierto para que esta apuesta tenga éxito?
- ¿Qué pasaría si no resolvemos este problema?
- Pregunta potente para priorizar:
  > "If we could only solve one part of this problem, which part would create
  > the most strategic value for Embat?"

### Tareas
1. Formular la apuesta (The Bet).
2. Hipótesis principales que la sostienen (qué tendría que ser cierto).
3. Por qué es el momento adecuado.

**Resultado:** apuesta estratégica conectada con objetivos de negocio.

---

## 3. Solution & Prioritization (30–50 min)

**Objetivo:** transformar la estrategia en una solución concreta con alcance MVP.

**Antes de elegir solución, fijar el resultado objetivo:**
> "What outcome would make us consider this initiative successful?"
> (El resultado esperado condiciona qué funcionalidades priorizar.)

### Preguntas clave
- ¿Qué alternativas de solución hay (2–3)?
- ¿Qué podemos resolver con capacidades existentes de la plataforma?
- ¿Automatizar por completo o mantener intervención humana?
  ¿Qué riesgos operativos aparecen si automatizamos completamente?
- ¿Qué debería poder hacer el usuario cuando la automatización falla?
  (Crítico en productos financieros: diseñar excepciones y recuperación,
  no solo el happy path.)
- ¿Qué solución da mayor valor con menor complejidad?
- ¿Qué es imprescindible para el MVP? ¿Qué queda fuera?
- ¿Qué segmento la prueba primero? ¿Qué dependencias hay?

### Stakeholders & Dependencies
- ¿Qué equipos deben participar (eng, producto, compliance, ops, ventas)?
- ¿Dependemos de bancos, proveedores externos o APIs de terceros?
- ¿Quién valida los requisitos de compliance?
- ¿Qué áreas podrían bloquear o condicionar el lanzamiento?
- ¿Qué decisiones necesitan alineamiento de otros equipos?

### Tareas
1. Diseñar workflow To-Be (incluido el fallback cuando algo falla).
2. Generar 2–3 alternativas y compararlas (valor, coste, complejidad, riesgo).
3. Seleccionar la recomendada con justificación.
4. Priorizar MVP (MoSCoW o Value vs. Effort).
5. Criterios de aceptación + out-of-scope explícito.

**Resultado:** solución recomendada + alcance MVP.

**Frase para verbalizar:**
> "I would rather deliver a smaller solution that solves the core customer
> problem reliably than a broader solution that introduces unnecessary
> complexity."

---

## 4. Success Metrics (50–60 min)

**Objetivo:** concretar cómo medir el resultado fijado en la fase 3.

### Preguntas clave
- ¿Cómo medimos hoy el proceso? ¿Qué baseline tenemos?
- ¿Qué indicadores demostrarían que hemos logrado el resultado objetivo?
- ¿Cómo medimos adopción? ¿Distinguimos uso de impacto real?
- ¿Qué métricas de fiabilidad monitorizamos?

### Criterio de flexibilidad
- 1 métrica principal de éxito + 2–4 KPIs complementarios (no todas las
  dimensiones).
- Si Alex no da baseline: identificar el dato necesario para obtenerlo.
- Objetivos iniciales como **hipótesis**, no compromisos arbitrarios.

**Resultado:** métrica principal + KPIs con baseline o plan para obtenerla
(plantilla: `frameworks/metrics.md`).

---

## 5. Roadmap (60–70 min)

**Objetivo:** explicar cómo evolucionaría la solución. No hace falta un
roadmap detallado.

### Preguntas clave
- ¿Qué dependencias deben resolverse antes de cada fase?
- ¿Qué aprendizaje o resultado permitirá pasar de Now a Next?
- ¿Qué funcionalidades no deberíamos desarrollar hasta tener evidencia de
  adopción?
- ¿Criterios para escalar, pivotar o parar?
- ¿Encaje con el resto del roadmap de Payments & Banking?

### Estructura Now / Next / Later
- **NOW — Prove the value:** resolver el problema prioritario para un segmento y validar.
- **NEXT — Improve and expand:** automatizar más, cubrir más casos, incorporar feedback.
- **LATER — Scale and differentiate:** ampliar cobertura y reforzar la ventaja.

**Resultado:** roadmap por resultados con gates de evidencia
(plantilla: `frameworks/roadmap.md`).

---

## 6. Validation, Economics & Risks (70–80 min, según caso)

Revisión transversal: solo lo que condicione la decisión.

### Qué revisar
- Coste de desarrollo y mantenimiento; costes de terceros y procesamiento.
- Viabilidad técnica y operativa.
- Riesgos de seguridad, compliance y fiabilidad.
- Alternativas competitivas y diferenciación (ver `research/competitors.md`).
- Implicaciones de pricing y monetización (ver modelo de Embat en
  `research/embat-product.md`).

**No intentes calcular un business case financiero completo en 10 minutos.**

### ¿Prototipo o no? (ver `frameworks/prototype-decision.md`)

- **Plan A (por defecto):** recomendación argumentada, con un wireframe o
  flujo sencillo si aporta claridad.
- **Plan B (si sobra tiempo y aporta valor):** demo mínima de una sola
  interacción (con opencode: `/demo` genera un mock HTML estático).
- Antes de construir, verbalizar:
  > "I could spend the remaining time building a small prototype, but before
  > doing that, I'd like to make sure we're aligned on the problem, the
  > proposed solution and what we want to validate. I don't want to optimize
  > for building something quickly if we're not solving the right problem."

---

## 7. Executive Summary & Discussion (80–90 min)

Genera `output/06-resumen-ejecutivo.md` (comando `/summary`) y preséntalo
compartiendo pantalla. Debes poder responder en 2 minutos:

1. ¿Qué problema resolvemos y para quién es prioritario?
2. ¿Por qué importa para Embat?
3. ¿Qué oportunidad identificamos (The Bet)?
4. ¿Qué solución recomiendo y por qué?
5. ¿Qué incluye el MVP y qué queda fuera?
6. ¿Principales riesgos?
7. ¿Cómo mediremos el éxito?
8. ¿Qué validamos a continuación?
9. **Open questions & assumptions:** qué sé, qué asumo y qué necesito validar.

Los entregables separados (`/problem`, `/mvp`, `/roadmap`, `/metrics`) se
generan al cierre si sobra tiempo; durante la sesión el documento vivo es
`templates/notes.md` vía `/notes`.

---

## Comportamientos a demostrar toda la sesión

| Comportamiento      | Qué demuestra                                            |
| ------------------- | -------------------------------------------------------- |
| Active listening    | Usar la información que da Alex                          |
| Structured thinking | Organizar la información y explicar el razonamiento      |
| Critical thinking   | Cuestionar hipótesis y detectar contradicciones          |
| Prioritization      | Distinguir lo importante de lo secundario                |
| Adaptability        | Cambiar de opinión con nueva información                 |
| Communication       | Explicar decisiones y trade-offs                         |
| Ownership           | Recomendar una dirección, aunque haya incertidumbre      |
| Pragmatism          | Saber cuándo hay suficiente información para avanzar     |

## Recordatorio final

El objetivo no es demostrar que sabes aplicar un framework de Product
Management, sino que sabes **cuándo usar cada herramienta y cuándo no**. Lo
que Alex debe recordar al terminar: entiendes el negocio, identificaste el
problema correcto y tuviste criterio para decidir qué construir.
