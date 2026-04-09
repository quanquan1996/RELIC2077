# Distill — Relic Extraction Skill (蒸馏技能)

## Description
Distill extracts a person's essence — thoughts, voice, emotions, knowledge, relationships — from conversations or source materials and crystallizes them into a structured **Relic** file tree. Inspired by the Relic chip from Cyberpunk 2077.

**Trigger phrases:** "distill", "蒸馏", "extract relic", "create relic", "build relic", "capture personality", "记录人格"

## Quick Start (快速开始)

```
蒸馏 <名字>              → 交互式采访，通过对话提取人格
从 <目录> 蒸馏 <名字>     → 批量提取，从文件中自动提取
从 <目录> 蒸馏 <名字>，缺的问我  → 混合模式
```

## Pre-Execution Protocol (执行前协议)

**MANDATORY: Never start extraction immediately. Always complete the following steps first.**

### Step 1: Clarify Requirements (澄清需求)

Ask the user to confirm:
- **Who** — The target person/persona to distill. Is this a real person, a historical figure, a fictional character, or an abstract methodology?
- **Source** — Where does the raw material come from? (conversation, directory, repo, URL, or a mix)
- **Scope** — Are all six dimensions needed, or only specific ones? Any custom dimensions?
- **Known context** — For well-known figures (historical, public), what does the LLM already know? What is unique in the source material that the LLM does NOT know? (Avoid redundant extraction of common knowledge.)
- **Output location** — Default is `{skill_dir}/relics/{name}/`, confirm or override.
- **Language** — Output in Chinese, English, or mixed?

### Step 2: Determine Mode (确定模式)

| Signal | Mode |
|--------|------|
| User wants to answer questions / have a conversation | **Interactive** (交互式) |
| User points to a directory, repo, or file collection | **Batch** (批量式) |
| User provides some files AND wants to fill gaps via Q&A | **Hybrid** (混合) |

If ambiguous, ask:
> I can distill a Relic in two ways: **interview you** directly, or **scan your files/repos**. Which do you prefer? (Or both?)

### Step 3: Present Plan (展示计划)

**For Interactive mode:**
- List the dimensions to cover and estimated number of questions.
- Propose interview order (e.g., "Mind first, then Voice, then...").
- Estimate time: "~15 minutes for a basic Relic, ~30 for a rich one."

**For Batch mode:**
- Run Step 1 of the batch flow (Scan & Inventory) — metadata only.
- Generate `.distill-spec.md` — the full execution plan.
- Present the spec summary to the user:
  - How many files, total size
  - Which dimensions will be extracted
  - How many parallel agents
  - Expected output structure
- **Wait for explicit user confirmation before proceeding.**

**For Hybrid mode:**
- Present both the batch scan plan AND which dimensions will likely need interactive supplementation.

### Step 4: Get Explicit Confirmation (获取确认)

**Do NOT proceed until the user explicitly says to go ahead.** Acceptable confirmations:
- "好的，开始" / "确认" / "go" / "执行" / "开始蒸馏"
- Or the user modifies the plan and then confirms.

**If the user says "直接做" or similar at the very start**, still complete Steps 1-3 but compress them into a single concise summary + confirmation request. Never skip the plan entirely.

## Output Location (产物存放)

All Relic artifacts go to:
```
{skill_dir}/relics/{name}/
```
Where `{skill_dir}` is this skill's directory and `{name}` is a slugified identifier (e.g. `zhang-san`, `linus`).

## Interactive Mode (交互式)

Reference: [`references/interview.md`](references/interview.md)

### Flow
1. **Read** [`references/dimensions.md`](references/dimensions.md) — understand the six dimensions to collect.
2. **Follow** [`references/interview.md`](references/interview.md) — structured interview framework.
3. **Write incrementally** — after each dimension segment, write/update the corresponding Relic file.
4. **Gap detection** — after the main interview, scan for thin dimensions and ask follow-up questions.
5. **Confirmation** — present a summary, get user sign-off, then run validation.

### Guidelines
- Be warm but efficient. This is an interview, not an interrogation.
- Write files as you go — don't wait until the end.
- If the user gets tired, save progress and offer to continue later.

## Batch Mode (批量式)

Reference: [`references/batch.md`](references/batch.md)

