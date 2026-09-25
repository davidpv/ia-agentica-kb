# Glosario — IA agentica en desarrollo

Términos que aparecen en el mapa, deltas o conversaciones de modernización de proceso. Se amplía cuando surge vocabulario nuevo o cambia el significado operativo. Orden alfabético.

| Término | Definición operativa |
|---|---|
| **AGENTS.md** | Fichero de instrucciones compartidas del repo (formato Agentic AI Foundation). Fuente de verdad multi-herramienta; Claude Code lo lee como fallback si no hay `CLAUDE.md`. |
| **Agent Skills** | Unidades de instrucción reutilizables (y a menudo con divulgación progresiva) frente a un system prompt monolítico. |
| **Agentic AI Foundation** | Iniciativa (Linux Foundation) que impulsó `AGENTS.md` como formato común entre herramientas. |
| **CLAUDE.md** | Instruction file específica de Claude Code. Si existe, suele ganar sobre `AGENTS.md` (salvo import o modo «ambos»). `CLAUDE.local.md` cuenta como `CLAUDE.md`. |
| **Codebase cognitive debt** | Deuda cognitiva del código cuando la IA acelera cambios que el equipo no entiende ni puede mantener. |
| **Context engineering** | Diseño de qué ve el modelo, en qué orden y con qué señal (sustituye a «prompt engineering» como disciplina dominante). |
| **Coordination (en AGENTS.md)** | Bloques de coordinación multiagente: dependencias, milestones binarios, exclusion zones y rollback. |
| **Exclusion zones** | Convenciones de «lock» por fichero o recurso para que dos agentes no editen el mismo área a la vez. |
| **Gates deterministas** | Comprobaciones no-LLM antes del merge: lint, types, tests, scanners. Sensores del harness. |
| **Globs (ámbito)** | Patrones de ficheros (`src/**/*.ts`) que limitan dónde aplica una rule; en muchos productos no son regex literales. |
| **Harness** | Conjunto instructions + skills + sandboxes + gates + review humano. El producto de ingeniería del equipo agentico, no el prompt puntual. |
| **Instruction bloat** | Crecimiento descontrolado de rules/system/AGENTS que degrada el comportamiento del agente. Caution en radares. |
| **Instructions** | Reglas persistentes (system, AGENTS.md, rules del IDE, políticas de repo, skills). Distintas del **prompt** puntual. |
| **MCP (Model Context Protocol)** | Protocolo de herramientas/contexto entre clientes y servidores. Ubicuo; «MCP by default» = Caution (superficie de ataque y shadow IT). |
| **Multiagente** | Varios agentes coordinados (orquestador + workers o peers). Equipos pequeños = Assess; swarms grandes = Caution. |
| **Prompt** | Petición puntual de la tarea. Cambia cada vez; no sustituye a las instructions versionadas. |
| **Repo-level (seguridad)** | Evaluación de código seguro a escala de repositorio (no solo snippets). Benchmarks: SecRepoBench, A.S.E, etc. |
| **Sandbox** | Entorno acotado donde el agente ejecuta (least privilege, sin acceso libre a secretos/red). |
| **Shadow IT (IA)** | Uso de herramientas/agentes fuera de política de la empresa, acelerado por IA. |
| **Spec-driven** | Flujo que parte de especificaciones compartidas (p. ej. Spec Kit, OpenSpec) antes de que el agente implemente. |
| **Swarm** | Multiagente a gran escala / muchos agentes en paralelo. Solo con specs y tests densos; sin exclusiones/rollback = deuda operativa. |
| **Vibe coding** | Generar código «a sensación» con poca especificación o review. Enfriado en el discurso de líderes técnicos para producción. |
| **Worktree** | Copia de trabajo Git aislada; harness base para un agente/cambio sin pisar a otros. |

_Última ampliación: 2026-09-25 (arranque + términos del delta AGENTS.md / coordinación)._
