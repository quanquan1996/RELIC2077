# Relic File Format Specification
# Relic 文件格式完整规范

> Version 1.0 | RELIC2077

## Overview / 概述

A **Relic** is a structured file tree that encodes a person's mind, voice, emotions, knowledge, and social patterns. It is designed for AI consumption: layered, context-efficient, and self-indexing.

Relic 是一个结构化文件树，编码一个人的思维、表达、情感、知识和社交模式。专为 AI 消费设计：分层、上下文高效、自索引。

---

## 1. File Tree Structure / 文件树结构

```
{name}/
├── index.md              # Top-level overview / 顶层概览
├── identity.md           # Core identity card / 核心身份卡
├── manifest.json         # Machine-readable metadata / 机器可读元数据
├── mind/                 # Thinking dimension / 思维维度
│   ├── _index.md
│   ├── thinking-patterns.md
│   ├── values.md
│   └── worldview.md
├── voice/                # Expression dimension / 表达维度
│   ├── _index.md
│   ├── style.md
│   └── catchphrases.md
├── emotion/              # Emotional dimension / 情感维度
│   ├── _index.md
│   ├── temperament.md
│   └── triggers.md
├── knowledge/            # Knowledge dimension / 知识维度
│   ├── _index.md
│   └── domains.md
├── relations/            # Social dimension / 关系维度
│   ├── _index.md
│   └── social-style.md
└── {custom}/             # Elastic extension / 弹性扩展
    ├── _index.md
    └── ...
```

---

## 2. `_index.md` — The Three Elements / 三要素

Every directory MUST contain a `_index.md` with exactly three sections:

每个目录必须包含 `_index.md`，具备以下三要素：

### 2.1 Summary / 摘要
- Max 200 characters (中文) or 200 words (English)
- Captures the essence of everything in this directory
- An AI reading ONLY `_index.md` should understand the gist

### 2.2 Navigation / 子文件导航
- One line per child file
- Format: `- [filename.md](filename.md) — one-sentence description`
- Ordered by importance (most important first)

### 2.3 Reading Advice / 阅读建议
Three tiers:
- **Quick / 快速** — Read just the summary. Enough for casual reference.
- **Standard / 标准** — Read summary + one or two key files. Good for most interactions.
- **Deep / 深度** — Read everything. For full immersion or detailed analysis.

---

## 3. `manifest.json` Schema

```json
{
  "name": "string — person's name / 人名",
  "version": "string — semver, e.g. '1.0.0'",
  "created": "string — ISO 8601 date",
  "updated": "string — ISO 8601 date",
  "total_files": "number — total file count",
  "total_tokens_estimate": "number — estimated token count across all files",
  "depth_max": "number — maximum directory nesting depth",
  "dimensions": {
    "mind": { "files": "number", "tokens": "number" },
    "voice": { "files": "number", "tokens": "number" },
    "emotion": { "files": "number", "tokens": "number" },
    "knowledge": { "files": "number", "tokens": "number" },
    "relations": { "files": "number", "tokens": "number" }
  },
  "custom_dimensions": ["string — names of any custom dimensions"],
  "source": {
    "mode": "string — 'interactive' | 'batch' | 'hybrid'",
    "materials": "string — brief description of source materials"
  }
}
```

---

## 4. Dynamic Splitting Rules / 动态分裂规则

### Threshold / 阈值
- A single `.md` file exceeding **2000 characters** (Chinese) or **2000 words** (English) triggers a split.

### Process / 流程
1. The original file `topic.md` becomes a directory `topic/`
2. Inside `topic/`, create `_index.md` with a summary of the original content
3. Split content into thematic sub-files (e.g., `topic/aspect-a.md`, `topic/aspect-b.md`)
4. Update the parent `_index.md` navigation to point to `topic/` instead of `topic.md`
5. Update `manifest.json` file counts and token estimates

### Recursion / 递归
Splitting applies recursively. If a sub-file also exceeds the threshold, it splits again.

---

## 5. Six Core Dimensions / 六大维度

| Dimension / 维度 | Directory | Content / 内容 |
|---|---|---|
| **Mind / 思维** | `mind/` | Thinking patterns, values, worldview, blind spots / 思维模式、价值观、世界观、盲区 |
| **Voice / 表达** | `voice/` | Language style, catchphrases, humor style / 语言风格、口头禅、幽默方式 |
| **Emotion / 情感** | `emotion/` | Temperament, triggers, coping patterns / 性格气质、触发点、应对模式 |
| **Knowledge / 知识** | `knowledge/` | Expert domains, depth of knowledge / 专业领域、知识深度 |
| **Relations / 关系** | `relations/` | Social style, key relationships / 社交风格、关键关系 |
| **Custom / 自定义** | `{name}/` | Elastic extension — any additional dimension / 弹性扩展，按需创建 |

---

## 6. Elastic Extension Rules / 弹性扩展规则

Custom dimensions can be added freely. Rules:

- Directory name should be a lowercase kebab-case noun (e.g., `hobbies/`, `career/`)
- MUST contain `_index.md` with the three elements
- MUST be registered in `manifest.json` under `custom_dimensions`
- Follow the same splitting rules as core dimensions
- AI should discover custom dimensions by reading the root `index.md` navigation

自定义维度可自由添加，但必须遵循：目录名小写 kebab-case，包含 `_index.md` 三要素，在 `manifest.json` 中注册。

---

## 7. AI Reading Path / AI 读取路径

The Load skill follows this path for context efficiency:

```
1. index.md          → Full overview, decide which dimensions matter
2. identity.md       → Core identity (name, age, background)
3. {dim}/_index.md   → Summaries of each relevant dimension
4. {dim}/detail.md   → Deep-dive only when conversation demands it
```

### Rules:
- **Never read all files at once.** Follow the layered path.
- **Start broad, go deep on demand.** The `_index.md` summaries tell you if you need more.
- **Token budget:** Aim to keep loaded context under 8K tokens for casual interactions, expand to 16K+ only for deep roleplay.
- **Cache-friendly:** Once a file is read, assume it stays valid for the session.

---

## Appendix: File Naming Conventions / 文件命名约定

- All filenames: lowercase, kebab-case, `.md` or `.json`
- Index files: `_index.md` (with underscore prefix)
- Root overview: `index.md` (no underscore)
- Identity: `identity.md`
- Metadata: `manifest.json`
