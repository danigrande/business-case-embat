# Guía de comandos — qué hacer y en qué orden

Guía práctica para usar los comandos de opencode durante el business case.
Los comandos se cargan al arrancar opencode: si acabas de crearlos, reinicia.

## Cómo funcionan

- Se invocan escribiendo `/comando` seguido de texto (o sin texto).
- Todo lo que escribas tras el comando se pasa como `$ARGUMENTS`.
- Los comandos **leen los archivos del repo** (`templates/notes.md`,
  `frameworks/`, `research/`), así que no necesitas pegar todo cada vez.
- `/notes` escribe en `templates/notes.md`; el resto escribe en `output/`.
- Si un comando genera un entregable y no le pasas texto, usa lo que ya haya
  en `notes.md`.

## Orden recomendado en la sesión (formato live: 1–1,5 h con Alex)

| Momento | Acción | Comando |
| ------- | ------ | ------- |
| Durante Discovery (~30–40 min de diálogo) | Hacer preguntas y volcar notas en bruto tras cada bloque | `/notes ...` |
| Al cerrar Strategic Fit | Actualizar decisiones y apuesta | `/notes ...` |
| Al cerrar Solution | Volcar solución/MVP acordados | `/notes ...` |
| Al cerrar Metrics/Roadmap | Volcar outcome, métricas y fases | `/notes ...` |
| Cierre (obligatorio) | Generar y presentar el resumen ejecutivo | `/summary` |
| Cierre (opcional, recomendado) | Deck HTML para presentar | `/present` |
| Alternativa todo-en-uno | Generar 02→06 + deck en una pasada | `/runall` |
| Si sobra tiempo | Entregables separados | `/problem`, `/mvp`, `/metrics`, `/roadmap` |
| Solo Plan B (demo) | Mock HTML de una pantalla | `/demo ...` |
| Reintentar el caso | Vaciar notas y output para empezar de cero | `/reset confirmar` |

**Regla:** durante la sesión trabaja con UN documento vivo (`/notes`). El
discovery en vivo es la fase que más se evalúa: las preguntas las haces tú,
no los comandos. No lances los comandos de entregables a mitad de
conversación; te distraen. `/summary` es el único obligatorio al final.

## Comando por comando

### `/notes` — documento vivo

- **Cuándo:** cada vez que Alex suelte información relevante (3–4 veces basta).
- **Qué pasar:** notas en bruto, casi literales. No hace falta estructurarlas:
  el comando separa Facts / Hypotheses / Open questions.
- **Qué produce:** actualiza `templates/notes.md` (no crea archivos en `output/`).
- **Ejemplo:**
  ```
  /notes Alex: equipos de finanzas mid-market tardan 2-3 días en conciliar.
  Usan Excel y portales bancarios. Impacta al cierre mensual. 40% de clientes
  lo piden. Usuario: Treasurer + Accountant. Compra: CFO.
  ```

### `/summary` — resumen ejecutivo (obligatorio)

- **Cuándo:** al cierre, para presentar compartiendo pantalla.
- **Qué pasar:** opcional; un énfasis o el siguiente paso que quieras cerrar.
- **Qué produce:** `output/06-resumen-ejecutivo.md` (9 puntos + open questions).
- **Ejemplo:**
  ```
  /summary cierra con qué validaríamos con los 3 clientes piloto
  ```

### `/present` — deck HTML de la solución

- **Cuándo:** al cierre, cuando quieras presentar con una pantalla bonita en
  lugar del markdown.
- **Qué pasar:** opcional; énfasis o estilo ("solo métricas", "fondo claro").
- **Qué produce:** `output/presentacion.html` (deck estático de 11
  diapositivas, sin dependencias externas, navegable con ←/→ y clic).
- **Ejemplo:**
  ```
  /present cierra con el trade-off de cobertura bancaria
  ```

### `/runall` — secuencia completa de cierre

