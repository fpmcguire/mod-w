# Artifacts

Moderated AI Development Workflow is artifact-driven. Each role works against a small set of shared files that keep intent, design, architecture, implementation, and verification aligned.

---

## Locations

In a MOD-W-enabled project, methodology artifacts normally live in `mod-w/`. Tool entrypoints and tool-specific config live at the repo root because the CLI tools discover them there:

- `AGENTS.md` - Tech Lead config for Codex
- `CLAUDE.md` - Development Team config for Claude Code
- `.codex/config.toml` - project-scoped Codex settings
- `.claude/settings.json` - Claude Code settings and optional hook automation
- `.mcp.json` - shared MCP tool/data connection config

The optional `prototype/` folder also lives at the repo root and must include `prototype/README.md`.

Templates for each artifact are in `/templates`.

---

## Overview

| Artifact | Owner (primary) | Location | Purpose |
| -------- | --------------- | -------- | ------- |
| `product.md` | Product Owner | `mod-w/` | What we are building and why |
| `design-spec.md` | Designer + Prototyper | `mod-w/` | Bounded visual and interaction design authority after approval |
| `DESIGN.md` (optional) | Designer / Moderator | `mod-w/` or project docs | Durable design-system foundations and brand principles |
| `architecture-notes.md` | Designer + Prototyper | `mod-w/` | Advisory prototype observations with evidence and confidence |
| `prototype/` | Designer + Prototyper | repo root | Non-authoritative research prototype and inventory |
| `architecture.md` | Tech Lead | `mod-w/` | How the system is built |
| `domain-language.md` | Tech Lead | `mod-w/` | Canonical domain and agent language |
| `roadmap.md` | Tech Lead | `mod-w/` | Ordered list of Steps |
| `step-xx.md` | Tech Lead | `mod-w/` | Brief for a single Step |
| `review.md` | Tech Lead | `mod-w/` | Technical review verdict and findings per Step |
| `qa.md` | QA / Tester | `mod-w/` | Test and verification record per Step |
| `ai-agents.md` | Tech Lead | `mod-w/` | Agent definitions and data-handling decisions |
| `cross-validation.md` | Moderator | `mod-w/` | Claude/Codex validation mode and discrepancy protocol |
| `agents/*.md` | Tech Lead | `mod-w/agents/` | Tool-neutral role definitions |
| `rules/*.md` | Tech Lead / Moderator | `mod-w/rules/` | Path-scoped architecture, testing, and security constraints |
| `skills/` | Tech Lead / Moderator | `mod-w/skills/` | Reusable MOD-W procedures, added only when identified |
| `validation/discrepancies.md` | Moderator | `mod-w/validation/` | Human-resolved Claude/Codex disagreement log |
| `CLAUDE.md` | Tech Lead | repo root | Development Team role config for Claude Code |
| `AGENTS.md` | Tech Lead | repo root | Tech Lead role config for Codex |
| `.codex/config.toml` | Tech Lead / Moderator | repo root | Project-scoped Codex settings |
| `.claude/settings.json` | Tech Lead / Moderator | repo root | Claude Code settings and hook automation |
| `.mcp.json` | Tech Lead / Moderator | repo root | Shared MCP tool/data connection config |

---

## product.md

**Owner:** Product Owner
**Audience:** All roles and agents

Defines the product concept and scope: problem, users, workflows, requirements, constraints, out-of-scope items, and product-level acceptance intent.

`product.md` is the main reference for what and why in every Step.

---

## design-spec.md

**Owner:** Designer + Prototyper
**Audience:** Product Owner, Tech Lead, Development Team, QA, Moderator

After Product Owner and Moderator approval, `design-spec.md` is authoritative for:

- user-facing visual behavior
- interaction intent
- screen composition
- component states and variants
- accessibility expectations
- approved user-facing terminology and content presentation

It is not independently authoritative for:

