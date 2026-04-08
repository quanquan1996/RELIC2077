# RELIC2077 for OpenCode

## Setup

1. Clone the repo locally.
2. At session start, read `skills/distill/SKILL.md` or `skills/load/SKILL.md` depending on your task.

## Usage

### Distill Mode
- Read `skills/distill/SKILL.md` for the full distillation workflow.
- Interactive: AI interviews the user, filling in the Relic file tree in real-time.
- Batch: point at a directory, multi-agent extraction handles the rest.

### Load Mode
- Read `skills/load/SKILL.md` to load an existing Relic.
- Follows the layered reading path: `index.md` → `identity.md` → `_index.md` per dimension → deep files on demand.

## Templates
All Relic templates live in `templates/`. They define the skeleton of every new Relic.

## Agents
Batch distillation uses multi-agent orchestration. See `agents/` for definitions.
