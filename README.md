
<p align="center">
  <img src="https://img.shields.io/badge/RELIC-2077-ff003c?style=for-the-badge&labelColor=0a0a0a&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZD0iTTEyIDJMMiAyMmgyMEwxMiAyeiIgZmlsbD0iI2ZmMDAzYyIvPjwvc3ZnPg==" alt="RELIC2077" />
  <img src="https://img.shields.io/badge/License-MIT-00d4ff?style=for-the-badge&labelColor=0a0a0a" alt="License" />
  <img src="https://img.shields.io/badge/AI_Skill-Personality_Distillation-fcee09?style=for-the-badge&labelColor=0a0a0a" alt="AI Skill" />
  <img src="https://img.shields.io/badge/No_RAG-Pure_File_Tree-00ff9f?style=for-the-badge&labelColor=0a0a0a" alt="No RAG" />
</p>

<p align="center">
<pre align="center">
██████╗ ███████╗██╗     ██╗ ██████╗██████╗  ██████╗ ███████╗███████╗
██╔══██╗██╔════╝██║     ██║██╔════╝╚════██╗██╔═████╗╚════██║╚════██║
██████╔╝█████╗  ██║     ██║██║      █████╔╝██║██╔██║    ██╔╝    ██╔╝
██╔══██╗██╔══╝  ██║     ██║██║     ██╔═══╝ ████╔╝██║   ██╔╝    ██╔╝
██║  ██║███████╗███████╗██║╚██████╗███████╗╚██████╔╝   ██║     ██║
╚═╝  ╚═╝╚══════╝╚══════╝╚═╝ ╚═════╝╚══════╝ ╚═════╝    ╚═╝     ╚═╝
</pre>
</p>

<h3 align="center">
  <em>"What if I told you... that chip in your head isn't just data. It's someone's soul."</em>
</h3>

<p align="center">
  <strong>Distill any human mind into a structured file tree. Load it. Become them.</strong>
</p>

<p align="center">
  <a href="./README.zh-CN.md">🌏 中文文档</a>
</p>

---

## What Is This?

**RELIC2077** is an AI Skill that captures anyone's essence — their thinking patterns, voice, emotions, knowledge, and social style — and crystallizes it into a structured file tree called a **Relic**.

Load a Relic, and an AI doesn't just _know about_ that person. **It becomes them.**

No vector databases. No RAG pipelines. No embeddings. Just pure file trees that AI reads like a book — layered, context-efficient, and self-indexing.

> Inspired by the Relic biochip from *Cyberpunk 2077* — the engram technology that stores a human consciousness in silicon.

---

## Core Concepts

### 🧠 The Relic

A Relic is a structured file tree encoding six dimensions of a human personality:

| Dimension | Directory | What It Captures |
|-----------|-----------|-----------------|
| **Mind** | `mind/` | Thinking patterns, values, worldview, blind spots |
| **Voice** | `voice/` | Language style, catchphrases, humor |
| **Emotion** | `emotion/` | Temperament, triggers, coping mechanisms |
| **Knowledge** | `knowledge/` | Expert domains, depth of knowledge |
| **Relations** | `relations/` | Social style, key relationships |
| **Custom** | `{name}/` | Elastic extension — anything that doesn't fit above |

Every directory self-indexes with `_index.md` (summary + navigation + reading advice), so AI loads context layer by layer — never blowing up the context window.

### ⚡ Two Operations

| | Distill | Load |
|---|---------|------|
| **What** | Extract a mind into a Relic | Read a Relic, become that person |
| **Input** | Conversations, writings, repos, notes | A Relic file tree |
| **Output** | A complete Relic file tree | AI embodying the persona |

---

## Distillation Modes

### 🎙️ Interactive Mode
AI interviews you through a structured conversation, building the Relic in real-time. Warm but efficient — not an interrogation.

### 📦 Batch Mode
Point at a directory or Git repo. A multi-agent swarm (7 specialized agents) scans your materials in parallel and extracts all six dimensions simultaneously.

### 🔀 Hybrid Mode
Batch-process your files first, then AI interviews you to fill the gaps. Best of both worlds.

---

