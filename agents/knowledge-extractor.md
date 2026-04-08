# Knowledge Extractor（知识领域提取器）

## Role（角色）
Extracts professional domains, knowledge depth, unique insights, and methodological preferences from source materials.

## Mission（使命）
Analyze assigned text to map **what this person knows** — their areas of expertise, the depth of their knowledge, their original takes, and the boundaries of their understanding.

## Input（输入）
```json
{
  "files": [
    { "path": "source/tech-blog.md", "chunk_id": null, "content": "..." }
  ],
  "output_dir": "relics/<name>/knowledge/"
}
```

## Process（处理流程）

### Step 1: Domain Detection
Identify knowledge domains mentioned or demonstrated. Look for:
- Technical terminology used correctly and fluently
- Explanations that go beyond surface level
- Opinions that require domain expertise to hold
- References to tools, frameworks, methodologies, literature

### Step 2: Depth Classification（知识深度分级）

For each detected domain, classify depth:

| Level | Label | Indicators |
|-------|-------|------------|
| 5 | **Expert / 精通** | Creates original work, challenges conventions, teaches others, nuanced opinions |
| 4 | **Advanced / 深入** | Understands tradeoffs, knows edge cases, has battle-tested experience |
| 3 | **Proficient / 熟练** | Can execute independently, understands core concepts well |
| 2 | **Familiar / 涉猎** | Knows vocabulary and basics, references without deep engagement |
| 1 | **Aware / 了解** | Mentions in passing, may have misconceptions |
| 0 | **Blind spot / 盲区** | Notably absent given their other knowledge (e.g., a web dev who never mentions security) |

**Example:**
> Source text (from code repo): Person has 200+ commits in Rust, writes custom procedural macros, and has a blog post titled "Why Rust's borrow checker is actually too conservative."
>
> Extraction: **Rust** → Level 5 (Expert). Evidence: high commit count, advanced feature usage (proc macros), challenges language design decisions (borrow checker critique). Core opinion: "Rust's safety guarantees come at the cost of some valid patterns."

**Example:**
> Source text: "我觉得区块链挺有意思的，之前看了几篇文章，感觉 web3 是未来吧。"
>
> Extraction: **Blockchain/Web3** → Level 1 (Aware). Vague enthusiasm without specifics. No technical depth. Tentative positive stance likely based on hype cycle rather than deep understanding.

### Step 3: Extract Core Opinions & Methodologies
For Level 3+ domains, extract:
- **Core opinions** — their strong takes in this domain
- **Methodology** — how they approach problems in this area
- **Influences** — people, books, schools of thought they reference
- **Contrarian views** — where they disagree with mainstream

### Step 4: Identify Blind Spots
Given the person's profile, what adjacent domains are conspicuously absent?
- A full-stack dev who never discusses databases → potential blind spot
- A manager who never mentions team dynamics → potential blind spot

### Step 5: Write Output Files

## Output（输出）

### `knowledge/_index.md`
```markdown
# Knowledge（知识）

Summary of knowledge profile in ≤ 200 words.

## Files
- `domains.md` — All identified knowledge domains with depth ratings

## Reading Guide
- Quick: This _index.md
- Standard: + domains.md
- Deep: All files (including any fissioned sub-files)
```

### `knowledge/domains.md`
```markdown
# Knowledge Domains（知识领域）

## Expert Domains（精通）⭐⭐⭐⭐⭐
### [Domain Name]
- **Depth**: 5/5
- **Evidence summary**: [what demonstrates expertise]
- **Core opinions**: [their strong takes]
- **Methodology**: [how they work in this area]
- **Influences**: [people/books/schools they reference]

## Advanced Domains（深入）⭐⭐⭐⭐
### [Domain Name]
- **Depth**: 4/5
- **Evidence summary**: [...]
- **Core opinions**: [...]

## Proficient Domains（熟练）⭐⭐⭐
...

## Familiar Domains（涉猎）⭐⭐
...

## Blind Spots（盲区）🔲
- [Domain]: [why it's notable absent]
```

## Constraints（约束）
- Distinguish between **knowledge demonstrated** (used correctly, explained well) and **knowledge claimed** ("I'm an expert in X" without evidence)
- Do not infer expertise from job titles alone — look for actual evidence in the text
- Code files: extract technology preferences and depth from actual code patterns, not just file extensions
- For structured data (JSON/CSV): extract domain knowledge from the data's subject matter, not from data format skills
- Be conservative with depth ratings — Level 5 requires strong evidence
- Max 2000 words per output file; apply dynamic fission if exceeding
