# Moderated AI Development Workflow (MOD-W)

MOD-W is a role-driven, document-centered workflow for AI-assisted software development. It separates product, design, technical, implementation, review, and verification decisions across distinct roles, enforces cross-validation between multiple AI agents and models, and requires a human Moderator to approve every step before it is accepted.

Full methodology reference: https://github.com/fpmcguire/mod-w

---

## Roles

| Role | Owns | AI agent (default) |
| ---- | ---- | ------------------ |
| **Moderator** | Workflow orchestration, go/no-go authority, HITL gate | Human only |
| **Product Owner** | What and why - `product.md`, acceptance intent | Claude chatbot + Perplexity + Gemini (Definition); Claude Code SubAgent (Validation) |
| **Designer + Prototyper** | Approved visual behavior, interaction intent, prototype evidence, advisory architecture notes | Claude Design |
| **Tech Lead** | How - `architecture.md`, `domain-language.md`, `roadmap.md`, `step-xx.md`, technical review | Codex (via `AGENTS.md` at repo root) |
| **Development Team** | Implementation - code, tests, docs for each Step | Claude Code (default) or Claude Design (visual Steps) |
| **QA / Tester** | End-to-end verification - `qa.md` | Claude Code SubAgent |

The Designer + Prototyper role is optional per project. Run it only when visual, interaction, chart, animation, or real-time product risk warrants a prototype before architecture is committed.

---

## Cross-validation

No single agent both plans and implements. No single agent both implements and reviews.

```text
Product Owner                                  -> defines what and why
       -> optional Prototype Ceremony
Designer + Prototyper (Claude Design)          -> design-spec.md + prototype/ + architecture-notes.md
       -> Architecture Handoff
Tech Lead (Codex)                              -> architecture.md, roadmap.md, step-xx.md; reviews Dev Team output
       -> Implementation
Development Team (Claude Code | Claude Design) -> implements only the approved Step
       -> QA and final gate
Moderator (human)                              -> reconciles all; has final authority
```

The single most-protected boundary is Tech Lead to Development Team: Codex plans and reviews; a different implementation role executes the approved Step.

---

## Workflow - Role Sequence Per Project

The Moderator is always the human gate. Phases iterate until acceptance is met.

### Phase 0 - Project Kickoff

0a. **Product Definition** - Moderator + Product Owner produce approved `product.md`.

0b. **Prototype Ceremony (optional, Moderator decision)** - Moderator + Designer + Prototyper produce:

- `design-spec.md`
- `prototype/` folder
- `architecture-notes.md`

`design-spec.md` becomes authoritative only after Product Owner and Moderator approval, and only for user-facing visual behavior, interaction intent, screen composition, component states and variants, accessibility expectations, and approved user-facing terminology and content presentation. It is not independently authoritative for production file paths, service or module boundaries, framework or library choices, canonical domain types, internal implementation names, test implementation strategy, or technical component decomposition.

0c. **Architecture Handoff (mandatory if 0b ran)** - Moderator + Tech Lead (Codex) consume `product.md`, `design-spec.md`, the complete `prototype/` inventory, and `architecture-notes.md`. Codex independently authors `architecture.md`, `roadmap.md`, `CLAUDE.md`, `AGENTS.md`, `domain-language.md`, `cross-validation.md`, minimal root tool config, and the first `step-xx.md`. Codex evaluates prototype evidence and may accept, modify, or reject prototype implications.

### Phase 1 - Define the Step

1a. **Tech Lead (Codex)** writes or refines `step-xx.md` with scope, inputs, relevant Design IDs, acceptance checks, assigned Dev Team interface, and Reference Implementation disposition when applicable.

1b. **Moderator decision** - confirms `step-xx.md` is clear and complete before briefing the Development Team.

### Phase 2 - Implement

2a. **Moderator -> Development Team** - provides the active `step-xx.md` and relevant context. Dev Team restates the Step, proposes a plan, and waits for Moderator approval before writing code.

2b. **Development Team** implements the approved scope only and runs the blocking build gate (`{{BUILD_COMMAND}}` + `{{TEST_COMMAND}}`).

### Phase 3 - Review and Iterate

3a. **Tech Lead (Codex)** reviews the diff for architectural fit, naming consistency, scope compliance, Design ID intent where applicable, and maintainability. Writes `review.md`. Sends rework directly to Dev Team if needed.

3b. **QA SubAgent** validates against acceptance checks and approved design intent without treating prototype code as authoritative. Writes `qa.md`.

3c. **Product Owner SubAgent** confirms acceptance intent and writes sign-off.

3d. **Development Team** addresses each finding explicitly. Return to 3a until green.

### Phase 4 - Accept and Advance

4a. **Moderator final gate (HITL)** - confirms all checks pass, `review.md` and `qa.md` are complete, manually exercises the feature, creates an annotated Git tag, and advances `roadmap.md`.

---

## Canonical Documents

