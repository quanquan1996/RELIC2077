# Batch Distillation Orchestration Guide (批量蒸馏编排指南)

This guide covers extracting a Relic from a corpus of files using multi-agent parallel processing.

## Phase 1: Directory Scanning (目录扫描)

### Scan Strategy
1. **Inventory** — Recursively list all files in the target directory.
2. **Filter** — Exclude binary files, node_modules, .git, build artifacts, and other noise.
3. **Classify** each file:

| Type | Extensions | Handling |
|------|-----------|----------|
| Prose | `.md`, `.txt`, `.rst`, `.org` | Direct extraction — richest signal |
| Structured | `.json`, `.yaml`, `.csv`, `.toml` | Parse structure, extract preferences & patterns |
| Code | `.js`, `.py`, `.rs`, `.go`, etc. | Extract thinking patterns, technical preferences, comments |
| Chat logs | `.log`, chat exports | High-value for voice, emotion, relations |
| Other | images, PDFs, etc. | Skip or note as "unprocessed" |

4. **Size assessment** per file:
   - **< 50KB** → Assign whole file to extractors
   - **50KB–200KB** → Slice into ≤50KB chunks with overlap
   - **> 200KB** → Multi-round processing, slice into ≤50KB segments

5. **Output** a scan manifest:
```
Files found: N
Processable: N (X MB total)
Skipped: N (binary/noise)
Estimated processing: N agent rounds
```

## Phase 2: Agent Assignment (Agent 分配)

### Assignment Logic

Each processable file/chunk is assigned to **all relevant extractors** in parallel. A single file often yields signal for multiple dimensions.

**Priority routing** (file → primary extractor):
- Personal essays, blog posts → Mind + Voice
- Chat logs, DMs → Voice + Emotion + Relations
- Technical docs, code → Knowledge + Mind
- Social media posts → Voice + Relations + Emotion
- Journals, diaries → Emotion + Mind
- Resumes, bios → Knowledge + Relations

**Rule:** Every file goes to at least 2 extractors. The orchestrator decides primary vs. secondary assignment.

### Task Packet Format
Each extractor receives a task packet:
```
Target: {relic_name}
Dimension: {mind|voice|emotion|knowledge|relations}
Source files: [{path, size, type, slice_range?}]
Output path: {relic_dir}/{dimension}/
Instructions: Extract all {dimension}-relevant content. Output as markdown.
```

## Phase 3: Parallel Execution (并行执行)

### Execution Strategy
- Spawn one sub-agent per extractor (5 agents for 5 dimensions).
- Each agent processes its assigned files independently.
- Agents write directly to the Relic dimension directory.
- **No cross-agent communication during extraction** — conflicts resolved in synthesis.

### Slicing Strategy (切片策略)
For large files that need slicing:
1. Split at natural boundaries (paragraphs, sections, message boundaries).
2. Include **200-char overlap** between slices for context continuity.
3. Each slice gets a sequence number for reassembly.
4. If a slice contains no signal for the target dimension, the extractor outputs nothing (no filler).

### Per-Agent Output
Each extractor produces:
- One or more `.md` files in the dimension directory
- A `_extraction_log.json` with:
  ```json
  {
    "dimension": "mind",
    "sources_processed": 12,
    "sources_skipped": 3,
    "confidence": "high|medium|low",
    "notes": "Sparse data on worldview; strong on decision-making"
  }
  ```

## Phase 4: Synthesis (合成流程)

The **Synthesizer** agent runs after all extractors complete.

### Synthesis Steps
1. **Collect** all extractor outputs + extraction logs.
2. **Deduplicate** — Same insight captured by multiple extractors? Keep the richest version.
3. **Conflict resolution** (冲突处理):
   - If extractors contradict each other, flag it and prefer:
     1. More recent source material
     2. Direct statements over inferred patterns
     3. Repeated patterns over one-off instances
   - Unresolvable conflicts → note both perspectives in the Relic with context.
4. **Organize** — Structure content within each dimension directory per the templates.
5. **Generate** root files:
   - `index.md` — Overall Relic summary
   - `identity.md` — Name, key identifiers, one-paragraph essence
   - `manifest.json` — Stats and metadata
6. **Generate** `_index.md` for each dimension directory.

## Phase 5: Density Check & Dynamic Splitting (密度检查 & 动态分裂)

After synthesis, scan every file:

```
for each .md file in relic:
  if character_count > 2000:  # Chinese chars
    split into subdirectory:
      original.md → original/
        _index.md (≤200 char summary + nav)
        topic-a.md
        topic-b.md
        ...
    recursively check new files
```

### Splitting Heuristics
- Split by **theme/topic**, not by arbitrary character count.
- Each sub-file should be **self-contained** — readable without siblings.
- `_index.md` must list all children with one-line descriptions.
- Aim for 500–1500 chars per sub-file (sweet spot for context loading).

## Error Handling

| Scenario | Action |
|----------|--------|
| Extractor finds zero signal | Log it, mark dimension as "thin" |
| Source file is corrupted/unreadable | Skip, log in extraction report |
| Agent times out | Retry once, then mark files as unprocessed |
| Conflicting extractions | Flag for synthesizer, use resolution rules above |
| Total content too thin for Relic | Report to user, suggest interactive mode to supplement |

## Output Checklist

Before returning the completed Relic:
- [ ] All extractor logs collected
- [ ] Synthesis complete, no unresolved conflicts
- [ ] All files under 2000-char threshold
- [ ] Every directory has `_index.md`
- [ ] `manifest.json` stats are accurate
- [ ] Root `index.md` provides coherent overview
