# Framework — Success Metrics

## North Star Metric

> **[Métrica única]** que refleja el valor entregado al cliente.
> Ej. "operaciones de tesorería procesadas automáticamente de extremo a
> extremo", "horas de cierre ahorradas por cliente".

**Regla de elección:**

> Choose the metric that best represents customer value delivered, not the
> metric that is easiest to track or most directly influenced by the feature.

Si dudas entre dos, pregúntate: ¿esta métrica mejoraría aunque el cliente no
notara nada? Si la respuesta es sí, no es la North Star.

## Cadena de valor producto → cliente → negocio

Antes de fijar KPIs, explicitar la cadena causal (como hipótesis, no como
resultado demostrado):

1. **Producto:** qué cambia para el usuario (p. ej. mayor visibilidad y
   resolución dentro de la plataforma).
2. **Cliente:** qué mejora en su trabajo (menos tiempo manual, menos
   incertidumbre, más confianza).
3. **Negocio:** qué produce para Embat (más adopción y volumen, mejor
   retención, menos coste de soporte por incidencia, diferenciación).

Cada eslabón necesita su métrica; si falta uno, la historia no se sostiene.

## Métricas por dimensión (elegir 3–5, no todas)

| Dimensión | Qué mide | Métrica ejemplo |
| --------- | -------- | --------------- |
| **Customer outcome** | ¿Mejora realmente el trabajo del cliente? | Horas manuales ahorradas por semana/cliente; TTR de incidencias |
| **Product adoption** | ¿Utiliza la solución? | % de clientes del segmento que usan la feature; volumen procesado en la plataforma |
| **Operational quality** | ¿Funciona de forma fiable? | Tasa de éxito; % de excepciones; errores por batch |
| **Business impact** | ¿Aporta valor económico a Embat? | Retención (renewal / GRR), expansión (volumen e ingresos), coste de soporte por incidencia |

**Sobre business impact:** son métricas **lagging** y dependen de más factores
que el producto (ventas, mercado, pricing). Distinguir:
- **Influenciables por el equipo:** adopción, volumen procesado, TTR, coste de
  soporte por incidencia.
- **Resultados de negocio:** GRR, expansión de ingresos. Se monitorizan y se
  conectan como hipótesis causal, no como compromisos directos del equipo.

## Reglas

1. **No fijar objetivos numéricos sin baseline** o sin hipótesis explícita.
   Si Alex no da baseline: identificar el dato necesario para obtenerla.
2. **Distinguir leading de lagging:** cobertura de datos o adopción semanal
   (leading) vs. retención o NRR (lagging). Necesitas ambos para decidir a
   tiempo.
3. **Identificar efectos perversos:** ¿maximizar esta métrica podría producir
   algo malo? Ej.: maximizar el % de pagos automatizados puede incentivar
   automatizaciones poco seguras → en pagos, toda métrica de automatización
   debe convivir con una de fiabilidad (tasa de error, pagos duplicados).
4. **Distinguir uso de impacto:**
   - **Uso:** adopción, volumen procesado, frecuencia.
   - **Impacto:** tiempo ahorrado, errores evitados, retención/expansión.
   - Un piloto debe medir ambos; uso alto con impacto plano no justifica escalar.

## Plan de medición

1. **Baseline:** cómo medimos el proceso hoy (antes del MVP).
2. **Piloto:** con qué clientes, cuánto dura, qué instrumentación.
3. **Lectura:** cuándo y cómo decidimos (umbrales en `roadmap.md`).

## Checklist de calidad

- [ ] 1 North Star + 3–5 KPIs, con baseline y objetivo (o hipótesis marcada)
- [ ] North Star elegida por valor al cliente, no por facilidad de medida
- [ ] Métricas de uso y de impacto separadas
- [ ] Alguna métrica de calidad/fiabilidad (crítico en pagos)
- [ ] Efectos perversos identificados por métrica
- [ ] Umbrales de decisión conectados con el roadmap
