---
name: managing-learnings
description: Stores, retrieves, and categorises agent learnings in a hierarchical
             domain/topic directory. Use when a learning is discovered during any
             task, when the user says remember this or store this, when consulting
             past learnings before starting a task, or when adding a learning to
             an existing skill file.
---

# Managing Learnings
# Version: 1.0 | Created: Monday, 13-Apr-2026 · IST | Updated: —

## When to use this skill
- A learning, fix, pattern, or insight is discovered during any task
- User says "remember this", "store this", or "add this to learnings"
- Phase 2 (CONSULT) — looking up past learnings before starting
- User says "add this learning to the skill files"
- End of session — extracting and storing session learnings

## Workflow

### Storing a learning
- [ ] Identify domain (e.g. `bot_building`, `product_management`)
- [ ] Identify topic within domain (e.g. `oracle_free_tier`, `prd_writing`)
- [ ] Identify category file (e.g. `best_practices.md`, `bug_fixes.md`)
- [ ] Navigate to `learnings/[domain]/[topic]/[category].md`
- [ ] Append entry using the standard format below
- [ ] Immediately re-index into Context Mode MCP — mandatory
- [ ] Verify index updated — confirm LEARN-ID is queryable
- [ ] If user says "add to skills" → also update relevant SKILL.md
- [ ] Never delete existing entries — append only

### Retrieving learnings (Phase 2 — CONSULT)
- [ ] Identify domain and topic of current task
- [ ] Query via Context Mode MCP — never read raw file directly
- [ ] Context Mode returns only matching entries from SQLite index
- [ ] Extract applicable LEARN-IDs from results
- [ ] Reference in output: `Learnings Applied: LEARN-BOT-001`

## Instructions

### Learning directory structure
```
learnings/
└── [domain]/
    └── [topic]/
        ├── best_practices.md
        ├── bug_fixes.md
        ├── efficiency_gains.md
        ├── resolving_issues.md
        └── mistakes_to_avoid.md
```

### Standard learning entry format
```md
---
## LEARN-[DOMAIN INITIALS]-[ID]
**Timestamp:** [Full Day Name, DD-Mon-YYYY · HH:MM IST]
**Keywords:** [tag1, tag2, tag3]
**Domain:** [domain]
**Topic:** [topic]
**Source:** [Brainstorm / PRD / Build / Test / General]

**Context:**
[What was happening when this was discovered]

**Learning:**
[The exact rule, fix, or insight — clear and reusable]

**Why It Matters:**
[What breaks if this is ignored]

**Apply When:**
[Exact trigger — when to recall this]
---
```

### Timestamp format — mandatory
```
Full Day Name, DD-Mon-YYYY · HH:MM IST
Monday, 13-Apr-2026 · 14:30 IST
```
- Full day name — never abbreviated
- Month abbreviated — `Apr` not `April` or `04`
- 24-hour time · IST always appended

### Two-destination rule
When user says "add to skill files":
```
Step 1 → Append to learnings/[domain]/[topic]/[category].md  (always)
Step 2 → Also update relevant SKILL.md with the learning      (additionally)
Both files coexist. Learning file is never deleted or replaced.
```

### Read routing rule — mandatory
All learning reads go through Context Mode MCP — never raw file load.
Context Mode queries SQLite and returns only matching entries.
Raw files are the source of truth for writing — Context Mode is for reading.

## Quality Control Measures
- [ ] Entry uses the standard format with all fields present
- [ ] Timestamp is in correct IST format with full day name
- [ ] Minimum 3 keywords tagged
- [ ] Domain and topic match the directory path exactly
- [ ] Entry is appended — existing entries untouched
- [ ] LEARN-ID is unique within the category file

## Building User Trust
- Always confirm domain and topic before storing — never guess the path
- Always show the LEARN-ID assigned so user can reference it later
- Always mention stored learning IDs in session output

## Resources
- [Learning categories guide](resources/managing-learnings_resources_categories-guide.md) ← When unsure which category file to use
- [Domain examples](resources/managing-learnings_resources_domain-examples.md) ← Reference for common domain/topic patterns
