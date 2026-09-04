# Moderated AI Development Workflow (MOD-W)

This pseudo-MOD-W example project uses MOD-W v5 layout conventions. It demonstrates artifact structure and Step 01 acceptance evidence without representing a complete production application.

Full methodology reference: https://github.com/fpmcguire/mod-w

## Entrypoints

- `../AGENTS.md` is the vendor-neutral agent entrypoint read by Codex and compatible agents.
- `../CLAUDE.md` is the Claude-specific entrypoint.
- `../.codex/config.toml`, `../.claude/settings.json`, and `../.mcp.json` live at the example root.

## Canonical Documents

| Document | Purpose |
| --- | --- |
| `product.md` | What is being built, for whom, and why |
| `architecture.md` | How the example is structured |
| `domain-language.md` | Shared vocabulary |
| `roadmap.md` | Ordered delivery steps |
| `step-01.md` | Current step brief |
| `review.md` | Review findings and decision |
| `qa.md` | Verification evidence |
| `ai-agents.md` | Agent registry and role boundaries |
| `cross-validation.md` | Claude/Codex validation protocol |

## Supporting Directories

- `agents/` contains tool-neutral role definitions.
- `rules/` contains modular constraints as they become real project rules.
- `skills/` is reserved for reusable MOD-W procedures and is intentionally empty here.
- `validation/` contains independent validation outputs and discrepancy logs.
