# Getting Started with MOD-W

New to MOD-W? Start here.

---

## 1. Understand the methodology

Read these three documents in order:

1. [`docs/manifesto.md`](manifesto.md) - why MOD-W exists and its core beliefs.
2. [`docs/roles.md`](roles.md) - who does what (Moderator, Product Owner, Designer + Prototyper, Tech Lead, Development Team, QA).
3. [`docs/step-lifecycle.md`](step-lifecycle.md) - how a step moves from idea to accepted, tagged output.

---

## 2. Set up your project

1. Copy the workflow templates from [`/templates`](../templates/) into your project's `mod-w/` folder.
2. Create the v5 support folders in `mod-w/`: `agents/`, `rules/`, `skills/`, and `validation/`.
3. Add minimal root tool config files: `.codex/config.toml`, `.claude/settings.json`, and `.mcp.json`.
4. Run the **Project Kickoff** ceremonies to produce approved planning artifacts - this is iterative work, not a fill-in-the-blanks exercise:
   - **1a. Product Definition** - iterate with the Product Owner SubAgent until `product.md` is Moderator-approved.
   - **1b. Prototype Ceremony (optional)** - when the project has visual, interaction, chart, or real-time risk, iterate with Claude Design until bounded `design-spec.md`, inventoried `prototype/`, and evidence-based `architecture-notes.md` are Moderator-approved.
   - **1c. Architecture Definition** - iterate with the Codex Tech Lead session until `architecture.md` is Moderator-approved. If the Prototype Ceremony ran, Codex performs the Architecture Handoff from all four kickoff inputs. Tech Lead then generates `roadmap.md`, `cross-validation.md`, root `CLAUDE.md`, root `AGENTS.md`, and minimal root tool config.
   - See [`docs/ceremonies.md`](ceremonies.md) for the full gated process.
5. Place generated `CLAUDE.md` and `AGENTS.md` at your repo root.
6. Create `mod-w/cross-validation.md` with `mode: parallel` unless the Moderator chooses sequential validation.
7. Create your first `step-01.md` using the [`step-xx.md` template](../templates/step-xx.md).

---

## 3. Run your first step

Follow the [`docs/step-lifecycle.md`](step-lifecycle.md) end-to-end for your first feature or change. The [example project](../examples/frontend-saved-views/) shows a pseudo-MOD-W project with artifacts through Step 01 review, QA, and tag documentation.

---

## 4. Reference docs

| What you need | Where to find it |
| --- | --- |
| Artifact definitions | [`docs/artifacts.md`](artifacts.md) |
| Quality gates | [`docs/quality-gates.md`](quality-gates.md) |
| Moderator checklist | [`docs/moderator-checklist.md`](moderator-checklist.md) |
| Domain language guide | [`docs/domain-language.md`](domain-language.md) |
| Ceremonies | [`docs/ceremonies.md`](ceremonies.md) |
| Tool integrations | [`docs/integrations/`](integrations/) |
| FAQ | [`docs/faq.md`](faq.md) |

---

MOD-W v5 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
