# Role-Tooling Matrix

This matrix shows the default tool assignment for each MOD-W role. These are the recommended defaults, not requirements — teams may substitute tools where appropriate.

---

## Default Role-Tool Assignments

| Role | Phase | Interface | Config | Primary artifacts |
| ---- | ----- | --------- | ------ | ----------------- |
| Product Owner | Definition (project start) | Claude chatbot + Perplexity + Gemini | None — no project infrastructure yet | `product.md` |
| Product Owner | Validation (per-step) | Claude Code SubAgent | `CLAUDE.md` (auto-loaded) | Acceptance sign-off |
| Designer + Prototyper | Prototype Ceremony (optional) | Claude Design | `prompts/designer.md` pasted at session start | `design-spec.md`, `prototype/`, `architecture-notes.md` |
| Tech Lead | Planning + Review | Codex (full session) | `AGENTS.md` (auto-loaded) | `architecture.md`, `roadmap.md`, `step-xx.md`, `review.md` |
| Development Team | Implementation | Claude Code SubAgent by default; Claude Design when explicitly assigned for visual / chart / interaction-heavy Steps | `CLAUDE.md` (auto-loaded where supported) | Code, tests, docs |
| QA | Acceptance validation | Claude Code SubAgent | `CLAUDE.md` (auto-loaded) | `qa.md` |
| Moderator | All gates | Human | — | Approvals, git tags |

---

## Cross-Validation Design

The tool split is intentional:

| Boundary | Tools | What it catches |
| -------- | ----- | --------------- |
| Product intent vs. visual design | Product Owner + Moderator ↔ Claude Design | Ensures prototype output serves product intent before architecture begins |
| Prototype vs. architecture | Claude Design → Codex | Prevents prototype-implied structure from becoming architecture without independent Tech Lead judgment |
| Plan vs. implement | Codex (Tech Lead) ↔ Claude Code (Dev Team) | Model-level blind spots — Codex plans, Claude Code implements, Codex reviews |
| Implementation vs. acceptance | Dev Team ↔ QA SubAgent | Context-isolated re-read of the same implementation against acceptance checks |
| Acceptance vs. product intent | QA ↔ Product Owner SubAgent | Validates that passing checks actually satisfy user-facing intent |
| All outputs | Human Moderator | Final authority — approves plans, gates steps, tags releases |

---

## Product Definition Tooling

The Product Definition phase (project start) uses external chatbots because no project agent infrastructure exists yet:

| Tool | Use |
| ---- | --- |
| Claude chatbot (claude.ai) | Draft and iterate on `product.md` |
| Perplexity | Research, fact-finding, market and domain context |
| Gemini | Informal cross-validation of scope, goals, and user workflows |

The Moderator drives this phase. All three tools are optional — use what fits the project.

---

## Tech Lead Session Types

Codex runs two session types for the Tech Lead role:

| Session | Trigger | Reads | Writes |
| ------- | ------- | ----- | ------ |
| Planning | Before each Step | `product.md`, `architecture.md` | `architecture.md`, `roadmap.md`, `step-xx.md`, `CLAUDE.md`, `AGENTS.md`, `cross-validation.md`, root tool config |
| Review | After Dev Team build gate | `step-xx.md`, implementation diff | `review.md` |

In the Review session, Tech Lead reads only — no edits to implementation files.

If the Prototype Ceremony ran, the Planning session also reads `design-spec.md`, `prototype/`, and `architecture-notes.md` as Architecture Handoff inputs. Codex may override prototype-implied structures and records material divergences in `architecture.md`.

---

## Development Team Build Gate

Before handing off to Tech Lead review, the Dev Team SubAgent runs a blocking build gate:

```
{{BUILD_COMMAND}}   # e.g. npm run build
{{TEST_COMMAND}}    # e.g. npm test
```

These commands are populated by the Tech Lead when generating the project-specific `CLAUDE.md`. The Dev Team cannot proceed until both pass cleanly.

---

MOD-W v5 · Moderated AI Development Workflow · https://github.com/fpmcguire/mod-w
