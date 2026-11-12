# Framework — ¿Prototipo/demo durante la sesión? (Plan A vs. Plan B)

> Precaución de terminología: aquí "prototipo/demo" = artefacto visual que
> construyes durante la sesión. El **MVP** (alcance del producto) es otra cosa
> y vive en `frameworks/solution-mvp.md`.

**Regla de oro:** lo que se evalúa es que decidas bien qué merece la pena
construir, no que construyas rápido. El prototipo puede sumar puntos, pero
nunca debe restárselos al razonamiento.

## Decisión

### SÍ, construye una demo si…

- [ ] La solución se entiende mucho mejor visualmente.
- [ ] Hay **una** interacción concreta que merece la pena demostrar.
- [ ] Puedes crear algo convincente en 10–15 min.
- [ ] No necesitas datos reales ni integraciones complejas.

**Criterios antes de decidir (no caer en el sesgo de construir por construir):**

- ¿La interacción es el principal problema, o lo es la estrategia/datos?
- ¿El prototipo valida una hipótesis concreta?
- ¿Necesitamos validar un flujo de trabajo o basta con explicar una idea?
- ¿Puede construirse sin simular capacidades que aún no sabemos si existen?

**Buenos candidatos en el dominio Embat (ejemplos orientativos):**
- Dashboard de previsión de tesorería / cash position.
- Pantalla de conciliación bancaria (matching + excepciones).
- Flujo de aprobación de pagos (batch, approver, mobile).
- Bandeja de excepciones de pagos (causa + acción sugerida).

### NO construyas si…

- [ ] El problema es principalmente de estrategia, procesos o integraciones.
- [ ] Aún hay incertidumbres importantes sobre las necesidades del usuario.
- [ ] La demo obliga a inventar demasiadas cosas.
- [ ] El tiempo de desarrollo compromete la calidad del análisis.

**Casos donde no:** rediseño de arquitectura de conexiones bancarias,
problemas de fiabilidad/trazabilidad, cobertura bancaria, modelo de datos.

## Si construyes (Plan B)

1. **Antes de construir, verbalizar:**
   > "I could spend the remaining time building a small prototype, but before
   > doing that, I'd like to make sure we're aligned on the problem, the
   > proposed solution and what we want to validate. I don't want to optimize
   > for building something quickly if we're not solving the right problem."
2. Una sola pantalla o interacción, con datos ficticios.
3. Con opencode: `/demo` genera un mock HTML estático en `output/demo.html`
   (sin dependencias externas). Comparte pantalla con ese archivo abierto.
4. Al presentar: explica qué problema resuelve, qué muestra la demo y qué
   validarías con ella. La demo ilustra la decisión, no la sustituye.

## Plan A (por defecto)

Recomendación argumentada + un wireframe o flujo sencillo (texto/ASCII o
HTML estático) si aporta claridad. Sin tocar código a no ser que el caso lo
pida.

## Prototipo ≠ MVP ≠ solución de producción

- **Prototipo:** valida comprensión y usabilidad. NO demuestra que una
  integración bancaria funcione, que el modelo de datos sea correcto ni que el
  producto sea viable operativamente.
- **MVP:** alcance de producto (ver `frameworks/solution-mvp.md`).
- **Producción:** fiabilidad, trazabilidad, compliance.

Al presentar la demo, déjalo claro: qué valida y qué NO valida.

## Checklist final

- [ ] ¿La demo explica la solución mejor que 2 frases? Si no, no la construyas.
- [ ] ¿Tengo el problem statement y la solución cerrados antes de construir?
- [ ] ¿Quedan ≥10 min tras construirla para presentar y discutir?
