# Mapa base — IA agentica en desarrollo de software

**Corte:** 25 septiembre 2026  
**Finalidad:** modernizar procesos de desarrollo en empresas que implantan IA agentica  
**Uso:** estado cero de la KB; los viernes solo se añaden deltas (no reescribir este mapa salvo revisión trimestral)

---

## Resumen ejecutivo

- El centro de gravedad pasó de autocomplete/chat a **agentes de código** (planifican, editan multi-archivo, ejecutan tests/shell e iteran). Thoughtworks Radar Vol. 34 (abr 2026): Claude Code y Cursor en **Adopt**.
- **Context engineering** sustituye a “prompt engineering” como disciplina dominante: qué ve el modelo, en qué orden y con qué señal.
- El ingeniero se mueve a **orquestación + verificación**. Anthropic (dato vendor, 2026): uso de IA en ~60 % del trabajo; delegación plena solo 0–20 %.
- Multiagente en equipos pequeños = **Assess**; swarms grandes = **Caution**.
- Emergen **harnesses**: AGENTS.md / Agent Skills, sandboxes, sensores deterministas (lint, types, tests), review humano en PRs.
- Seguridad repo-level: LLMs siguen fallando en código seguro a escala de repositorio; prompts “sé seguro” ayudan poco.
- Gobernanza: Caution sobre MCP by default, instruction bloat, shadow IT acelerado por IA, y medir productividad por throughput de código.

---

## 1. Prompts vs instructions

| Concepto | Qué es | Notas |
|---|---|---|
| **Prompt** | Petición puntual de la tarea | Cambia cada vez |
| **Instructions** | Reglas persistentes: system, AGENTS.md, rules del IDE, políticas de repo, Agent Skills | Fuente de verdad del equipo; versionar en Git |
| **Ámbito por ficheros** | En muchos productos: **globs** (`src/**/*.ts`), no regex literal | No es propiedad universal de toda instruction |

**Señales:** Adopt = instrucciones compartidas y curadas. Caution = agent instruction bloat. Preferir skills con divulgación progresiva frente a un prompt/system gigante.

---

## 2. Prácticas de desarrollo con IA

Flujo típico: especificar → acotar contexto → agente implementa → gates deterministas → review humano.

- Spec-driven (Spec Kit, OpenSpec): uso emergente.
- “Vibe coding” como práctica seria: enfriado en el discurso de líderes técnicos.
- Riesgo: *codebase cognitive debt* (Caution en radar).

---

## 3. Orquestación

- Patrón: orquestador + workers; subtareas en paralelo; humano revisa entregables (p. ej. Symphony / board de issues).
- Cuello de botella: atención humana (~3–5 sesiones cómodas, señal de mercado).
- Preferir equipos pequeños de agentes; swarms solo con specs y tests densos.

---

## 4. Herramientas (señal Thoughtworks / mercado)

| Herramienta | Señal |
|---|---|
| Claude Code | Adopt |
| Cursor | Adopt |
| OpenAI Codex | Trial |
| GitHub Copilot | Fuerte en enterprise (GitHub/CI) |
| MCP | Ubicuo; **MCP by default = Caution** |
| Agent Skills / AGENTS.md | Alternativa más controlada; Trial/Adopt según caso |

---

## 5. Calidad, seguridad y gobernanza

- Benchmarks repo-level (SecRepoBench, A.S.E): bueno en snippets ≠ seguro en repo real.
- Sube: sandboxes, least privilege, Zero Trust para agentes, evals + sensores deterministas.
- Baja: medir productividad por LOC o throughput de código generado.

---

## 6. Tendencias 2025 → 2026

**Sube:** context engineering, harnesses, agentes CLI, multiagente pequeño, specs compartidas, sandboxes, gobernanza multi-herramienta.

**Baja:** prompt engineering de taller como núcleo, autocomplete como único valor, vibe coding en producción, MCP ilimitado, delegación sin review, monoteísmo de un solo vendor.

---

## Prácticas accionables (director / modernización de procesos)

1. Harness de equipo: AGENTS.md + skills en Git + gates antes del PR; medir fallos del harness, no LOC.
2. Stack deliberado: IDE agentic (día a día) + agente CLI (multi-paso); política de auto-merge vs humano (auth, pagos, PII, infra).
3. Sandbox y least privilege por defecto; SSO; no MCP abierto por defecto.
4. Specs antes de multiagente; swarms solo en experimentos controlados.
5. Seguridad/calidad en el pipeline; versionar políticas/prompts; re-evaluar al cambiar de modelo.

---

## Fuentes (corte 2026-09-25)

- Anthropic — Eight trends… 2026: https://claude.com/blog/eight-trends-defining-how-software-gets-built-in-2026
- Anthropic — 2026 Agentic Coding Trends Report: https://resources.anthropic.com/2026-agentic-coding-trends-report
- Thoughtworks Technology Radar Vol. 34: https://www.thoughtworks.com/radar
- Thoughtworks — Coding agent swarms: https://www.thoughtworks.com/en-us/radar/techniques/coding-agent-swarms
- InfoQ — OpenAI Symphony: https://www.infoq.com/news/2026/05/openai-symphony-agents/
- SecRepoBench: https://arxiv.org/html/2504.21205v1
- A.S.E / AICGSecEval: https://github.com/Tencent/AICGSecEval

---

## Vigilancia (próximas 4–8 semanas)

Actualizaciones Claude Code / Cursor / Codex; madurez Spec-Kit y orquestadores tipo Symphony; benchmarks de seguridad repo-level; control planes enterprise (SSO + política PR).
