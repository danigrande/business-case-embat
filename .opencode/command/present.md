---
description: Genera un deck HTML estático de la solución en output/presentacion.html
agent: build
---

Genera una presentación HTML estática del business case de Embat con el look & feel de embat.io.

1. Lee `templates/notes.md` y, si existen, los entregables `output/02-problem-statement.md`,
   `output/03-solucion-mvp.md`, `output/04-roadmap.md`, `output/05-metricas.md` y
   `output/06-resumen-ejecutivo.md`. Si algún entregable no existe, construye
   esa sección desde `templates/notes.md`.
2. Input adicional del usuario: $ARGUMENTS (énfasis, secciones o estilo; si
   viene vacío, usa el deck estándar completo).
3. **Estilo:** lee `templates/embat-theme.css` y copia su contenido dentro de
   una etiqueta `<style>` del HTML (UN solo archivo, sin dependencias externas:
   nada de `<link>`, `@import`, URLs remotas ni fuentes remotas; la fuente
   Haffer ya va embebida en el theme). Usa las clases del theme
   (`.eb-card`, `.eb-tag`, `.slide.hero`, `.mock`, etc.) y el branding real
   documentado en `research/embat-brand.md`: tema claro (blanco/off-white),
   navy `#050B2C`, gradiente de marca `#C357EC→#B565F3→#5C92FE`, texto en
   español, sin inventar cifras (las hipótesis se marcan como tales).
4. **Estructura del deck** (una diapositiva por sección, navegable con teclado
   ←/→, clic y botones; barra de progreso y puntos):
   1. Portada (hero navy + logo Embat inline SVG + título del caso)
   2. Problema (problem statement en 2–3 frases + usuario y contexto)
   3. Por qué importa para Embat (encaje estratégico + captura SVG real de
      Corporate Payments de embat.io si está disponible en el repo o embebida)
   4. The Bet (oportunidad y por qué ahora)
   5. Solución recomendada (alternativas y trade-off, workflow To-Be resumido)
    6. MVP (incluido / fuera + mock `.mock`; añadir un chip de esfuerzo
       relativo del MVP marcado como hipótesis — "a validar con engineering" —
       y una nota en la tarjeta "Fuera": se aplaza por capacidad/riesgo, no
       por falta de valor)
    7. Riesgos y mitigación (2–3)
    8. Métricas (North Star + KPIs, baseline y objetivos marcados como hipótesis)
    9. Roadmap Now / Next / Later + criterios go/pivot/kill + franja de
       disclaimer con 3 chips: esfuerzo relativo por fase (hipótesis), "cada
       gate es un checkpoint de retorno: no se escala sin beneficio
       demostrado" y "compite por capacidad con el resto del roadmap: la
       secuencia depende de engineering y otras prioridades"
    10. Próximos pasos + open questions clave
    11. Cierre (hero navy, frase de recomendación para verbalizar, con el
       disclaimer de capacidad: "asumo X capacidad y que no hay una prioridad
       mayor que no esté viendo; si la hay, el orden cambia")
5. Al terminar, resume en 2 líneas: dónde está el archivo y cómo navegarlo.
   No modifiques otros archivos.
