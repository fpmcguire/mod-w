# Artifacts

Moderated AI Development Workflow is artifact-driven. Each role works against a small set of shared files that keep intent, design, architecture, implementation, and verification aligned.

---

## Locations

In a MOD-W-enabled project, methodology artifacts normally live in `mod-w/`. Two tool config files live at the repo root because the CLI tools read them automatically:

- `CLAUDE.md` - Development Team config for Claude Code
- `AGENTS.md` - Tech Lead config for Codex

The optional v4 `prototype/` folder also lives at the repo root and must include `prototype/README.md`.

Templates for each artifact are in `/templates`.

---

## Overview

| Artifact | Owner (primary) | Location | Purpose |
| -------- | --------------- | -------- | ------- |
| `PRODUCT.md` | Product Owner | `mod-w/` | What we are building and why |
| `DESIGN-SPEC.md` | Designer + Prototyper | `mod-w/` | Bounded visual and interaction design authority after approval |
| `DESIGN.md` (optional) | Designer / Moderator | `mod-w/` or project docs | Durable design-system foundations and brand principles |
| `ARCHITECTURE-NOTES.md` | Designer + Prototyper | `mod-w/` | Advisory prototype observations with evidence and confidence |
| `prototype/` | Designer + Prototyper | repo root | Non-authoritative research prototype and inventory |
| `ARCHITECTURE.md` | Tech Lead | `mod-w/` | How the system is built |
| `DOMAIN_LANGUAGE.md` | Tech Lead | `mod-w/` | Canonical domain and agent language |
| `ROADMAP.md` | Tech Lead | `mod-w/` | Ordered list of Steps |
| `STEP-XX.md` | Tech Lead | `mod-w/` | Brief for a single Step |
| `REVIEW.md` | Tech Lead | `mod-w/` | Technical review verdict and findings per Step |
| `QA.md` | QA / Tester | `mod-w/` | Test and verification record per Step |
| `AI_AGENTS.md` | Tech Lead | `mod-w/` | Agent definitions and data-handling decisions |
| `CLAUDE.md` | Tech Lead | repo root | Development Team role config for Claude Code |
| `AGENTS.md` | Tech Lead | repo root | Tech Lead role config for Codex |

---

## PRODUCT.md

**Owner:** Product Owner
**Audience:** All roles and agents

Defines the product concept and scope: problem, users, workflows, requirements, constraints, out-of-scope items, and product-level acceptance intent.

`PRODUCT.md` is the main reference for what and why in every Step.

---

## DESIGN-SPEC.md

**Owner:** Designer + Prototyper
**Audience:** Product Owner, Tech Lead, Development Team, QA, Moderator

After Product Owner and Moderator approval, `DESIGN-SPEC.md` is authoritative for:

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

Those technical matters remain under Tech Lead authority in `ARCHITECTURE.md`, `DOMAIN_LANGUAGE.md`, and `STEP-XX.md`. Approval of `DESIGN-SPEC.md` does not make the prototype authoritative.

`DESIGN-SPEC.md` carries Design IDs such as `DS-001` so screens, components, and significant interactions can trace Product requirements to prototype evidence and first implementation Steps.

---

## DESIGN.md (optional)

`DESIGN-SPEC.md` is the canonical MOD-W design artifact. A separate `DESIGN.md` is optional project documentation for broader design-system foundations, brand language, or durable visual principles.

When both exist:

- `DESIGN.md` contains reusable principles and global design-system guidance.
- `DESIGN-SPEC.md` contains product-specific screens, components, states, interactions, traceability, and approval.
- `DESIGN-SPEC.md` references `DESIGN.md` instead of duplicating token catalogues.

`DESIGN.md` is not required for every project.

---

## ARCHITECTURE-NOTES.md

**Owner:** Designer + Prototyper
**Audience:** Tech Lead, Moderator

Records evidence-based observations from prototyping:

- observation
- evidence
- prototype location
- reproduction conditions
- confidence
- possible architectural implication

`ARCHITECTURE-NOTES.md` is advisory. Confidence is not architectural authority. The Tech Lead may accept, modify, or reject any implication.

---

## prototype/

**Owner:** Designer + Prototyper
**Audience:** Tech Lead, Development Team when referenced by `STEP-XX.md`, QA when validating design intent

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

## ARCHITECTURE.md

**Owner:** Tech Lead
**Audience:** Tech Lead, Development Team, Moderator

Captures stack, boundaries, data flow, integration points, test strategy, risks, and architectural decisions. It is the authoritative reference for how and where changes should be made.

`ARCHITECTURE.md` is authored by Codex, never by Claude Design.

---

## DOMAIN_LANGUAGE.md

**Owner:** Tech Lead, with Product Owner input
**Audience:** All roles and agents

Defines canonical domain vocabulary, business meaning, technical meaning, allowed and banned synonyms, and code naming guidance.

The current artifact is `DOMAIN_LANGUAGE.md`; `DOMAIN_LANGUAGE_MATRIX.md` is not an active MOD-W v4 artifact.

---

## ROADMAP.md

**Owner:** Tech Lead
**Audience:** All roles and agents

Lists small, verifiable Steps with goals, sequencing, dependencies, and risks.

---

## STEP-XX.md

**Owner:** Tech Lead
**Audience:** Development Team, Tech Lead, QA, Moderator

Defines a single Step: goal, scope, inputs, related requirements, related Design IDs, expected changes, Reference Implementation disposition, acceptance checks, and risks.

`STEP-XX.md` is the active Step artifact. `STEP.md` is stale shorthand and should not be used for current v4 projects.

---

## REVIEW.md

**Owner:** Tech Lead
**Audience:** Tech Lead, Development Team, Moderator, Product Owner

Records the Codex Tech Lead review verdict, findings, acceptance-check mapping, required revisions, and final technical approval. The Moderator uses `REVIEW.md` as input to the final gate but does not replace the Tech Lead review.

---

## QA.md

**Owner:** QA / Tester, with Moderator final review
**Audience:** Moderator, Tech Lead, stakeholders

Captures verification evidence, automated and manual checks, defects, known limitations, regression risks, and confidence.

QA may verify approved design acceptance intent by Design ID, but prototype code is not authoritative.

---

## AI_AGENTS.md

**Owner:** Tech Lead
**Audience:** All agents; Moderator

Defines active agents, interfaces, role boundaries, build/test commands, data handling, and tool constraints.

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

## Reference Implementation (v4, concept - not a file)

A Reference Implementation is a candidate implementation produced outside the Development Team role, typically inside `prototype/`. It does not auto-promote to production. The Tech Lead disposes of it in `STEP-XX.md` as:

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
2. Place generated `CLAUDE.md` and `AGENTS.md` at the repo root.
3. Create `PRODUCT.md` first.
4. Run the optional Prototype Ceremony only when warranted.
5. Create `DOMAIN_LANGUAGE.md` and `ARCHITECTURE.md` before roadmap and Step work.
6. Maintain `ROADMAP.md` and `STEP-XX.md` as work is planned.
7. Update `REVIEW.md` and `QA.md` for every Step.

---

MOD-W v4.0.1 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
