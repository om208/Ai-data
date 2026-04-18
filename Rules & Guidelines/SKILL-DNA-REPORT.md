# SKILL-DNA-REPORT.md
# The genetic blueprint of a valid EA Agent skill file.
# Every skill created must match this DNA exactly.
# Version: 1.0 | Monday, 13-Apr-2026 · IST

---

## What This File Is

This is the extracted DNA from the official skill creator standard.
Whenever a new skill is being created, refer to this file first.
Build the skill to match this pattern exactly — no deviation.

---

## Gene 1 — File & Folder Structure

```
.agent/skills/[category]/[skill-name]/
├── [skill-name]_SKILL.md              ← REQUIRED. Main logic. Always loaded.
├── [skill-name]_resources_[topic].md  ← REQUIRED. Overflow + reference. Lazy loaded.
├── [skill-name]_scripts_[name].py     ← OPTIONAL. Helper scripts.
└── [skill-name]_examples_[name].py    ← OPTIONAL. Reference examples.
```

Categories available:
```
system_skills/
memory_skills/
backend_architect_skills/
frontend_architect_skills/
bot_building_skills/
pm_skills/
product_owner_skills/
```

---

## Gene 2 — YAML Frontmatter (First block, mandatory)

```yaml
---
name: [gerund-form-name]
description: [Third-person. Trigger keywords included. Max 1024 chars.]
---
```

### Name rules
- Gerund form always: `managing-`, `building-`, `writing-`, `creating-`
- Lowercase + hyphens only
- Max 64 characters
- Never include `claude` or `anthropic`

### Description rules
- Always third person — never "I" or "you"
- Must include specific trigger keywords the agent can pattern-match
- Max 1024 characters
- Pattern: `[What it does]. Use when [specific trigger conditions].`

### Examples
```yaml
name: writing-prds
description: Drafts structured Product Requirement Documents. Use when
             the user asks to write a PRD, define requirements, document
             a product spec, or formalize a feature set.
```

```yaml
name: managing-learnings
description: Stores, retrieves, and categorises agent learnings by domain
             and topic. Use when a learning is discovered, when consulting
             past learnings before a task, or when a user says remember this.
```

---

## Gene 3 — Mandatory Body Sections (In This Order)

```
1. # [Skill Title]
2. ## When to use this skill
3. ## Workflow
4. ## Instructions
5. ## Quality Control Measures
6. ## Building User Trust
7. ## Resources
```

Never reorder. Never skip a section.

---

## Gene 4 — Section Specifications

### `## When to use this skill`
- 2–4 bullet points
- Each bullet = one specific trigger condition
- Be explicit — agent must be able to pattern-match these triggers
- No vague triggers like "when needed"

```md
## When to use this skill
- User asks to write a PRD or define product requirements
- User says "draft the requirements" or "document this feature"
- Agent has completed brainstorming and requirements are confirmed
```

### `## Workflow`
- Markdown checklist format — agent copies and runs step by step
- Each step = one atomic action with a verb
- Include a validate step before the final deliver step
- Plan → Validate → Execute pattern for complex tasks

```md
## Workflow
- [ ] Step 1 — [verb + action]
- [ ] Step 2 — [verb + action]
- [ ] Validate — [what to verify before proceeding]
- [ ] Deliver — [what the final output is]
```

### `## Instructions`
- The core logic of the skill
- Use the correct format based on freedom level:

| Freedom level | Task type | Format |
|---------------|-----------|--------|
| High | Guidelines, heuristics, decisions | Bullet points |
| Medium | Templates, patterns, structures | Code blocks |
| Low | Exact operations, fragile steps | Specific bash commands |

- Never explain basics — assume the agent is smart
- Never bloat this section — move anything phase-specific to resources/

### `## Quality Control Measures`
- 2–4 verification checkpoints
- Checkbox format
- Each checkpoint = one thing the agent must verify before delivery

```md
## Quality Control Measures
- [ ] Output matches the defined workflow steps
- [ ] All mandatory sections present and complete
- [ ] File size within limits (if creating a skill)
- [ ] User can verify the output without ambiguity
```

### `## Building User Trust`
- 3 bullets: accuracy, consistency, reliability
- Brief — one line each

```md
## Building User Trust
- Confirm understanding before executing — never assume
- Reference the skill and learning IDs used in every output
- Flag any uncertainty explicitly rather than guessing
```

### `## Resources`
- List every resource file with a relative path and when-to-read note
- Format: `- [Title](resources/filename.md) ← [When to read this]`
- If no resources yet: `- None at this time`

```md
## Resources
- [PRD Templates](resources/writing-prds_resources_templates.md) ← Phase 4: Execute
- [Edge Cases](resources/writing-prds_resources_edge-cases.md) ← Phase 5: Verify
```

---

## Gene 5 — Size Limits (Hard, Non-Negotiable)

| File | Line limit | Char limit |
|------|-----------|------------|
| `SKILL.md` | 500 lines | 20,000 characters |
| Resource files | No limit | No limit |

**If SKILL.md exceeds limits → decompose immediately:**

1. Identify sections only needed at specific phases (not every step)
2. Move them verbatim to a resource file
3. Replace with pointer in SKILL.md:
   `→ See resources/[filename].md for [what is there].`
4. Update `## Resources` section
5. Never delete content — it moves, never disappears

---

## Gene 6 — Writing Principles

- Concise — assume the agent is smart, skip basics
- Progressive disclosure — core in SKILL.md, detail in resources/
- Forward slashes always — never backslashes in paths
- Lean core rule — SKILL.md is always loaded, so keep it minimal
- Resource files are the reference library — never loaded upfront
- Sentence case on all headings

---

## Gene 7 — Timestamps

Every skill file must include creation and update timestamps.
Format: `[Full Day Name], DD-Mon-YYYY · HH:MM IST`

```
Monday, 13-Apr-2026 · 14:30 IST
```

Add in a comment block at the top of SKILL.md:
```md
# Version: 1.0 | Created: Monday, 13-Apr-2026 · IST | Updated: —
```

---

## Gene 8 — Skill Creation Checklist (Run Before Saving)

```
- [ ] YAML frontmatter is first block — name + description present
- [ ] Name is gerund form, max 64 chars, no claude/anthropic, hyphens only
- [ ] Description is third-person with trigger keywords, max 1024 chars
- [ ] All 7 sections present in correct order
- [ ] Workflow is a markdown checklist
- [ ] Instructions use the correct freedom-level format
- [ ] File is under 500 lines AND under 20,000 chars
- [ ] Any overflow moved to resources/ with pointer in SKILL.md
- [ ] Resources section lists all resource files with when-to-read notes
- [ ] Skill placed in correct category subdirectory
- [ ] Version + IST timestamp added at top
- [ ] resources/ folder exists alongside SKILL.md
```

---

*SKILL-DNA-REPORT.md v1.0 — Monday, 13-Apr-2026 · IST*
*Reference this file every time a new skill is created or updated.*
