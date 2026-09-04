# Roles in Moderated AI Development Workflow

Moderated AI Development Workflow defines a small set of roles with clear boundaries and accountability. Some roles may be supported by AI tools, but the role names and authority boundaries remain stable.

---

## Moderator

The Moderator is the human-in-the-loop operator of MOD-W.

The Moderator:

- Orchestrates handoffs between roles and artifacts.
- Works in the Workbench to build, run, test, debug, and fine-tune changes.
- Approves or rejects each gate.
- Uses `review.md` and `qa.md` as inputs to the final gate and records final Moderator decisions.
- Has authority to reject output, request retries, adjust scope, or stop work.

The Moderator is always human. On very small teams the Moderator may also hold Product Owner or local technical responsibilities, but the Moderator gate remains a human decision.

---

## Product Owner

The Product Owner defines what is built and why.

The Product Owner:

- Authors and maintains `product.md`.
- Sets acceptance intent and criteria for each Roadmap Step.
- Reviews and approves `roadmap.md` before implementation.
- Reviews `design-spec.md` during the Prototype Ceremony when that ceremony runs.
- Does not merge code, author architecture, or override quality gates.

In one common setup, the Product Owner role is supported by chatbot sessions during definition and by a Claude Code SubAgent during per-Step validation.

---

## Designer + Prototyper

**Default interface:** Claude Design
**Optional role:** Run the Prototype Ceremony only when visual, interaction, chart, animation, or real-time behavior warrants it.

The Designer + Prototyper produces:

- `design-spec.md`
- `prototype/` at repo root
- `architecture-notes.md`

### Authority

After Product Owner and Moderator approval, `design-spec.md` is authoritative for:

- user-facing visual behavior
- interaction intent
- screen composition
- component states and variants
- accessibility expectations
- approved user-facing terminology and content presentation

`design-spec.md` is not independently authoritative for:

- production file paths
- service or module boundaries
- framework or library choices
- canonical domain types
- internal implementation names
- test implementation strategy
- technical component decomposition

Those technical matters remain under Tech Lead authority in `architecture.md`, `domain-language.md`, and `step-xx.md`.

### Non-authoritative outputs

- `prototype/` is a research artifact and evidence source, not production code.
- `architecture-notes.md` is advisory evidence for the Tech Lead. Confidence levels in the notes are not architectural authority.
- Domain language proposals in `design-spec.md` are non-authoritative until the Tech Lead ratifies them in `domain-language.md`.

### Constraints

The Designer + Prototyper may not:

- Author `architecture.md`, `roadmap.md`, any `step-xx.md`, `review.md`, `qa.md`, `CLAUDE.md`, or `AGENTS.md`.
- Write or modify production code outside the `prototype/` folder unless separately assigned as Development Team for an approved Step.
- Declare canonical types, file paths, service boundaries, framework choices, test strategy, or domain terms.

The role prompt is `prompts/designer.md`.

---

## Tech Lead

The Tech Lead defines how the product is built. In the default MOD-W v5 workflow, the Tech Lead is Codex.

The Tech Lead:

- Cross-validates `product.md` with the Product Owner.
- Authors and maintains `architecture.md`.
- Authors and maintains `domain-language.md`.
- Authors and maintains `roadmap.md`.
- Writes and refines `step-xx.md`.
- Generates project-specific `CLAUDE.md`, `AGENTS.md`, and minimal tool config scaffolding.
- Runs the Architecture Handoff when the Prototype Ceremony ran.
- Evaluates `design-spec.md`, prototype inventory, and `architecture-notes.md` evidence without treating prototype code as authoritative.
- Reviews completed Steps and writes `review.md` before QA acceptance.

`architecture.md` is authored by Codex, never by Claude Design.

---

## Development Team

The Development Team implements approved Steps.

The Development Team:

- Reads the active `step-xx.md` and relevant approved artifacts.
- Proposes a plan and waits for Moderator approval before writing files.
- Implements code, tests, and docs scoped to the active Step.
- Runs the blocking build gate before handoff.
- Revises output based on Tech Lead review.
- Does not redefine product scope, architecture, domain language, or acceptance intent.

Supported interfaces:

| Interface | Config | Best for |
| --------- | ------ | -------- |
| Claude Code | `CLAUDE.md` at repo root | Default implementation, multi-file code changes, SubAgent spawning |
| Claude Design | `CLAUDE.md` at repo root, by Moderator assignment | Visual, chart, animation, or interaction-heavy Steps |

Claude Design as Development Team may not have authored the Step it implements. If the Step is derived from a prototype Claude Design previously produced, the Tech Lead must record accepted, modified, rejected, and mandatory-divergence prototype assumptions in `step-xx.md`. The implementing Claude Design session treats `step-xx.md` and authoritative architecture as controlling.

---

## QA / Tester

The QA role validates accepted output end to end after Tech Lead approval.

The QA function is commonly performed by a Claude Code SubAgent:

- Reads implementation files and `step-xx.md` acceptance checks.
- Verifies relevant Design IDs and approved design acceptance intent when applicable.
- Does not treat prototype code as authoritative.
- Produces `qa.md` with results, manual checks, defects, and known limitations.
- Flags checks that require human or browser verification.

---

## Workbench

The Workbench is the human-operated development environment used by the Moderator.

The Workbench:

- Hosts the local repository.
- Runs builds, tests, linters, and manual UX checks.
- Supports light code edits and debugging under Moderator control.
- Is where final human validation happens before tagging and Roadmap advancement.

---

## Default Tool Implementations

| Role | Default interface | Primary artifacts |
| ---- | ----------------- | ----------------- |
| Moderator | Human Workbench | repo state, approvals, tags |
| Product Owner definition | Claude chatbot + Perplexity + Gemini | `product.md` |
| Product Owner validation | Claude Code SubAgent | sign-off |
| Designer + Prototyper | Claude Design | `design-spec.md`, `prototype/`, `architecture-notes.md` |
| Tech Lead | Codex full session | `architecture.md`, `domain-language.md`, `roadmap.md`, `step-xx.md`, `CLAUDE.md`, `AGENTS.md`, `cross-validation.md`, `review.md` |
| Development Team | Claude Code by default; Claude Design by assignment | code, tests, docs |
| QA | Claude Code SubAgent | `qa.md` |

All AI output is moderated. No AI role self-approves its own work.

---

## Role Summary

- Moderator is always human.
- Tech Lead is Codex in the default v5 workflow.
- `architecture.md` is authored by Codex, never Claude Design.
- The same model does not both author a Step and implement that Step.
- Every Step receives Codex Tech Lead review before QA acceptance.
- Every Step receives Moderator final approval before tagging and Roadmap advancement.
- Single-role-per-session remains enforced.
- Historical work cannot receive retroactive approval.

---

MOD-W v5 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
