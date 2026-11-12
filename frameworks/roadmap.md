# Framework — Roadmap (Now / Next / Later)

Roadmap orientado a **evidencia y decisiones**, no a una lista de features con
fechas.

## Plantilla

| Horizonte | Pregunta a responder | Objetivo | Qué entregamos | Hito de validación |
| --------- | -------------------- | -------- | -------------- | ------------------ |
| **NOW** — Validar problema y viabilidad | ¿Merece la pena construirlo? | Confirmar el problema, su tamaño y la viabilidad técnica | Instrumentación, discovery, MVP mínimo | Métrica objetivo del piloto |
| **NEXT** — Validar solución y adopción | ¿Resuelve el problema de forma efectiva? | Demostrar impacto y adopción en el segmento | Ampliar cobertura, cerrar el ciclo, automatizar | Gate de adopción e impacto |
| **LATER** — Escalar y diferenciar | ¿Podemos ampliar el valor de forma rentable? | Prevenir, automatizar y reforzar la ventaja | Prevención, auto-reintento, scorecards | Gate de escala |

**Horizontes temporales:** 0–3 / 3–6 / 6–12 meses son solo orientativos; no
comprometer fechas si aún desconoces dependencias técnicas, bancarias o
comerciales. Prioriza la secuencia de dependencias: datos → validación →
automatización.

**Esfuerzo y coste de oportunidad:** cada horizonte debe indicar el esfuerzo
relativo (bajo/medio/alto, como hipótesis a validar con engineering) y qué
compite por capacidad. La secuencia **no es decisión exclusiva de la feature**:
se ajusta con engineering y con las prioridades del resto del roadmap. Los
gates son además **checkpoints de retorno**: no se escala sin beneficio
demostrado.

Frase para verbalizar: *"mi secuencia asume X capacidad y que no hay una
prioridad mayor que no esté viendo; si la hay, el orden cambia."*

**Evolución condicional:** las capacidades avanzadas se prometen como
evolución condicionada, no como siguiente paso garantizado. Patrón genérico:

> Una vez que tengamos datos fiables de [resultado] y entendamos los patrones
> principales, podremos explorar [capacidad avanzada]. Empezaría por reglas
> deterministas y evolucionaría hacia capacidades predictivas solo si el
> histórico demuestra suficiente valor predictivo.

Esto comunica ambición sin prometer lo que aún no está justificado.

## Preguntas que debe responder

1. ¿Qué validamos antes de invertir en la solución completa?
2. ¿Qué capacidades deben existir antes de lanzar el MVP?
3. ¿Qué dependencias condicionan el orden?
4. ¿Qué aprenderemos de los primeros clientes?
5. ¿Criterios para escalar, pivotar o parar?
6. **¿Qué tendría que ser cierto para que NO continuásemos con esta
   iniciativa?** (criterio de kill explícito = asignar recursos con criterio)
7. ¿Encaje con el resto del roadmap de Payments & Banking?

## Criterios de decisión (go/kill/pivot)

- Go si: [umbral de adopción/resultado] en [tiempo].
- Pivot si: [señal concreta].
- Kill si: [señal concreta].

Los umbrales se proponen como hipótesis si no hay baseline; se fijan con datos
al cierre de NOW.

## Checklist de calidad

- [ ] Cada horizonte tiene una pregunta a responder y un objetivo de
      resultado, no solo features
- [ ] El orden respeta dependencias (datos → validación → automatización)
- [ ] Hay hitos de validación medibles
- [ ] Incluye criterios para escalar o parar (incluido qué nos haría NO continuar)
- [ ] Sin compromisos de fechas hasta conocer dependencias
- [ ] Esfuerzo relativo por horizonte y coste de oportunidad señalados
      (hipótesis a validar con engineering)
