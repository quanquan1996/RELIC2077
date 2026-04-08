# Dimension Definitions (维度定义)

The six dimensions form the skeleton of every Relic. Five are fixed; the sixth is elastic.

---

## 1. Mind (思维)

**Directory:** `mind/`

**Definition:** How this person thinks — their cognitive patterns, mental models, values, worldview, and blind spots. This is the **operating system** of the personality.

**Boundary:** Mind covers *how* they process, not *what* they know (that's Knowledge) or *how they say it* (that's Voice).

**Typical contents:**
- `thinking-patterns.md` — Decision-making process, analytical vs. intuitive, first-principles vs. pattern-matching
- `values.md` — Core beliefs, non-negotiables, moral framework
- `worldview.md` — How they see the world, optimism/pessimism, agency vs. determinism
- `blind-spots.md` — Self-identified or observed gaps in thinking
- `mental-models.md` — Frameworks they rely on (if enough material)

**Quality bar:** A reader should be able to predict how this person would approach a novel problem they've never seen before.

---

## 2. Voice (表达)

**Directory:** `voice/`

**Definition:** How this person expresses themselves — language style, tone, verbal habits, humor, register shifts across contexts.

**Boundary:** Voice is about *form*, not *content*. "They believe in honesty" → Mind. "They say 'honestly' before every opinion" → Voice.

**Typical contents:**
- `style.md` — Overall communication style (direct/diplomatic, formal/casual, verbose/terse)
- `catchphrases.md` — Repeated phrases, verbal tics, signature expressions
- `humor.md` — Type of humor (sarcastic, dry, absurdist, self-deprecating), when they deploy it
- `register.md` — How their voice changes between contexts (work vs. friends vs. strangers)
- `languages.md` — Languages used, code-switching patterns (if multilingual)

**Quality bar:** An AI loading this dimension should be able to write a paragraph that "sounds like" the person to someone who knows them.

---

## 3. Emotion (情感)

**Directory:** `emotion/`

**Definition:** The person's emotional landscape — baseline temperament, what triggers strong reactions, how they cope, and how they express (or suppress) feelings.

**Boundary:** Emotion is about *feeling states and patterns*, not opinions (Mind) or how feelings are verbalized (Voice).

**Typical contents:**
- `temperament.md` — Baseline emotional state, energy level, stability
- `triggers.md` — What reliably provokes anger, joy, anxiety, excitement
- `coping.md` — Stress responses, self-soothing patterns, healthy and unhealthy
- `attachment.md` — How they bond, separation anxiety, independence (if enough signal)
- `vulnerability.md` — Fears, insecurities, soft spots

**Quality bar:** A reader should understand what makes this person light up, shut down, or explode — and roughly how they'd handle a crisis.

---

## 4. Knowledge (知识)

**Directory:** `knowledge/`

**Definition:** What this person knows deeply — professional expertise, hobby mastery, intellectual interests, and their relationship with information.

**Boundary:** Knowledge is about *domains and depth*, not how they acquired it (Mind) or how they explain it (Voice).

**Typical contents:**
- `domains.md` — Map of expertise areas with depth indicators (novice → expert)
- `professional.md` — Work-related knowledge, industry insights, contrarian takes
- `interests.md` — Non-professional deep interests, nerd territories
- `information-diet.md` — How they consume information, trusted sources
- `{specific-domain}.md` — Detailed knowledge in a specific area (if rich enough to warrant its own file)

**Quality bar:** A reader should know what topics this person can speak authoritatively on, and where their knowledge drops off.

---

## 5. Relations (关系)

**Directory:** `relations/`

**Definition:** How this person relates to others — social style, trust patterns, group dynamics, and the shape of their social world.

**Boundary:** Relations is about *interpersonal patterns*, not feelings about people (Emotion) or communication style (Voice).

**Typical contents:**
- `social-style.md` — Introvert/extrovert, social energy, approach to strangers
- `trust.md` — How trust is built and broken, loyalty patterns
- `roles.md` — Typical role in groups (leader, mediator, observer, provocateur)
- `key-relationships.md` — Important relationship archetypes (not specific people unless volunteered)
- `boundaries.md` — Where they draw lines, deal-breakers in relationships

**Quality bar:** A reader should be able to predict how this person would behave at a dinner party, in a team meeting, and in a one-on-one conflict.

---

## 6. Custom Dimensions (自定义维度)

**Directory:** `{custom-name}/`

**Definition:** Elastic extension for content that doesn't fit the five core dimensions but is central to who this person is.

### When to Create a Custom Dimension
- Content is **substantial** (enough for 500+ chars of meaningful material)
- Content doesn't fit naturally into any core dimension
- The content is **identity-defining** — removing it would leave the Relic incomplete

### Common Custom Dimensions
| Name | When to use |
|------|------------|
| `aesthetics/` | Strong design/art/taste opinions that define them |
| `spirituality/` | Faith, philosophy, or existential framework is central |
| `ambition/` | Goals, drive, and vision are a defining trait |
| `craft/` | A specific practice or discipline is core to identity |
| `creativity/` | Creative process and output are central |
| `health/` | Physical/mental health is a major life theme |

### Rules for Custom Dimensions
- Follow the same structure: `_index.md` + content files
- Register in `manifest.json` under `dimensions`
- Keep to 1–3 custom dimensions max — if you need more, some content probably belongs in a core dimension

---

## Dimension Relationships & Overlap Handling (维度间关系)

Dimensions are not hermetic. Content often touches multiple dimensions. Rules:

1. **Primary home** — Every piece of content has ONE primary dimension. Place it there.
2. **Cross-references** — If content is relevant to another dimension, add a brief reference: `(→ see also: voice/humor.md)`
3. **Overlap resolution:**
   - "They value directness" → **Mind** (it's a value)
   - "They speak very directly" → **Voice** (it's expression style)
   - "Indirect people annoy them" → **Emotion** (it's a trigger)
   - "They're known as the blunt one in the group" → **Relations** (it's a social role)
4. **When genuinely ambiguous** — Put it where it provides the most context for that dimension's narrative.

---

## Quality Standards (质量标准)

### Per-Dimension Minimums
| Level | Criteria |
|-------|---------|
| **Thin** | < 500 chars, vague generalities. Flag for supplementation. |
| **Adequate** | 500–1500 chars, 2+ concrete examples or specific patterns. |
| **Rich** | 1500+ chars, multiple concrete examples, nuanced patterns, contradictions acknowledged. |

### Overall Relic Quality
- At least 4/5 core dimensions should be **Adequate** or better.
- No dimension should be completely empty (even "thin" with a note is better).
- Custom dimensions only if they meet the **Adequate** bar.

### Anti-Patterns to Avoid
- ❌ Generic filler ("They are a good communicator") — push for specifics
- ❌ Resume language ("Experienced leader with proven track record") — capture the person, not the brand
- ❌ Contradictions without context — if they contradict themselves, explain the tension
- ❌ Hallucinated content — every claim must trace to source material or direct statement
