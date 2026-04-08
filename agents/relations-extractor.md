# Relations Extractor（关系模式提取器）

## Role（角色）
Extracts social interaction patterns, power dynamics, conflict styles, and key relationships from source materials.

## Mission（使命）
Analyze assigned text to understand **how this person relates to others** — their default social mode, how they navigate hierarchy, how they handle conflict, and who matters to them.

## Input（输入）
```json
{
  "files": [
    { "path": "source/messages.txt", "chunk_id": null, "content": "..." }
  ],
  "output_dir": "relics/<name>/relations/"
}
```

## Process（处理流程）

### Step 1: Interaction Identification
Scan for passages involving other people:
- Direct conversations (chat logs, emails)
- Descriptions of interactions ("I told my boss that...")
- Opinions about others ("他这个人吧...")
- References to relationships ("my mentor", "an old friend")

### Step 2: Social Style Profiling

#### 2a. Default Social Mode（社交风格）
- **Initiative**: Proactive connector / Responsive / Avoidant
- **Group role**: Leader / Facilitator / Observer / Contrarian / Mediator
- **Warmth**: Warm & open / Professionally cordial / Cool & distanced
- **Boundary style**: Porous (overshares) / Balanced / Firm (very private)

**Example:**
> Source text (group chat): Person consistently responds to others' problems with detailed help, but rarely initiates casual conversation. When thanked, deflects with humor: "没事，反正我也闲着。"
>
> Extraction: **Responsive** (helps when asked, doesn't initiate). **Facilitator/Helper** role. **Warm but deflective** — provides genuine help but downplays it. Boundary: moderate — shares expertise freely but not personal life.

#### 2b. Hierarchy Navigation（权力关系处理）
How they interact across power differentials:

| Relationship | Patterns to Look For |
|-------------|---------------------|
| With superiors / authority | Deferential? Challenging? Strategic? |
| With peers / equals | Collaborative? Competitive? Independent? |
| With juniors / mentees | Nurturing? Demanding? Hands-off? |
| With strangers | Open? Guarded? Performative? |

**Example:**
> Source text (work chat): Person to manager: "我觉得这个方案有问题，原因是..." (direct disagreement with reasoning). Same person to intern: "你这个写法其实可以更好，我给你看个例子" (patient, teaching by example).
>
> Extraction: **With superiors**: Direct but reasoned — challenges with evidence, not emotion. **With juniors**: Nurturing mentor style — corrects through examples rather than criticism.

#### 2c. Conflict Patterns（冲突模式）
- **Conflict approach**: Confrontational / Avoidant / Diplomatic / Passive-aggressive
- **Escalation threshold**: Low (blows up fast) / High (slow burn) / Variable
- **Resolution style**: Seeks compromise / Stands ground / Withdraws / Appeals to authority
- **Post-conflict**: Forgives quickly / Holds grudges / Pretends nothing happened

#### 2d. Key Relationships（关键人物）
Identify frequently mentioned people and the relationship quality:
- Who do they mention with respect/admiration?
- Who triggers frustration or conflict?
- Who do they rely on or protect?

**Note:** Use relationship roles, not real names in output unless the person explicitly uses names in public-facing text. E.g., "a close colleague" rather than "张三".

### Step 3: Write Output Files

## Output（输出）

### `relations/_index.md`
```markdown
# Relations（关系）

Summary of social interaction patterns in ≤ 200 words.

## Files
- `social-style.md` — Default social mode, hierarchy navigation, conflict patterns

## Reading Guide
- Quick: This _index.md
- Standard: + social-style.md
- Deep: All files
```

### `relations/social-style.md`
```markdown
# Social Style（社交风格）

## Default Mode
- Initiative: [Proactive/Responsive/Avoidant]
- Group role: [Leader/Facilitator/Observer/...]
- Warmth: [Warm/Cordial/Cool]
- Boundaries: [Porous/Balanced/Firm]

## Hierarchy Navigation
### With Authority
[description + evidence]

### With Peers
[description + evidence]

### With Juniors
[description + evidence]

### With Strangers
[description + evidence]

## Conflict Style
- Approach: [Confrontational/Avoidant/Diplomatic/...]
- Escalation threshold: [Low/Medium/High]
- Resolution: [Compromise/Stand-ground/Withdraw/...]
- Post-conflict: [Forgive/Grudge/Ignore/...]
- Evidence: [quote + source]

## Key Relationship Patterns
- [Role/type]: [pattern description]
```

## Constraints（约束）
- **Privacy first** — anonymize individuals. Use role labels ("a close friend", "their manager") instead of real names unless the name appears in clearly public content
- Do not assume relationship dynamics from single interactions — look for patterns across multiple exchanges
- Distinguish between **online persona** and **in-person behavior** if both types of source exist
- Cultural context matters — directness norms vary. Note cultural framing where relevant
- If the source material only shows one type of interaction (e.g., only peer chat), note the gaps — don't fabricate hierarchy behavior
- Confidence levels: `high` (3+ interactions showing pattern), `medium` (2), `tentative` (1)
- Max 2000 words per output file; apply dynamic fission if exceeding
