# Embat Business Case — Kit de preparación

Repo de preparación para la entrevista de **Principal Product Manager en Embat**
(plataforma de tesorería: conectividad bancaria y ERP, cash management, pagos a
proveedores, conciliación y vuelcado de datos al ERP).

Business case esperado: **sesión de 1–1,5 h en la oficina** con un interlocutor
(al que llamamos "Alex") que presentará un problema real en directo. **El
formato evalúa el proceso:** qué preguntas haces, cómo identificas lo
importante y cuándo pasas a la solución. Al final se presenta la propuesta.

## Cómo usar este repo durante la sesión

1. **Fase de preguntas (la que más se evalúa):** usa
   `guide/90min-case-framework.md` como guion — pregunta por usuario, proceso
   As-Is, frecuencia, impacto, causa raíz y restricciones antes de proponer.
   No propongas features hasta entender el problema.
2. **Abre `templates/notes.md`** — es el **documento único de trabajo** de la
   sesión: contexto, Facts / Hypotheses / Open questions, decision log,
   stakeholders, problem statement, outcome target, MVP, métricas y roadmap.
   Captura solo lo que condiciona decisiones; no transcribas todo.
3. **Sigue el orden de prioridad de `guide/90min-case-framework.md`:**
   Problem Discovery → Strategic Fit → Solution → Metrics → Roadmap.
   Competitors, moat y economics son **transversales**: úsalos cuando afecten
   a una decisión, no como fase aislada.
4. **Durante la sesión usa `/notes`** para mantener el documento vivo.
   No generes entregables separados a mitad de sesión.
5. **Prototipo solo si aporta** (decídete con
   `frameworks/prototype-decision.md`): Plan A = recomendación argumentada
   (por defecto). Plan B = `/demo` genera un mock HTML estático de una sola
   pantalla en `output/demo.html`.
6. **Al cierre:** `/summary` genera `output/06-resumen-ejecutivo.md` para
   presentar compartiendo pantalla. `/present` añade un deck HTML
   (`output/presentacion.html`); `/runall` hace toda la secuencia (02→06 +
   deck) en una pasada. `/problem`, `/mvp`, `/roadmap`, `/metrics` solo si
   sobra tiempo.

## Comandos de opencode

Detalle de cada comando, qué pasarle y en qué orden: **[GUIA-COMANDOS.md](GUIA-COMANDOS.md)**.

| Comando      | Genera (al cierre o si sobra tiempo)                   |
| ------------ | ------------------------------------------------------ |
| `/notes`     | Actualiza `templates/notes.md` (documento vivo)        |
| `/summary`   | `output/06-resumen-ejecutivo.md` (obligatorio al cierre) |
| `/present`   | `output/presentacion.html` (deck estático para presentar) |
| `/runall`    | Secuencia completa: 02→03→04→05→06 + deck en una pasada |
| `/reset`     | Vacía notas y `output/` para empezar de cero (requiere `confirmar`) |
| `/problem`   | `output/02-problem-statement.md`                       |
| `/mvp`       | `output/03-solucion-mvp.md`                            |
| `/roadmap`   | `output/04-roadmap.md`                                 |
| `/metrics`   | `output/05-metricas.md`                                |
| `/demo`      | `output/demo.html` (mock HTML de una pantalla, Plan B) |

## Contenido del repo

| Carpeta       | Qué hay                                                              |
| ------------- | -------------------------------------------------------------------- |
| `GUIA-COMANDOS.md` | Qué hace cada comando, qué pasarle y el orden de uso            |
| `guide/`      | Guion de 90 min reorganizado por prioridad                          |
| `research/`   | Embat (producto), competidores y glosario de dominio de tesorería    |
| `frameworks/` | Plantillas accionables (problem statement, MVP, roadmap, métricas, prototipo…) |
| `templates/`  | Plantilla de notas en vivo, decision log y theme de marca             |
| `output/`     | Entregables generados durante la sesión                              |
| `.opencode/`  | Comandos que automatizan la generación de entregables                |

## Regla de oro de la sesión

> No intentes cubrir todas las fases ni responder todas las preguntas.
> Selecciona las preguntas que permiten tomar mejores decisiones.
> Esa capacidad de selección es parte de lo que se evalúa.

Y una frase para verbalizar cuando toque decidir alcance:

> "I would rather deliver a smaller solution that solves the core customer
> problem reliably than a broader solution that introduces unnecessary
> complexity."
