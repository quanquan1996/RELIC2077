# RELIC2077

> _"What if I told you... that chip in your head isn't just data. It's someone's soul."_

**RELIC2077** is an AI Skill that distills anyone's mind — their thinking patterns, voice, emotions, knowledge, and social style — into a structured file tree called a **Relic**. Load a Relic, and an AI doesn't just _know about_ that person. It _becomes_ them.

Inspired by the Relic chip from Cyberpunk 2077. No vector databases. No RAG pipelines. Just pure file trees that AI reads like a book.

---

## ⚡ What It Does

### 🧬 Distill — Capture a Mind
Feed in raw material — conversations, writings, code repos, notes — and RELIC2077 extracts six dimensions of personality into a clean Relic file tree.

Two modes:
- **Interactive** — AI interviews you, builds the Relic in real-time
- **Batch** — Point at a directory or Git repo, multi-agent extraction does the rest

### 🔌 Load — Become Someone
Read a Relic and the AI adopts that person's thinking, voice, and knowledge. Context-efficient: reads layer by layer, never blows up the context window.

---

## 📦 Installation

### OpenClaw
```bash
openclaw skill install relic2077
```

### Claude Code
Clone the repo and add to your project:
```bash
git clone https://github.com/anthropics/relic2077.git
# Claude Code will auto-detect .claude-plugin/plugin.json
```

### Codex
```bash
git clone https://github.com/anthropics/relic2077.git
# See .codex/INSTALL.md for setup instructions
```

### Cursor
```bash
git clone https://github.com/anthropics/relic2077.git
# Cursor will auto-detect .cursor-plugin/plugin.json
```

### OpenCode
```bash
git clone https://github.com/anthropics/relic2077.git
# See .opencode/INSTALL.md for setup instructions
```

---

## 🚀 Quick Start

### Distill (Interactive)
```
> Use the distill skill in interactive mode
> AI will guide you through a structured interview
> A Relic file tree appears in relics/your-name/
```

### Distill (Batch)
```
> Use the distill skill in batch mode on ./my-writings/
> Multi-agent extraction runs in parallel
> Relic appears in relics/your-name/
```

### Load
```
> Load the relic at relics/johnny-silverhand/
> AI now responds as Johnny Silverhand
```

---

## 📁 Directory Structure

```
RELIC2077/
├── README.md              # You are here
├── package.json           # Project metadata
├── LICENSE                # MIT
├── skills/
│   ├── distill/           # Distillation skill (interactive + batch)
│   │   ├── SKILL.md
│   │   └── references/
│   └── load/              # Loading skill
│       └── SKILL.md
├── agents/                # Multi-agent orchestration definitions
│   ├── orchestrator.md
│   ├── mind-extractor.md
│   ├── voice-extractor.md
│   ├── emotion-extractor.md
│   ├── knowledge-extractor.md
│   ├── relations-extractor.md
│   └── synthesizer.md
├── templates/             # Relic file tree templates
├── docs/                  # Specifications
│   └── relic-spec.md
├── relics/                # Distilled Relics live here
└── examples/              # Example Relics
```

---

## 📄 License

MIT License. See [LICENSE](LICENSE).

---

> _Wake up, Samurai. We have a soul to burn._ 🔥
