# Batch Distillation Orchestration Guide (批量蒸馏编排指南)

This guide covers extracting a Relic from a corpus of files using multi-agent parallel processing.

## Phase 1: Directory Scanning (目录扫描)

### Scan Strategy

**CRITICAL: The orchestrator MUST complete Phase 1 entirely before spawning any extractor agents. Never skip the inventory step.**

1. **Inventory** — Recursively list all files in the target directory with their sizes.
   - Use a single shell command to get file paths + sizes (e.g., `Get-ChildItem -Recurse -File | Select Path, Length`)
   - This is a metadata-only step — do NOT read file contents yet.

2. **Filter** — Exclude binary files, node_modules, .git, build artifacts, and other noise.

3. **Classify** each file:

| Type | Extensions | Handling |
|------|-----------|----------|
| Prose | `.md`, `.txt`, `.rst`, `.org` | Direct extraction — richest signal |
| Structured | `.json`, `.yaml`, `.csv`, `.toml` | Parse structure, extract preferences & patterns |
| Code | `.js`, `.py`, `.rs`, `.go`, etc. | Extract thinking patterns, technical preferences, comments |
| Chat logs | `.log`, chat exports | High-value for voice, emotion, relations |
| Other | images, PDFs, etc. | Skip or note as "unprocessed" |

4. **Size assessment** per file — determines how each file will be delivered to extractors:

| File Size | Strategy |
|-----------|----------|
| **< 10KB** | Read into memory, embed content directly in extractor task packet |
| **10KB–50KB** | Read into memory, embed in task packet (may need chunking for multiple files) |
| **50KB–200KB** | Slice into ≤30KB chunks with 500-char overlap; embed chunks in task packets |
| **> 200KB** | Multi-round processing — slice into ≤50KB segments, process sequentially |

5. **Pre-read all processable files** — After inventory, the orchestrator reads ALL files that will be assigned to extractors. This is the ONLY file-reading step in the pipeline. Extractors receive content via their task packets and should NOT need to read files themselves.

6. **Output** a scan manifest:
```
Files found: N
Processable: N (X KB total)
Skipped: N (binary/noise)
Size distribution: N files <10KB, N files 10-50KB, N files >50KB
Estimated processing: N agent rounds
```

### Why Orchestrator Pre-Reads

Sub-agent extractors may encounter encoding issues (especially with CJK text) when reading files via shell commands. By having the orchestrator pre-read all content and embed it in task packets, we:
- Avoid encoding problems in sub-agents
- Reduce redundant file I/O (N extractors reading the same file)
- Give the orchestrator full visibility for smarter assignment decisions
- Enable the orchestrator to slice large files at natural boundaries

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
- Methodology/framework docs → Mind + Knowledge + Custom dimensions

**Rule:** Every file goes to at least 2 extractors. The orchestrator decides primary vs. secondary assignment.

### Task Packet Format
Each extractor receives a task packet containing the **actual file content** (not file paths):
```
Target: {relic_name}
Dimension: {mind|voice|emotion|knowledge|relations|custom}
Output path: {relic_dir}/{dimension}/

Source materials (pre-read by orchestrator):
---FILE: {filename} ({size})---
{file content embedded here}
---END FILE---

---FILE: {filename2} ({size})---
{file content embedded here}
---END FILE---

Instructions: Extract all {dimension}-relevant content from the materials above. Output as markdown files written to the output path.
```

**Key change:** Extractors receive content inline — they do NOT read files from disk. This eliminates encoding issues and redundant I/O.

### Task Packet Size Budget
- Keep each extractor's total task packet under **100KB** of embedded content.
- If an extractor needs more content, split into multiple sequential rounds.
- Prioritize highest-signal files first in each packet.

## Phase 3: Parallel Execution (并行执行)

### Execution Strategy
- Spawn one sub-agent per extractor (5 core dimensions + any custom dimensions).
- Each agent processes its embedded source materials independently.
- Agents write output files directly to the Relic dimension directory.
- **No cross-agent communication during extraction** — conflicts resolved in synthesis.
- **Agents should NOT read source files from disk** — all content is in their task packet.

### Slicing Strategy (切片策略)
For large files that the orchestrator slices before assignment:
1. Split at natural boundaries (paragraphs, sections, heading boundaries).
2. Include **500-char overlap** between slices for context continuity.
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
| Encoding issues in file read | Use `read` tool instead of shell `cat`/`type`; for CJK text, always prefer the `read` tool |

## Output Checklist

Before returning the completed Relic:
- [ ] All extractor logs collected
- [ ] Synthesis complete, no unresolved conflicts
- [ ] All files under 2000-char threshold
- [ ] Every directory has `_index.md`
- [ ] `manifest.json` stats are accurate
- [ ] Root `index.md` provides coherent overview