### Flow
1. **Scan & Inventory** — List all files with sizes (metadata only, do NOT read content yet). Output a scan manifest.
2. **Generate Spec** — Write `.distill-spec.md` to the output directory. This is the execution plan: file inventory, dimension assignments, token budgets, expected outputs. Review before proceeding.
3. **Pre-read** — Orchestrator reads ALL processable files using the `read` tool (not shell commands, to avoid CJK encoding issues). Store content in memory.
4. **Refine Spec** — After reading content, update the spec if assignments need adjustment.
5. **Assign & Embed** — Build task packets with **file content embedded inline**. Extractors never read from disk.
6. **Execute** — Spawn extractors in parallel via sub-agents. Update spec with status (⏳/✅/❌).
7. **Synthesize** — the synthesizer agent merges outputs, resolves conflicts, generates `index.md` and `manifest.json`.
8. **Density check** — apply dynamic splitting rules.
9. **Validate** — run the validation checklist.
10. **Finalize Spec** — Append result summary to `.distill-spec.md`.

**Key principles:**
- **Spec-driven**: The `.distill-spec.md` is written BEFORE any file reading or agent spawning. It serves as review gate, execution tracker, and audit trail.
- **No disk reads by extractors**: The orchestrator pre-reads everything and delivers content in task packets. This avoids encoding issues and redundant I/O.

### Agent Roster
| Agent | File | Role |
|-------|------|------|
| Orchestrator | `agents/orchestrator.md` | Scans, assigns, coordinates |
| Mind Extractor | `agents/mind-extractor.md` | Thinking patterns, values, worldview |
| Voice Extractor | `agents/voice-extractor.md` | Language style, catchphrases |
| Emotion Extractor | `agents/emotion-extractor.md` | Temperament, triggers, coping |
| Knowledge Extractor | `agents/knowledge-extractor.md` | Domains, expertise depth |
| Relations Extractor | `agents/relations-extractor.md` | Social style, key relationships |
| Synthesizer | `agents/synthesizer.md` | Merge, deduplicate, validate |

## Hybrid Mode (混合模式)

1. Run **Batch** on provided files first.
2. Identify thin/empty dimensions from the batch output.
3. Run a **targeted Interactive** session covering only the gaps.
4. Re-run synthesis and validation.

## Dimensions (维度)

Reference: [`references/dimensions.md`](references/dimensions.md)

Six core dimensions, plus elastic custom dimensions:

| Dimension | Directory | What it captures |
|-----------|-----------|-----------------|
| Mind (思维) | `mind/` | Thinking patterns, values, worldview, blind spots |
| Voice (表达) | `voice/` | Language style, catchphrases, humor |
| Emotion (情感) | `emotion/` | Temperament, triggers, coping mechanisms |
| Knowledge (知识) | `knowledge/` | Expert domains, depth of knowledge |
| Relations (关系) | `relations/` | Social style, key relationships |
| Custom (自定义) | `{name}/` | Elastic — created when content doesn't fit above |

## Dynamic Splitting (动态分裂)

**Rule:** Any single file exceeding **2000 characters** (Chinese) / **2000 words** (English) must be split.

### Splitting Procedure
1. The oversized file `topic.md` becomes a directory `topic/`.
2. Create `topic/_index.md` with a ≤200-char summary + navigation to sub-files.
3. Split content into thematic sub-files within `topic/`.
4. Recursively check — if any sub-file still exceeds the threshold, split again.

### `_index.md` Format
```markdown
# {Topic} — Index

{≤200 char summary}

## Contents
- `sub-file-a.md` — one-line description
- `sub-file-b.md` — one-line description

## Reading Guide
- **Quick:** Read this index only
- **Standard:** Read this + each sub-file intro paragraph
- **Deep:** Read everything
```

## Validation Checklist (校验步骤)

Before declaring a Relic complete, verify:

- [ ] **Structure** — `index.md`, `identity.md`, `manifest.json` all exist at Relic root
- [ ] **Dimensions** — Each non-empty dimension has `_index.md` + at least one content file
- [ ] **Density** — No single file exceeds 2000-char/word threshold
- [ ] **Index consistency** — Every file is listed in its parent `_index.md`
- [ ] **Manifest accuracy** — `manifest.json` file counts and token estimates are correct
- [ ] **Readability** — A cold reader can understand the person from `index.md` → `_index.md` chain alone
- [ ] **No hallucination** — All content traces back to source material or direct user statements

## Completion Criteria (完成标准)

A Relic is **complete** when:
1. All six dimensions have been addressed (even if some are explicitly marked thin/unknown).
2. The validation checklist passes with zero failures.
3. The user (interactive) or orchestrator (batch) has confirmed the output.
4. `manifest.json` is generated with accurate stats.

Output a final summary:
```
✅ Relic distillation complete: {name}
   Dimensions: {N}/6 populated
   Files: {N} total
   Estimated tokens: ~{N}
   Location: {path}
```
