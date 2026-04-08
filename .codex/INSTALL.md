# RELIC2077 for Codex

## Setup

1. Clone the repo locally.
2. At session start, read `skills/distill/SKILL.md` or `skills/load/SKILL.md` depending on your task.

## Usage

### Distill Mode
- Read `skills/distill/SKILL.md` for the full distillation workflow.
- For interactive mode, follow the interview framework in `skills/distill/references/interview.md`.
- For batch mode, follow `skills/distill/references/batch.md`.

### Load Mode
- Read `skills/load/SKILL.md` to load an existing Relic.
- The AI reads `index.md` → `identity.md` → dimension `_index.md` files → deep-dives on demand.

## Templates
All Relic templates are in `templates/`. Use them as scaffolding when creating new Relics.

## Agents
For batch distillation, the orchestrator dispatches work to dimension-specific extractors.
See `agents/` for all agent definitions.