## Clone vs Fork — Choose Your Path

> **This is the most important decision you'll make.**

RELIC2077 supports two usage patterns with fundamentally different privacy models:

### 🔒 Clone — Private Distillation

```bash
git clone https://github.com/anthropics/relic2077.git
```

- Your distilled Relics stay **local** — never uploaded anywhere
- The `relics/` directory is in `.gitignore` by default
- **Best for:** You want to distill yourself but keep your data private
- **Your Relic lives and dies on your machine**

> Think of it as an air-gapped engram. Your soul, your rules.

### 🌐 Fork — Public Distillation

```
Fork this repo → Distill → Push → Share
```

1. Fork RELIC2077 to your own GitHub account
2. Clone your fork locally
3. Run distillation — Relic appears in `relics/`
4. Remove `relics/` from `.gitignore` (or add your specific Relic path)
5. Commit and push to **your** fork
6. Anyone can clone your fork and `load` your Relic

- **Best for:** You want to share your digital twin with the world
- **Community power:** Fork each other's repos, load each other's Relics
- **Build your engram network**

> Your consciousness, open-sourced. Let others run your soul.

---

## Installation

### OpenClaw (Recommended)
```bash
openclaw skill install relic2077
```

### Claude Code
```bash
git clone https://github.com/anthropics/relic2077.git
# Auto-detected via .claude-plugin/plugin.json
```

### Codex
```bash
git clone https://github.com/anthropics/relic2077.git
# See .codex/INSTALL.md for setup
```

### Cursor
```bash
git clone https://github.com/anthropics/relic2077.git
# Auto-detected via .cursor-plugin/plugin.json
```

### OpenCode
```bash
git clone https://github.com/anthropics/relic2077.git
# See .opencode/INSTALL.md for setup
```

---

## Quick Start

### Distill (Interactive)
```
> Use the distill skill in interactive mode
> AI guides you through a structured interview
> Relic appears in relics/your-name/
```

### Distill (Batch)
```
> Use the distill skill in batch mode on ./my-writings/
> Multi-agent extraction runs in parallel
> Relic appears in relics/your-name/
```

### Load a Relic
```
> Load the relic at relics/johnny-silverhand/
> AI now responds as Johnny Silverhand
```

---

## Project Structure

```
RELIC2077/
├── README.md               # You are here
├── README.zh-CN.md         # 中文文档
├── package.json            # Project metadata
├── LICENSE                 # MIT
├── .gitignore              # relics/ excluded by default
├── skills/
│   ├── distill/            # Distillation skill
│   │   ├── SKILL.md        #   Interactive + Batch + Hybrid modes
│   │   └── references/     #   Interview framework, dimensions spec
│   └── load/               # Loading skill
│       └── SKILL.md        #   Persona activation protocol
├── agents/                 # Multi-agent orchestration (7 agents)
│   ├── orchestrator.md     #   Task distribution & coordination
│   ├── mind-extractor.md   #   Thinking patterns extraction
│   ├── voice-extractor.md  #   Language style extraction
│   ├── emotion-extractor.md#   Emotional patterns extraction
│   ├── knowledge-extractor.md # Domain knowledge extraction
│   ├── relations-extractor.md # Social patterns extraction
│   └── synthesizer.md      #   Merge, deduplicate, validate
├── templates/              # Relic file tree templates
├── docs/
│   └── relic-spec.md       # Full Relic format specification
├── relics/                 # Your distilled Relics (git-ignored)
└── examples/               # Example Relics
```

---

## Contributing

RELIC2077 is open to contributions. Whether it's improving extraction quality, adding new dimension types, or building tools around the Relic format:

1. Fork the repo
2. Create a feature branch
3. Make your changes
4. Submit a PR

See [docs/relic-spec.md](docs/relic-spec.md) for the full file format specification.

---

## License

[MIT](LICENSE) — Do whatever you want. Just don't sell someone's soul without their consent.

---

<p align="center">
  <em>"Wake up, Samurai. We have a soul to burn."</em> 🔥
</p>

<p align="center">
  <sub>Built for the age of digital consciousness. No RAG. No vectors. Just file trees and fire.</sub>
</p>
