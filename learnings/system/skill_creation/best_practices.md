# best_practices.md — System / Skill Creation
# Domain: system | Topic: skill_creation | Category: best_practices
# Append-only. Never delete entries.
# Version: 1.0 | Created: Thursday, 17-Apr-2026 · IST

---

## LEARN-SKL-001
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** skill-dna, blueprint, before-writing
**Domain:** system
**Topic:** skill_creation
**Source:** General

**Context:**
Documenting the mandatory first step from CLAUDE.md hard rules.

**Learning:**
Always read SKILL-DNA-REPORT.md before creating any new skill —
no exceptions. Every element of the Skill DNA standard must be
applied: YAML frontmatter, gerund naming, 7 mandatory sections,
size limits, and the Gene 8 creation checklist.

**Why It Matters:**
Skills created without reading the DNA report inevitably miss one
or more of the 8 Gene requirements. A non-compliant skill cannot
be reliably triggered, loaded, or quality-checked by the agent.
It becomes a dead skill — present but unusable.

**Apply When:**
Every skill creation session. Before writing a single line of
the new skill file — open SKILL-DNA-REPORT.md and read all 8 Genes.
---

---

## LEARN-SKL-002
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** skill-size, decompose, resource-files
**Domain:** system
**Topic:** skill_creation
**Source:** General

**Context:**
Documenting the size limit enforcement from Gene 5 of SKILL-DNA-REPORT.md.

**Learning:**
If any SKILL.md file grows beyond 500 lines or 20,000 characters,
decompose it immediately. Move phase-specific content to resource files.
Never delete the content — it moves to `resources/`, never disappears.

**Why It Matters:**
An oversized SKILL.md is always loaded, meaning every token in the
oversized file is consumed on every task that triggers the skill.
Decomposing keeps the SKILL.md lean and only loads the overflow
content when that specific phase needs it.

**Apply When:**
End of every session — check all skill files touched during the session.
If any exceeds 500 lines → decompose before closing the session.
---

---

## LEARN-SKL-003
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** gerund-naming, trigger-keywords, yaml
**Domain:** system
**Topic:** skill_creation
**Source:** General

**Context:**
Documenting the YAML frontmatter requirements from Gene 2 of SKILL-DNA-REPORT.md.

**Learning:**
Skill names must be gerund form (managing-, building-, writing-, creating-).
Skill descriptions must be third-person and include specific trigger
keywords the agent can pattern-match. Vague descriptions make skills
untriggerable — the agent cannot identify when to load them.

**Why It Matters:**
The skill activation map in CLAUDE.md uses trigger keywords to route
the agent to the right skill. If the description lacks specific triggers,
the agent has no reliable way to identify when to load the skill.

**Apply When:**
Every skill description write. After drafting the description, ask:
"Could the agent match a specific user phrase to this description?"
If no — the description is too vague. Add more trigger keywords.
---
