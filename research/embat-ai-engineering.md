# Embat — AI engineering (agentes, evals y coste)

> Fuente: tech blog de embat.io (sept 2026), Alexander Cogneau, Head of
> Banking and Payment Products. Sirve para formular soluciones con IA con el
> rigor que Embat practica. Los datos son claims públicos: **no citarlos como
> hechos del caso**; úsalos como patrones y preguntas.

## Qué cuentan

- Plataforma interna de agentes ("Agent M. Batt") sobre Claude Managed Agents:
  cada equipo posee sus prompts sobre capacidades compartidas (routing de
  subagentes, memoria, tool calling, escalado). Un equipo puede shipar una
  mejora en ~30 min.
- El agente investiga incidencias operativas (pagos fallidos, consultas de
  clientes, forecasts) y decide **escalar / responder / actuar / cerrar**, y
  redacta la respuesta al cliente.
- Ejemplo canónico: un pago falla por un código postal faltante; el agente
  identifica el pago, busca en logs, determina la siguiente acción y redacta
  la respuesta. Si escala sin necesidad o **actúa sin permiso, el eval falla**.

## Marco de evals (cómo mantienen la calidad)

- Escenarios que fijan: el **input** (ticket real con datos congelados), las
  **herramientas** que debe llamar, la **decisión** esperada (escalar /
  responder / actuar / cerrar) y la **comunicación al cliente** (hechos que
  deben aparecer y claims que NO deben).
- Los escenarios se construyen a partir de fallos reales pasados.
- Los evals se ejecutan ante cada cambio de prompt o herramienta (~€5 por run).

## Auto-mejora y human-in-the-loop

- El agente se auto-escala cuando: un tool call vuelve vacío, entra en bucle
  (límite de 15 tool calls) o un humano puntúa mal la respuesta (Slack/Zendesk,
  thumbs up/down registrados por sesión).
- El mensaje de escalado incluye el diagnóstico y el prompt que lo arreglaría;
  se aplica el cambio y **una persona lo revisa**. El trabajo pasa de
  "encontrar el fix" a "revisar el fix".

## Economía (patrones, no cifras del caso)

- Investigación/resolución: ~30 min de ingeniero vs ~3 min del agente por
  ~€0,70 (claim del artículo).
- La mayor línea de coste es **escribir la prompt cache** (prefijo compartido);
  ratio lectura/escritura ~2,3; la lectura cacheada cuesta ~90% menos.
- Herramientas acotadas por agente: seguridad + prefijo más corto = coste menor.
- Consultas de datos: herramientas dedicadas (columnas concretas + filtro de
  fecha) en vez de escanear cientos de GB.

## Qué implica para el caso (claves de solutioning)

- Para incidencias de pago, el patrón esperable en Embat es: **agente que
  investiga, interpreta y redacta; humano que decide y ejecuta**.
- Cualquier propuesta con IA debe incluir: **gate de evals** (input fijo,
  decisión esperada, claims prohibidos), human-in-the-loop por defecto y
  **coste como hipótesis** (caching y tooling acotado como palancas).
- Lo que Embat valora (inferencia razonable, no certeza): calidad validada,
  coste disciplinado y velocidad sin degradación. Alineado con la disciplina
  de evidencia del repo.
- Ojo: el artículo describe agentes **internos** (soporte/ingeniería). Si el
  caso pide una feature de cara al cliente, la propuesta puede ser
  "productizar esa capacidad": preguntar qué existe internamente antes de
  proponer construir.

## Preguntas a validar si el caso toca IA

- ¿La solución es para usuarios finales o para equipos internos (soporte, CS)?
- ¿Qué evals/criterios de exactitud existen o hay que crear antes de lanzar?
- ¿Qué puede hacer la IA sin permiso y qué requiere siempre decisión humana?
- ¿Cómo se mide y limita el coste por operación?
- ¿Qué datos congelados hay para validar la calidad de forma repetible?