- production file paths
- service or module boundaries
- framework or library choices
- canonical domain types
- internal implementation names
- test implementation strategy
- technical component decomposition

Those technical matters remain under Tech Lead authority in `architecture.md`, `domain-language.md`, and `step-xx.md`. Approval of `design-spec.md` does not make the prototype authoritative.

`design-spec.md` carries Design IDs such as `DS-001` so screens, components, and significant interactions can trace Product requirements to prototype evidence and first implementation Steps.

---

## DESIGN.md (optional)

`design-spec.md` is the canonical MOD-W design artifact. A separate `DESIGN.md` is optional project documentation for broader design-system foundations, brand language, or durable visual principles.

When both exist:

- `DESIGN.md` contains reusable principles and global design-system guidance.
- `design-spec.md` contains product-specific screens, components, states, interactions, traceability, and approval.
- `design-spec.md` references `DESIGN.md` instead of duplicating token catalogues.

`DESIGN.md` is not required for every project.

---

## architecture-notes.md

**Owner:** Designer + Prototyper
**Audience:** Tech Lead, Moderator

Records evidence-based observations from prototyping:

- observation
- evidence
- prototype location
- reproduction conditions
- confidence
- possible architectural implication

`architecture-notes.md` is advisory. Confidence is not architectural authority. The Tech Lead may accept, modify, or reject any implication.

---

## prototype/

**Owner:** Designer + Prototyper
**Audience:** Tech Lead, Development Team when referenced by `step-xx.md`, QA when validating design intent

The repo-root `prototype/` folder is a clickable research artifact. It must include `prototype/README.md` with:

- screens or routes included
- states demonstrated
- simulated integrations
- prototype-only controls
- known limitations
- explicitly out-of-scope behavior
- architecturally relevant files

The prototype is not production code and must not be imported into `src/`.

---

## architecture.md

**Owner:** Tech Lead
**Audience:** Tech Lead, Development Team, Moderator

Captures stack, boundaries, data flow, integration points, test strategy, risks, and architectural decisions. It is the authoritative reference for how and where changes should be made.

`architecture.md` is authored by Codex, never by Claude Design.

---

## domain-language.md

**Owner:** Tech Lead, with Product Owner input
**Audience:** All roles and agents

Defines canonical domain vocabulary, business meaning, technical meaning, allowed and banned synonyms, and code naming guidance.

The current artifact is `domain-language.md`; `DOMAIN_LANGUAGE_MATRIX.md` is not an active MOD-W artifact.

---

## roadmap.md

**Owner:** Tech Lead
**Audience:** All roles and agents

Lists small, verifiable Steps with goals, sequencing, dependencies, and risks.

---

## step-xx.md

**Owner:** Tech Lead
**Audience:** Development Team, Tech Lead, QA, Moderator

Defines a single Step: goal, scope, inputs, related requirements, related Design IDs, expected changes, Reference Implementation disposition, acceptance checks, and risks.

`step-xx.md` is the active Step artifact. `STEP.md` is stale shorthand and should not be used for current projects.

---

## review.md

**Owner:** Tech Lead
**Audience:** Tech Lead, Development Team, Moderator, Product Owner

Records the Codex Tech Lead review verdict, findings, acceptance-check mapping, required revisions, and final technical approval. The Moderator uses `review.md` as input to the final gate but does not replace the Tech Lead review.

---

## qa.md

**Owner:** QA / Tester, with Moderator final review
**Audience:** Moderator, Tech Lead, stakeholders

Captures verification evidence, automated and manual checks, defects, known limitations, regression risks, and confidence.

QA may verify approved design acceptance intent by Design ID, but prototype code is not authoritative.

---

## ai-agents.md

**Owner:** Tech Lead
**Audience:** All agents; Moderator

Defines active agents, interfaces, role boundaries, build/test commands, data handling, and tool constraints.

---

## cross-validation.md

