# Prototype Ceremony

> Optional kickoff ceremony introduced in MOD-W v4. Run before Architecture Definition when the Moderator decides visual, interaction, chart, animation, or real-time risk warrants a prototype.

---

## Purpose

Produce a working clickable prototype, a bounded design specification, and advisory architecture observations before architecture is committed. The prototype surfaces what `product.md` alone cannot: visual fidelity, interaction grain, state behavior, simulated integrations, and performance clues that emerge only when the design is forced to run.

The ceremony preserves MOD-W cross-validation by keeping technical authority with the Tech Lead. `architecture-notes.md` is advisory, the prototype is a research artifact, and `architecture.md` is authored by Codex in the Architecture Handoff that follows.

---

## When to Run

Run the Prototype Ceremony when any of these apply:

- The product has novel interaction models, real-time data, or unusual visual systems.
- Design decisions cannot be confidently made from text-only requirements.
- Chart, animation, dashboard, or data-visualization work is central.
- "Looks right" or "feels right" is part of acceptance intent.

Skip it when the UI is conventional, the visual layer is well understood, and no design uncertainty surfaced during Product Definition.

The Moderator decides per project and records the decision in the project's `MOD-W.md`.

---

## Inputs

| Input | Source | Authority |
| ----- | ------ | --------- |
| `product.md` | Product Owner | Authoritative |
| Brand assets, reference imagery, written tone descriptions | Moderator | Directional |
| `templates/design-spec.md` | MOD-W repo | Template |
| `templates/architecture-notes.md` | MOD-W repo | Template |
| `templates/prototype-README.md` | MOD-W repo | Template |
| `prompts/designer.md` | MOD-W repo | Role prompt |

---

## Outputs

| Output | Status | Path |
| ------ | ------ | ---- |
| `design-spec.md` | Bounded authority after Product Owner and Moderator approval | `mod-w/design-spec.md` |
| Clickable prototype | Research artifact, non-authoritative | `prototype/` at repo root |
| `architecture-notes.md` | Advisory evidence for Architecture Definition | `mod-w/architecture-notes.md` |

After approval, `design-spec.md` is authoritative for user-facing visual behavior, interaction intent, screen composition, component states and variants, accessibility expectations, and approved user-facing terminology and content presentation.

It is not independently authoritative for production file paths, service or module boundaries, framework or library choices, canonical domain types, internal implementation names, test implementation strategy, or technical component decomposition.

---

## Lifecycle

### 1. Brief

The Moderator provides `product.md`, assets, references, `prompts/designer.md`, and the three templates.

### 2. Restate

Claude Design states its environment, role, MAY / MAY NOT scope, product understanding, expected screens, and up to five clarifying questions.

### 3. Moderator Approves Understanding

No prototype work begins until the Moderator confirms.

### 4. Plan

Claude Design proposes a short plan distinguishing design-spec work, prototype work, and architecture-notes work.

### 5. Options Gate

The Moderator approves or adjusts the plan.

### 6. Produce

Claude Design produces:

- `design-spec.md` with Design IDs, traceability, and Approval Record.
- `prototype/` with `prototype/README.md` inventory.
- `architecture-notes.md` with evidence and confidence.

### 7. Cross-validation Pause

Before exit, the following reviews run:

- Product Owner reviews `design-spec.md` against `product.md` acceptance intent.
- Codex performs a Tech Lead feasibility pre-review of the design, prototype inventory, and architecture notes.
- Optional independent design review checks visual coherence.

Tech Lead feasibility pre-review is advisory and does not transfer architecture authority.

### 8. Iterate

Claude Design addresses feedback by section number, updates the full artifacts, and keeps prototype behavior aligned with the spec.

### 9. Moderator Final Gate

The Moderator accepts or rejects the ceremony output.

---

## Exit Criteria

The ceremony exits only when:

- `design-spec.md` Approval Record shows Product Owner approval.
- `design-spec.md` Approval Record shows Moderator approval for Architecture Handoff.
- Tech Lead feasibility pre-review is recorded, even if concerns remain open for Architecture Handoff.
- Prototype renders without errors, demonstrates every screen in scope, and matches the spec.
- `prototype/README.md` includes the full inventory.
- `architecture-notes.md` exists with concrete evidence and honest confidence levels where observations exist.

Approval of `design-spec.md` does not make the prototype authoritative.

---

## Backfill and Retroactive Approval

Existing design or prototype work may be analyzed and backfilled as reference documentation or evidence. It may not be retroactively declared compliant. Authoritative adoption requires the Prototype Ceremony or Architecture Handoff gate to be re-executed under the current workflow.

---

## Anti-patterns

- Skipping the cross-validation pause.
- Treating the prototype as production scaffolding.
- Treating `design-spec.md` as technical architecture.
- Allowing the Designer + Prototyper to declare canonical types, file paths, framework choices, or domain terms.
- Running the ceremony when it is not needed.

---

MOD-W v5
