# Architecture Handoff

> Mandatory kickoff gate when the Prototype Ceremony has run. Runs in a Codex Tech Lead session immediately after the Prototype Ceremony exits.

---

## Purpose

The Architecture Handoff is where Designer + Prototyper outputs pass to Codex for independent technical disposition. It prevents prototype-implied structures from silently becoming production architecture.

This gate may not be skipped when the Prototype Ceremony has run.

---

## Inputs

Codex receives all four kickoff inputs:

| Input | Status |
| ----- | ------ |
| `PRODUCT.md` | Authoritative product intent |
| `DESIGN-SPEC.md` | Bounded design authority after approval |
| `prototype/` folder | Research artifact with inventory |
| `ARCHITECTURE-NOTES.md` | Advisory evidence |

`DESIGN-SPEC.md` is authoritative only for user-facing visual behavior, interaction intent, screen composition, component states and variants, accessibility expectations, and approved user-facing terminology and content presentation. Technical matters remain under Tech Lead authority.

---

## Inspection Requirements

Codex must:

- inspect the complete `prototype/README.md` inventory;
- run or view all in-scope flows listed in the inventory;
- read all prototype files identified as architecturally relevant;
- inspect screenshots, routes, or pages cited as prototype evidence in `DESIGN-SPEC.md`;
- evaluate all significant `ARCHITECTURE-NOTES.md` observations, including evidence, reproduction conditions, and confidence;
- sample supporting prototype files as needed for confidence.

Codex is not required to read every generated or supporting prototype file line by line when the prototype is large, unless the inventory identifies those files as architecturally relevant.

---

## Codex Authority

Codex has explicit authority to:

- disagree with structural choices implied by the prototype;
- reorganize service boundaries, module boundaries, type names, and file layout;
- choose framework, library, runtime, and test strategy;
- reject or revise domain term proposals from `DESIGN-SPEC.md`;
- accept, modify, or reject possible implications from `ARCHITECTURE-NOTES.md`;
- decide the disposition of every candidate Reference Implementation in `prototype/`.

`ARCHITECTURE-NOTES.md` is input, not constraint. Confidence levels in the notes do not create architectural authority.

---

## Outputs

Codex produces:

| Output | Path |
| ------ | ---- |
| `ARCHITECTURE.md` | `mod-w/ARCHITECTURE.md` |
| `DOMAIN_LANGUAGE.md` | `mod-w/DOMAIN_LANGUAGE.md` |
| `ROADMAP.md` | `mod-w/ROADMAP.md` |
| `CLAUDE.md` | repo root |
| `AGENTS.md` | repo root |
| `STEP-01.md` | `mod-w/STEP-01.md` |

If `ARCHITECTURE.md` materially diverges from prototype implications, Codex records the divergence in `ARCHITECTURE.md` section "Decisions That Diverge From Prototype" with rationale.

When writing `STEP-XX.md`, Codex cites relevant Design IDs. If Claude Design is assigned to implement a Step derived from its own prototype, Codex records accepted, modified, rejected, and mandatory-divergence prototype assumptions in the Step.

---

## Reference Implementation Disposition

The Tech Lead disposes of candidate prototype code in `STEP-XX.md` as:

- `Adopt as-is`
- `Adopt with modifications`
- `Reject`

`Adopt as-is` preserves approved behavior and relevant structure without redesign. It still requires normal production adaptation, including framework integration, type safety, accessibility, error handling, security, tests, performance, repository conventions, and architecture compliance. It never bypasses architecture, review, QA, or production-quality requirements.

---

## Lifecycle

1. Moderator provides the four kickoff inputs and `prompts/tech-lead.md`.
2. Codex inspects the inputs according to the inspection requirements.
3. Codex restates product intent, design constraints, prototype evidence, and architectural decisions to make.
4. Moderator confirms the restatement.
5. Codex proposes architecture, file layout, service boundaries, key patterns, and divergence call-outs.
6. Moderator approves or requests options.
7. Codex writes the output artifacts.
8. Moderator reviews and approves or sends back for revision.

---

## Backfill and Retroactive Approval

Backfill may produce reference documentation or evidence from existing work. A re-executed gate runs this Architecture Handoff again and produces new authoritative outputs under the current workflow. Retroactive approval declares historical work compliant without rerunning the required gate and is prohibited.

Existing work may be analyzed and backfilled, but it may not be retroactively declared compliant. Authoritative adoption requires this gate to be re-executed.

---

## Anti-patterns

- Treating `ARCHITECTURE-NOTES.md` as authoritative.
- Treating `DESIGN-SPEC.md` as technical architecture.
- Codex consuming only `DESIGN-SPEC.md` and skipping prototype inventory or `ARCHITECTURE-NOTES.md`.
- Letting Claude Design author `ARCHITECTURE.md`.
- Letting `Adopt as-is` bypass production-quality requirements.

---

MOD-W v4.0.1