| Document | Owner | Purpose |
| -------- | ----- | ------- |
| `MOD-W.md` | Moderator | Project workflow quick-reference |
| `product.md` | Product Owner | What is being built, for whom, and why |
| `design-spec.md` | Designer + Prototyper | Approved visual and interaction design within its bounded authority |
| `DESIGN.md` (optional) | Designer / Moderator | Reusable design-system foundations, brand language, or durable visual principles |
| `architecture-notes.md` | Designer + Prototyper | Advisory prototype observations with evidence and confidence |
| `architecture.md` | Tech Lead | Authoritative technical structure, stack, patterns, constraints |
| `domain-language.md` | Tech Lead | Canonical terms used across docs, prompts, and code |
| `roadmap.md` | Tech Lead | Ordered sequence of small, reviewable Steps |
| `step-xx.md` | Tech Lead | Current Step - goal, scope, inputs, Design IDs, acceptance checks |
| `review.md` | Tech Lead | Technical review findings and verdict for the current Step |
| `qa.md` | QA / Tester | Verification evidence for the current Step |
| `ai-agents.md` | Tech Lead | Agent registry - models, interfaces, data handling decisions |
| `cross-validation.md` | Moderator | Claude/Codex validation mode and discrepancy protocol |
| `agents/` | Tech Lead | Tool-neutral role definitions |
| `rules/` | Tech Lead / Moderator | Path-scoped constraints |
| `skills/` | Tech Lead / Moderator | Reusable MOD-W procedures, added only when identified |
| `validation/` | Moderator | Independent validation outputs and discrepancy logs |
| `CLAUDE.md` (repo root) | Tech Lead | Dev Team config for Claude Code |
| `AGENTS.md` (repo root) | Tech Lead | Tech Lead config for Codex |
| `.codex/config.toml` (repo root) | Tech Lead / Moderator | Codex project settings |
| `.claude/settings.json` (repo root) | Tech Lead / Moderator | Claude Code settings and hooks |
| `.mcp.json` (repo root) | Tech Lead / Moderator | Shared MCP tool/data connections |

All MOD-W docs live under `mod-w/` in the project except root-level tool entrypoints and tool config. `CLAUDE.md`, `AGENTS.md`, `.codex/config.toml`, `.claude/settings.json`, and `.mcp.json` live at the repo root so CLI agents read them automatically. The optional `prototype/` folder lives at the repo root and is explicitly marked as a research artifact via `prototype/README.md`.

`mod-w/cross-validation.md` records the Claude/Codex validation mode. `mod-w/agents/` contains tool-neutral role definitions, `mod-w/rules/` contains path-scoped constraints, `mod-w/skills/` is reserved for reusable procedures, and `mod-w/validation/` contains independent validation outputs and discrepancy logs.

`design-spec.md` is the canonical MOD-W design artifact. A separate `DESIGN.md` is optional; when both exist, `DESIGN.md` holds reusable principles and global design-system guidance, while `design-spec.md` holds product-specific screens, components, states, interactions, traceability, and approval.

---

## Reference Implementation

A Reference Implementation is candidate implementation work produced outside the Development Team role, typically inside `prototype/`. It never auto-promotes to production. The Tech Lead dispositions it in `step-xx.md` as `Adopt as-is`, `Adopt with modifications`, or `Reject`.

`Adopt as-is` means preserving approved behavior and relevant structure without redesign. It still requires normal production adaptation, including framework integration, type safety, accessibility, error handling, security, tests, performance, repository conventions, and architecture compliance.

---

## Backfill and Gates

- **Backfill** produces reference documentation or evidence from work that already exists.
- **Re-executed gate** runs the current ceremony again and produces new authoritative outputs under the present workflow.
- **Retroactive approval** declares historical work compliant without rerunning the required gate. This is prohibited.

Existing work may be analyzed and backfilled, but it may not be retroactively declared compliant. Authoritative adoption requires the applicable gate to be re-executed.

---

## Operating Rules

- **Documents must earn their existence.** Prefer updating an existing doc over creating a new one.
- **No hidden scope.** Anything not in the current `step-xx.md` is out of scope for this Step.
- **Explicit out-of-scope.** When something is deferred, state it.
- **Stable naming.** Resolve naming conflicts early; keep `domain-language.md` current.
- **Pause on ambiguity.** Any role that is unsure stops and clarifies rather than guessing.
- **Lean first, expand later.** Start with `product.md`, `roadmap.md`, and `step-xx.md`; add further docs only when they clearly help.
- **Single-role-per-session.** A session is started with exactly one role prompt. Mid-session role switching is prohibited.
- **Architecture is authored by Codex, never by Claude Design.**
- **Every Step receives Codex Tech Lead review before QA acceptance.**
- **Every Step receives Moderator final approval before tagging and Roadmap advancement.**
- **If Claude Design implements from its own prototype, `step-xx.md` must record accepted, modified, rejected, and mandatory-divergence prototype assumptions.**

---

MOD-W v5 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
