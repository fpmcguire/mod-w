# Using MOD-W with Claude Design

> Companion integration guide for MOD-W v4.0.1.
> Peers with `articles/modw-with-codex.md`, `articles/modw-with-claude-code.md`, and `articles/modw-with-gemini.md`.

---

## Overview

**Claude Design** is Anthropic's project-scoped design environment. It can edit files, render HTML/JS in a preview pane, capture screenshots, and run scripted browser operations within a single project context — capabilities the Claude chatbot and Claude Code do not share.

In MOD-W v4.0.1, Claude Design is the default agent for the **Designer + Prototyper** role. Optionally, it may also play the **Development Team** role for visual / chart / interaction-heavy Steps when the Moderator assigns it in `step-xx.md`.

## Where Claude Design fits

| Role | Interface | Config |
| ---- | --------- | ------ |
| Designer + Prototyper | Claude Design session | `prompts/designer.md` pasted at session start |
| Development Team (visual / chart / interaction Steps, by Moderator assignment) | Claude Design session | `CLAUDE.md` at repo root |

Claude Design does **not** replace Codex (Tech Lead), Claude Code (default Dev Team and QA), the Product Owner sessions, or the Moderator.

## Responsibility split

- **Claude Design owns:** the Prototype Ceremony — producing `design-spec.md`, the `prototype/` folder, and `architecture-notes.md`. Optionally implementing visual Steps when assigned by the Moderator in `step-xx.md`.
- **Codex (Tech Lead) owns:** authoring `architecture.md` after the Architecture Handoff. Codex has authority to override structures implied by the prototype.
- **Claude Code owns:** default Development Team implementation, QA SubAgent, Product Owner SubAgent validation.
- **MOD-W owns:** Moderator authority at every gate, cross-validation invariants, Step-scoped discipline.

## Prototype Ceremony

The Prototype Ceremony is an **optional kickoff ceremony** in v4. Run it when:

- The product has novel interaction models, real-time data, or unusual visual systems
- Design decisions cannot be confidently made from text-only requirements
- Chart, animation, dashboard, or data-visualization work is central
- "Looks right" or "feels right" is part of the acceptance criteria

Skip it for CRUD apps, headless services, and projects where the visual layer is conventional.

The ceremony slots between Product Definition and Architecture Definition:

```
Product Definition  →  PROTOTYPE CEREMONY  →  ARCHITECTURE HANDOFF  →  per-Step lifecycle
                       (Claude Design)        (Codex)
```

Full lifecycle: see `docs/prototype-ceremony.md`.

Exit criteria:

- `design-spec.md` Approval Record shows Product Owner and Moderator approval
- Prototype renders without errors, demonstrates every screen in scope, includes a complete inventory, and matches the spec
- `architecture-notes.md` exists with evidence and confidence levels

## Architecture Handoff (non-negotiable gate)

After the Prototype Ceremony, the Tech Lead (Codex) consumes the four kickoff inputs - `product.md`, bounded `design-spec.md`, complete `prototype/` inventory, and `architecture-notes.md` evidence - and **independently authors** `architecture.md`. Codex has explicit authority to:

- Disagree with structural choices implied by the prototype
- Reorganize service boundaries, type names, file layout
- Reject domain term proposals from `design-spec.md §"Domain Language Proposals"` and choose alternatives
- Accept, modify, or reject `architecture-notes.md` implications after evaluating evidence, reproduction conditions, and confidence

Material divergences are recorded in `architecture.md §"Decisions That Diverge From Prototype"` with rationale.

**Why this gate is non-negotiable:** the architecture document is the highest-cost failure point in the project — every downstream Step inherits its assumptions. Allowing Claude Design to author it would create sequential same-model outputs (prototype → spec → notes → architecture → first Step), eliminating model contrast at exactly the point where contrast matters most. The Moderator may shorten or skip other v4 ceremonies under time pressure. **The Architecture Handoff may not be skipped.**

Full gate definition: see `docs/architecture-handoff.md`.

## New artifact classes

- **`prototype/`** — research artifact at repo root, produced by Claude Design, explicitly marked non-authoritative via `prototype/README.md` disclaimer. Lives outside `src/` to prevent accidental import.
- **`architecture-notes.md`** - advisory input to Architecture Definition, produced by Claude Design, retained in `mod-w/` as historical context. Observations include evidence and confidence; confidence is not authority.
- **Reference Implementation** - a candidate implementation produced outside the Dev Team role (typically inside `prototype/`). Never auto-promotes. The Tech Lead disposes of it in `step-xx.md` as `Adopt as-is`, `Adopt with modifications`, or `Reject`. `Adopt as-is` preserves approved behavior and relevant structure without redesign while still requiring production adaptation, architecture compliance, review, QA, tests, accessibility, security, performance, and repository conventions.

## Claude Design as Development Team (optional per Step)

Claude Design may play the Development Team role for a Step when:

- The Step is visual, chart, animation, or interaction-heavy
- The Step benefits from in-environment screenshot verification
- The Moderator explicitly assigns Claude Design as Dev Team in `step-xx.md §"Assigned Dev Team Interface"`

When assigned, Claude Design reads the Step brief, proposes a plan, waits for Moderator approval, and implements **only within `src/`** (the prototype folder is closed). It hands off to Codex for Tech Lead Review like any other Step.

**Hard rule:** Claude Design as Dev Team **may not** also have produced the `step-xx.md` spec. When Claude Design implements from its own prototype, Codex must record accepted, modified, rejected, and mandatory-divergence prototype assumptions in `step-xx.md`; the implementation session treats the Step and architecture as controlling.

## What Claude Design cannot do

- Author `architecture.md`, `roadmap.md`, any `step-xx.md`, `review.md`, `qa.md`, `CLAUDE.md`, or `AGENTS.md`
- Make canonical declarations about domain types, file paths, service boundaries, framework versions, or library choices
- Implement production code outside an explicit Moderator-assigned Dev Team Step
- Override or modify any artifact owned by another role
- Run the final Moderator gate or any Tech Lead approval

If asked to do any of these, Claude Design must stop and surface the request to the Moderator, naming the correct role (Tech Lead → Codex / Dev Team → Claude Code).

## Drift prevention rules

Designer + Prototyper sessions in Claude Design follow these rules:

1. **Single-role-per-session.** A session is started with exactly one role prompt (`prompts/designer.md` or the Dev Team prompt when assigned). Mid-session role switching is prohibited.
2. **Environment self-identification on session start.** The agent restates its interface (`Claude Design`), its role (`Designer + Prototyper`), and its MAY / MAY NOT scope before producing any artifact.
3. **Refuse out-of-lane requests.** When asked to produce an out-of-lane artifact, the response is: "This artifact is owned by [Codex Tech Lead / Claude Code Dev Team]. Please route this request through the appropriate role. I will stop here."
4. **Moderator-confirmed plan before any artifact production.** Even within-lane, the agent proposes the artifact list and waits for Moderator approval.
5. **No retroactive approval.** Existing work may be backfilled as reference documentation or evidence, but authoritative adoption requires the applicable gate to be re-executed under the current workflow.

## Bottom line

Claude Design adds a bounded role that captures its unique value (working prototype + design spec in one environment) without compromising MOD-W's core cross-validation guarantee (different models for plan and implement).

Claude Design is a tool for the kickoff phase and for visual Step implementation. It is not a methodology replacement and not a Tech Lead substitute.

---

MOD-W v4.0.1 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
