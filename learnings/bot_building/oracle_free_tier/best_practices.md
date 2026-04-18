# best_practices.md — Bot Building / Oracle Free Tier
# Domain: bot_building | Topic: oracle_free_tier | Category: best_practices
# Append-only. Never delete entries.
# Version: 1.0 | Created: Thursday, 17-Apr-2026 · IST

---

## LEARN-BOT-001
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** oracle, free-tier, memory-constraint
**Domain:** bot_building
**Topic:** oracle_free_tier
**Source:** General

**Context:**
Documenting the core Oracle Free Tier constraint from capability 20.

**Learning:**
Oracle Free Tier has 1 GB RAM and limited CPU. Every architectural
decision must be evaluated against this constraint. Unoptimized code
is a hard rule violation — not just a quality issue.

**Why It Matters:**
RAM spikes on Free Tier cause OOM kills and service interruptions.
CPU spikes cause throttling. Either is a production incident that
costs user trust and project viability.

**Apply When:**
Every time code is written, an architecture is designed, or a library
is selected. Ask: "Does this fit within 1 GB RAM and limited CPU?"
Prefer generators, lazy loading, and async non-blocking patterns.
---

---

## LEARN-BOT-002
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** sqlite, indexing, context-mode
**Domain:** bot_building
**Topic:** oracle_free_tier
**Source:** General

**Context:**
Documenting the Context Mode MCP indexing strategy from capability 7.

**Learning:**
Use SQLite local indexing (Context Mode MCP) for all file reads and
tool outputs. Never dump raw file contents into the context window.
SQLite indexing achieves up to 98% token reduction on large reads.

**Why It Matters:**
Raw file dumps into context consume tokens rapidly and hit Claude's
context limits faster, forcing expensive resets. SQLite indexing
keeps the context window lean on Free Tier resource budgets.

**Apply When:**
Every file read and tool output. Route all reads through Context Mode
MCP. Only write to raw files — Context Mode handles all reads.
---

---

## LEARN-BOT-003
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** lazy-loading, skills, context-lean
**Domain:** bot_building
**Topic:** oracle_free_tier
**Source:** General

**Context:**
Documenting the lazy loading rule from capabilities 3 and 6.

**Learning:**
Load only the skill triggered by the current task — never preload
multiple skills. Load learning files only for the specific domain
and topic of the current task — never all at once.

**Why It Matters:**
Preloading multiple skills or learning files multiplies token usage
before a single line of work is done. On Free Tier limits, this
pushes sessions toward the credit window before the task completes.

**Apply When:**
Every session start. Resist the instinct to "load everything upfront."
Let the task drive what gets loaded, phase by phase.
---
