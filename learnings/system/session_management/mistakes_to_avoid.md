# mistakes_to_avoid.md — System / Session Management
# Domain: system | Topic: session_management | Category: mistakes_to_avoid
# Append-only. Never delete entries.
# Version: 1.0 | Created: Thursday, 17-Apr-2026 · IST

---

## LEARN-SES-004
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** phase-skipping, protocol, non-negotiable
**Domain:** system
**Topic:** session_management
**Source:** General

**Context:**
Documenting the most critical hard rule from the CLAUDE.md constitution.

**Learning:**
Never skip any of the 7 phases, even for simple or "obvious" tasks.
The most dangerous skip is CONSULT (Phase 2) — skipping it means past
learnings are not applied, repeating mistakes from previous sessions.

**Why It Matters:**
Each phase exists because its absence caused a quality failure at
some point in the system's design. A skipped phase is not time saved
— it is a deferred failure that shows up at delivery or after.

**Apply When:**
Every single task. Before executing any work, mentally check: "Have I
completed UNDERSTAND and CONSULT?" If no — do them now.
---

---

## LEARN-SES-005
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** preloading, skills, token-waste
**Domain:** system
**Topic:** session_management
**Source:** General

**Context:**
Documenting the most common token waste pattern from capability 3.

**Learning:**
Never preload multiple skills at session start "just in case." Load
only the skill triggered by the current task phase. Load the next
skill only when that phase begins.

**Why It Matters:**
Preloading 3–4 skills at session start consumes hundreds of tokens
before any work is done. On Oracle Free Tier's credit window, this
shrinks the available working budget for actual task execution.

**Apply When:**
Every session start. Resist the temptation to load all PM skills
when a PM task begins. Load pm-orchestrating first. Let it identify
the correct sub-skill. Then load only that one.
---

---

## LEARN-SES-006
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** raw-file, context-mode, bypass
**Domain:** system
**Topic:** session_management
**Source:** General

**Context:**
Documenting the most critical technical rule from CLAUDE.md.

**Learning:**
Never read any file directly when Context Mode MCP is active. All
reads — skills, learnings, tool outputs — must route through Context
Mode MCP. Direct reads dump raw content into context and consume
massive tokens unnecessarily.

**Why It Matters:**
A single raw read of a large skill file can consume 2,000–5,000 tokens.
Context Mode MCP returns a summary in 50–100 tokens. On Free Tier,
one bypassed read can waste an hour's worth of token budget.

**Apply When:**
Every file read, every tool output. If you catch yourself using
a direct file read — stop. Route it through Context Mode MCP instead.
---