**Owner:** Moderator
**Audience:** Reviewer, Validator, Tech Lead, Moderator

Defines whether Claude and Codex validation runs happen in `parallel` or `sequential` mode. It also defines where disagreements are recorded. Agents re-read this file before each validation pass.

---

## agents/

**Owner:** Tech Lead
**Audience:** Tool-neutral role runners and Moderator

Contains role definition files such as `architect.md`, `reviewer.md`, `qa.md`, and `validator.md`. These are supporting role descriptions, not root entrypoints.

---

## rules/

**Owner:** Tech Lead / Moderator
**Audience:** All implementation, review, and validation roles

Contains modular path-scoped constraints such as `architecture.md`, `testing.md`, and `security.md`. These files start empty and are filled only when real project constraints arise.

---

## skills/

**Owner:** Tech Lead / Moderator
**Audience:** Agents performing reusable MOD-W procedures

Reserved for reusable `SKILL.md` procedures. Do not pre-create empty skill scaffolding; add skills only when a specific procedure becomes reusable.

---

## validation/

**Owner:** Moderator
**Audience:** Reviewer, Validator, Tech Lead, Moderator

Contains independent validation outputs and `discrepancies.md`, the log of Claude/Codex disagreements that require human resolution.

---

## CLAUDE.md

**Owner:** Tech Lead
**Audience:** Claude Code and Claude Design when assigned as Development Team

Configures the Development Team role. It lives at the repo root so Claude Code reads it automatically.

---

## AGENTS.md

**Owner:** Tech Lead
**Audience:** Codex

Configures the Tech Lead role. It lives at the repo root so Codex reads it automatically.

---

## .codex/

**Owner:** Tech Lead / Moderator
**Audience:** Codex

Contains project-scoped Codex configuration such as model, sandbox, and approval policy. Keep it minimal until the project needs tuning.

---

## .claude/

**Owner:** Tech Lead / Moderator
**Audience:** Claude Code

Contains Claude Code settings and optional hook automation such as PreToolUse, PostToolUse, and Stop hooks. An empty `{}` settings file is valid when no hooks are configured.

---

## .mcp.json

**Owner:** Tech Lead / Moderator
**Audience:** All agents using shared MCP servers

Defines shared MCP tool and data connections for the project. An empty `{}` file is valid when no shared MCP connections are configured.

---

## Reference Implementation (concept - not a file)

A Reference Implementation is a candidate implementation produced outside the Development Team role, typically inside `prototype/`. It does not auto-promote to production. The Tech Lead disposes of it in `step-xx.md` as:

- `Adopt as-is`
- `Adopt with modifications`
- `Reject`

`Adopt as-is` preserves the approved behavior and relevant structure without redesign. It still requires normal production adaptation, including framework integration, type safety, accessibility, error handling, security, tests, performance, repository conventions, and architecture compliance. It never bypasses architecture, review, QA, or production-quality requirements.

---

## Backfill and Retroactive Approval

Existing work may be analyzed and backfilled, but it may not be retroactively declared compliant. Authoritative adoption requires the applicable gate to be re-executed.

---

## Usage

For each new project or example:

1. Copy templates from `/templates` into the project's `mod-w/` folder.
2. Add the v5 support folders under `mod-w/`: `agents/`, `rules/`, `skills/`, and `validation/`.
3. Place generated `CLAUDE.md` and `AGENTS.md` at the repo root.
4. Add minimal root tool config: `.codex/config.toml`, `.claude/settings.json`, and `.mcp.json`.
5. Create `product.md` first.
6. Run the optional Prototype Ceremony only when warranted.
7. Create `domain-language.md` and `architecture.md` before roadmap and Step work.
8. Maintain `roadmap.md`, `step-xx.md`, and `cross-validation.md` as work is planned and validated.
9. Update `review.md`, `qa.md`, and `validation/discrepancies.md` for every Step as applicable.

---

MOD-W v5 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
