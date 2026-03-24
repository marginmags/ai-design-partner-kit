---
name: skill-writing
description: >
  How to write, refine, and evaluate skills. Read this skill when creating a new
  skill, editing an existing one, choosing a model recommendation, or auditing
  skill quality. This is the meta-skill — the skill about skills.
model: opus
---

# Writing Skills

## What a Skill Is

A skill is a focused instruction set that tells Claude how to handle a specific domain. It's not documentation — it's an operating manual. Every skill should answer: "when this situation comes up, what do I do?"

Skills are read by Claude, not humans. Write for how Claude processes text, not how a person would read a wiki page.

---

## Structure

Every skill file lives at `.claude/commands/<skill-name>/SKILL.md` and starts with frontmatter:

```yaml
---
name: skill-name
description: >
  Trigger-rich description. List the specific situations, words, and decisions
  that should cause this skill to be loaded. Be specific, not generic.
model: sonnet | opus | haiku
---
```

### Frontmatter rules
- **name** — kebab-case
- **description** — the most important field. It determines when the skill gets loaded. Pack it with trigger words and situations. Don't be generic ("handles design stuff") — be specific ("Read this when making decisions about component spacing, color usage, or visual hierarchy")
- **model** — which Claude model processes this skill best (see Model Selection below)

---

## Line Count

- **Target: 50–150 lines**
- Under 50: probably too vague to be actionable
- Over 150: split into two skills or trim

**Splitting skills:** Don't pre-split. Draft the skill first, then check length. If it exceeds 150 lines, split by domain:
- **Product vision** stays as the north star (what + who + why)
- **Personas** split out if there are 2+ detailed profiles
- **Architecture** splits out if there are real technical constraints
- **Design system** splits out if there are visual rules, tokens, or component patterns
- If it's simple and fits in one skill, leave it as one

---

## Writing for Claude

**Do:**
- Lead with rules, not context — Claude doesn't need a preamble
- Use bullet points over paragraphs — each bullet = one instruction
- Bold the key phrase in each rule — Claude anchors on bold text
- Use "when X, do Y" patterns — these map to how Claude decides
- Put the most important rules first — earlier content gets more weight
- Make instructions actionable with specific triggers

**Don't:**
- Repeat the same idea in different words — dilutes rather than reinforces
- Write long narrative paragraphs — break into discrete points
- Include context that lives better elsewhere (decisions → worklog, working style → second brain)
- Use hedging language ("consider," "might want to") — be direct

---

## Model Selection Guide

| Model | Use when | Examples |
|---|---|---|
| **Opus** | Nuanced judgment, creative synthesis, ambiguity, cross-domain reasoning | Second brain, skill-writing, vision, strategy |
| **Sonnet** | Pattern-matching, consistent rule application, structured output | Personas, architecture, design system |
| **Haiku** | Simple lookups, formatting, mechanical transformations | Worklog formatting, templates |

**The test:** If the skill requires Claude to *interpret and weigh competing priorities*, use Opus. If it requires *following defined rules consistently*, use Sonnet. If it's mostly *templates and formatting*, Haiku.

---

## Refinement Workflow

1. **Draft** — write the full skill, erring on the side of too much
2. **Scan for contradictions** — check against other skills
3. **Trim redundancy** — if two bullets say the same thing, keep the stronger one
4. **Check line count** — target 50–150
5. **Designer review** — show the skill for feedback
6. **Final scan** — one last check after edits

---

## What Does NOT Belong in a Skill

| Content type | Where it belongs |
|---|---|
| How Claude works with the designer | `second-brain` skill |
| Decisions made in a session | Worklog |
| Temporary task tracking | Todo list (within session) |
| Code patterns and conventions | Derive from codebase |

---

## Auditing Existing Skills

When reviewing a skill for quality, check:

- [ ] Description is trigger-rich (would Claude know when to load this?)
- [ ] Line count is 50–150
- [ ] No content that belongs in another skill or in the worklog
- [ ] Rules are actionable ("when X, do Y") not descriptive ("X is important")
- [ ] Bold text highlights the key phrase in each rule
- [ ] `model` is set and justified
- [ ] No contradictions with other skills
- [ ] Aligns with the current product vision
