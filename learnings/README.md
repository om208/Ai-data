# Learnings — EA Agent Persistent Memory System
# Version: 1.0 | Created: Thursday, 17-Apr-2026 · IST

---

## What This Directory Is

This is the EA Agent's hierarchical learning storage.
Every insight, pattern, fix, or rule discovered during any task is stored here.
It is the agent's long-term memory across all sessions — it only grows, never shrinks.

---

## Directory Structure

```
learnings/
├── README.md                               ← This file
│
├── product_management/                     ← PM domain
│   ├── prd_writing/
│   │   ├── best_practices.md
│   │   ├── mistakes_to_avoid.md
│   │   └── efficiency_gains.md
│   ├── brainstorming/
│   │   ├── best_practices.md
│   │   └── mistakes_to_avoid.md
│   ├── feature_cards/
│   │   ├── best_practices.md
│   │   └── mistakes_to_avoid.md
│   ├── roadmap/
│   │   └── best_practices.md
│   └── vision/
│       └── best_practices.md
│
├── bot_building/                           ← Bot building domain
│   ├── oracle_free_tier/
│   │   ├── best_practices.md
│   │   └── efficiency_gains.md
│   ├── architecture/
│   │   └── best_practices.md
│   └── integrations/
│       └── best_practices.md
│
└── system/                                 ← Agent system domain
    ├── session_management/
    │   ├── best_practices.md
    │   └── mistakes_to_avoid.md
    ├── context_mcp/
    │   └── best_practices.md
    └── skill_creation/
        ├── best_practices.md
        └── mistakes_to_avoid.md
```

---

## Category Files — What Goes Where

| File | What it stores |
|---|---|
| `best_practices.md` | Patterns that work — always apply these |
| `mistakes_to_avoid.md` | Anti-patterns that caused problems — never repeat |
| `efficiency_gains.md` | Optimizations discovered — apply for performance |
| `resolving_issues.md` | Specific bug fixes or problem resolutions |
| `bug_fixes.md` | Exact technical fixes for repeating bugs |

---

## Standard Learning Entry Format

Every entry in every category file follows this exact format:

```md
---
## LEARN-[DOMAIN INITIALS]-[3-digit ID]
**Timestamp:** [Full Day Name, DD-Mon-YYYY · HH:MM IST]
**Keywords:** [tag1, tag2, tag3]
**Domain:** [e.g. product_management]
**Topic:** [e.g. prd_writing]
**Source:** [Brainstorm / PRD / Build / Test / General]

**Context:**
[What was happening when this learning was discovered — 1–2 sentences]

**Learning:**
[The exact rule, fix, or insight — clear, specific, reusable]

**Why It Matters:**
[What breaks or goes wrong if this is ignored]

**Apply When:**
[Exact trigger condition — when to recall and apply this learning]
---
```

---

## LEARN-ID Naming Convention

| Domain | Prefix | Example |
|---|---|---|
| product_management | PM | LEARN-PM-001 |
| bot_building | BOT | LEARN-BOT-001 |
| system | SYS | LEARN-SYS-001 |
| session_management | SES | LEARN-SES-001 |
| skill_creation | SKL | LEARN-SKL-001 |

IDs are sequential within each category file. Check the last entry before assigning a new ID.

---

## Read Rules — Mandatory

- **Never raw-load a learnings file.** All reads go through Context Mode MCP.
- Context Mode queries the SQLite index and returns only matching entries.
- Raw files are the source of truth for writing — Context Mode is for reading.
- After every write to a learnings file → re-index into Context Mode MCP immediately.

---

## Write Rules — Mandatory

- **Extract minimum 1 learning per interaction — mandatory, no exception.**
- Append only — never delete or edit existing entries.
- Always re-index after appending.
- Assign a unique LEARN-ID before writing.
- Always include all fields in the format — no partial entries.
- Timestamp format: `Full Day Name, DD-Mon-YYYY · HH:MM IST`

## Per-Interaction Extraction Sources

Before closing every interaction, check all five sources in order:

| Priority | Source | Question to ask | Category file |
|---|---|---|---|
| 1 | Mistakes made | What went wrong that I should never repeat? | `mistakes_to_avoid.md` |
| 2 | User corrections | What did the user change, redirect, or clarify? | `mistakes_to_avoid.md` |
| 3 | New patterns | Did I find a better or faster way mid-task? | `efficiency_gains.md` |
| 4 | Edge cases | Did I handle something unexpected? | `resolving_issues.md` |
| 5 | Confirmations | What worked and should always be repeated? | `best_practices.md` |

If none of 1–4 apply, source 5 always applies — every interaction confirms something.
No interaction is too small or too simple to produce a learning.

---

*learnings/README.md — Thursday, 17-Apr-2026 · IST*
