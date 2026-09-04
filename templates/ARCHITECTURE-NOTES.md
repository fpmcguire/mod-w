# Architecture Notes - {{PROJECT_NAME}}

**Date:** {{DATE}}
**Author:** Designer + Prototyper (Claude Design)
**Status:** Advisory - input to Tech Lead Architecture Definition. **Not authoritative.**

---

> This document records observations from the Prototype Ceremony for the Tech Lead's consideration during Architecture Definition.
>
> It is **advisory**, not constraint. Confidence describes the prototyper's certainty in an observation; it is not architectural authority. The Tech Lead may accept, modify, or reject any possible implication. Material divergences should be recorded in `architecture.md` section "Decisions That Diverge From Prototype" with rationale.

---

## Observation Format

Use one subsection per significant observation. Include concrete evidence where available; state "none observed" when a category has no findings.

### OBS-001 - {{SHORT_TITLE}}

| Field | Notes |
| ----- | ----- |
| Observation | |
| Evidence | |
| Prototype location | `prototype/...` |
| Reproduction conditions | Browser, viewport, data volume, interaction path, or simulated integration used |
| Confidence | High / Medium / Low |
| Possible architectural implication | |

---

## 1. Streaming / Performance observations

> Patterns that worked or failed under realistic load during prototyping. Include measurements where possible (FPS, render time, memory growth).

- OBS-...

---

## 2. Component composition patterns that worked

> Component boundaries, prop / signal shapes, and reuse patterns that surfaced naturally during prototyping.

- OBS-...

---

## 3. State management patterns that worked

> How state was held during prototyping (signals, stores, props), what scaled, what did not.

- OBS-...

---

## 4. Integration shapes surfaced during prototyping

> External or internal API shapes, data formats, or event flows that emerged from making the prototype actually run.

- OBS-...

---

## 5. Failed approaches

> Approaches abandoned during prototyping. Save the Tech Lead time by documenting these explicitly, including why they failed.

- OBS-...

---

## 6. Open questions for the Tech Lead

> Specific architectural decisions the prototype could not resolve and that the Tech Lead needs to make.

- ...

---

MOD-W v5
