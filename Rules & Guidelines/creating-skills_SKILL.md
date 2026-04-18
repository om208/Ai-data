---
name: creating-skills
description: Creates, structures, and saves new EA Agent skill files following
             the official SKILL-DNA-REPORT.md standard. Use when the user asks
             to build a skill, create a capability, save instructions as a skill,
             or when a recurring task pattern is identified that should be codified.
---

# Creating Skills
# Version: 1.0 | Created: Monday, 13-Apr-2026 · IST | Updated: —

## When to use this skill
- User says "create a skill", "build a skill", or "save this as a skill"
- User provides repeatable instructions that should persist across sessions
- Agent identifies a recurring task pattern worth codifying
- An existing skill needs to be updated or decomposed

## Workflow
- [ ] Read `SKILL-DNA-REPORT.md` — confirm DNA pattern before writing anything
- [ ] Identify goal and scope of the new skill
- [ ] Choose gerund-form name (max 64 chars, hyphens only, no claude/anthropic)
- [ ] Determine correct category subdirectory
- [ ] Draft YAML frontmatter — name + third-person description with triggers
- [ ] Write all 7 mandatory sections in order
- [ ] Validate — check file is under 500 lines / 20,000 chars
- [ ] If over limit → decompose: extract to resources/, add pointers
- [ ] Create resources/ folder alongside SKILL.md
- [ ] Save to `.agent/skills/[category]/[skill-name]/[skill-name]_SKILL.md`
- [ ] Immediately re-index into Context Mode MCP — mandatory
- [ ] Verify index updated before marking skill as complete
- [ ] Update skill activation map in CLAUDE.md if this is a new trigger

## Instructions

### Skill folder layout
```
.agent/skills/[category]/[skill-name]/
├── [skill-name]_SKILL.md
├── [skill-name]_resources_[topic].md
└── [skill-name]_scripts_[name].py     (optional)
```

### SKILL.md mandatory section order
```
1. YAML frontmatter
2. # Title + version comment
3. ## When to use this skill
4. ## Workflow
5. ## Instructions
6. ## Quality Control Measures
7. ## Building User Trust
8. ## Resources
```

### Format by freedom level
- High freedom (decisions, heuristics) → bullet points
- Medium freedom (templates, structures) → code blocks
- Low freedom (exact, fragile steps) → specific bash commands

### Resource pointer syntax
```
→ See `resources/[skill-name]_resources_[topic].md` for [what is there].
```

### Resource file header
```md
# [skill-name]_resources_[topic].md
## Parent skill: [skill-name]_SKILL.md
## Created: [Day, DD-Mon-YYYY · HH:MM IST]
```

## Quality Control Measures
- [ ] YAML frontmatter is the very first block — no content before it
- [ ] Name is gerund, max 64 chars, lowercase-hyphens, no claude/anthropic
- [ ] Description is third-person with specific trigger keywords
- [ ] All 7 sections present in correct order
- [ ] File is under 500 lines AND under 20,000 characters
- [ ] Every overflow section moved to resources/ with pointer in SKILL.md
- [ ] Resources section lists all resource files with when-to-read notes
- [ ] Skill is saved to correct category path

## Building User Trust
- Always read SKILL-DNA-REPORT.md first — never create from memory alone
- Always confirm skill name and category with user before saving
- Always show the created skill structure before writing to disk

## Resources
- [SKILL-DNA-REPORT.md](../../../SKILL-DNA-REPORT.md) ← Read before every skill creation
- [skill-decomposing guide](resources/creating-skills_resources_decomposing-guide.md) ← When SKILL.md exceeds size limits