- **Cuándo:** al cierre, cuando prefieras una sola pasada en vez de comando a
  comando. Asume que `notes.md` ya está completo.
- **Qué pasar:** opcional; pasos a excluir ("sin presentacion").
- **Qué produce:** `output/02` → `03` → `04` → `05` → `06` y
  `output/presentacion.html`, manteniendo coherencia entre todos.
- **Ejemplo:**
  ```
  /runall sin roadmap
  ```

### `/reset` — empezar el caso de cero

- **Cuándo:** entre sesiones o si el caso cambia por completo.
- **Qué pasar:** obligatorio `confirmar` (sin él, no ejecuta nada).
- **Qué produce:** restaura `templates/notes.md` y
  `templates/decision-log.md` a su plantilla y vacía `output/` (excepto
  `.gitkeep`). No toca `research/`, `frameworks/` ni `.opencode/`.
- **Ejemplo:**
  ```
  /reset confirmar
  ```

### `/problem` — Problem Statement

- **Cuándo:** al cerrar Discovery, o al final si sobra tiempo.
- **Qué pasar:** opcional; matices que no estén en las notas.
- **Qué produce:** `output/02-problem-statement.md`.
- **Ejemplo:**
  ```
  /problem el impacto principal es el retraso del cierre, no el coste
  ```

### `/mvp` — solución y alcance MVP

- **Cuándo:** al cerrar Solution, o al final si sobra tiempo.
- **Qué pasar:** opcional; restricciones o preferencias de alcance.
- **Qué produce:** `output/03-solucion-mvp.md`.
- **Ejemplo:**
  ```
  /mvp prioriza reutilizar la conectividad existente y TellMe; deja la
  conciliación de PSP fuera del MVP
  ```

### `/metrics` — métricas de éxito

- **Cuándo:** al cerrar Metrics, o al final si sobra tiempo.
- **Qué pasar:** opcional; la métrica que quieras priorizar o un baseline.
- **Qué produce:** `output/05-metricas.md`.
- **Ejemplo:**
  ```
  /metrics usa como métrica principal las horas de conciliación ahorradas
  ```

### `/roadmap` — Now / Next / Later

- **Cuándo:** al cerrar Roadmap, o al final si sobra tiempo.
- **Qué pasar:** opcional; dependencias o plazos conocidos.
- **Qué produce:** `output/04-roadmap.md`.
- **Ejemplo:**
  ```
  /roadmap la validación con el piloto bloquea el paso a Next
  ```

### `/demo` — prototipo (solo Plan B)

- **Cuándo:** solo si decides construir demo según
  `frameworks/prototype-decision.md` y sobra tiempo.
- **Qué pasar:** qué pantalla construir. Sin texto, elige la más representativa.
- **Qué produce:** `output/demo.html` (HTML estático, sin dependencias, datos
  ficticios).
- **Ejemplo:**
  ```
  /demo pantalla de conciliación con matching automático y excepciones
  ```

## Errores comunes

- **`/notes` sin texto:** no actualiza nada. Pasa las notas.
- **`/reset` sin `confirmar`:** no ejecuta nada, por seguridad.
- **Lanzar `/mvp` antes de tener problema y outcome claros:** el resultado será
  genérico. Primero `/notes` con el problema y el resultado objetivo.
- **Generar 6 documentos a mitad de sesión:** fricción innecesaria. Documento
  único hasta el cierre; separa solo al final.
- **Construir demo sin cerrar problema y solución:** primero verbaliza el
  problema y la solución, luego construye.

## Checklist antes de presentar

- [ ] `templates/notes.md` refleja Facts / Hypotheses / Open questions
- [ ] `output/06-resumen-ejecutivo.md` generado y revisado
- [ ] (Opcional) `output/presentacion.html` abierto si presentas con deck
- [ ] Cada decisión tiene justificación y trade-off
- [ ] Hay un siguiente paso accionable de validación
- [ ] (Opcional) `output/demo.html` abierto si vas a enseñarlo
