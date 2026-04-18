# best_practices.md — System / Session Management
# Domain: system | Topic: session_management | Category: best_practices
# Append-only. Never delete entries.
# Version: 1.0 | Created: Thursday, 17-Apr-2026 · IST

---

## LEARN-SES-001
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** session-file, tmp, startup
**Domain:** system
**Topic:** session_management
**Source:** General

**Context:**
Documenting the session file requirement from capability 23.

**Learning:**
Always create a `.tmp/session_[YYYY-MM-DD_HH-MM]_IST.md` file at the
start of every session using the session template. This is the first
action before any task work begins — non-negotiable.

**Why It Matters:**
Without a session file, sub-task tracking is lost on context compaction
or credit reset. The session file is the recovery point — it is what
allows the agent to resume from exactly the right PENDING sub-task
after a reset, with zero context lost and zero work repeated.

**Apply When:**
Every session start, without exception. Before reading any task or
loading any skill — write the session file to `.tmp/` first.
---

---

## LEARN-SES-002
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** credit-warning, snapshot, pause
**Domain:** system
**Topic:** session_management
**Source:** General

**Context:**
Documenting the credit limit handling protocol from capability 23.

**Learning:**
When token usage approaches the credit limit threshold (less than
~20% of the window remaining), the agent must: (1) snapshot the full
session state, (2) warn the user clearly, (3) show the done/pending
sub-task list, (4) pause cleanly. Never let credits exhaust silently.

**Why It Matters:**
Silent credit exhaustion results in an abrupt session end with no
record of where work stopped. The user loses context and the agent
cannot resume without guessing. Proactive warning and snapshotting
eliminate this problem entirely.

**Apply When:**
Monitor `credits_log.csv` at each major sub-task checkpoint. When
tokens remaining crosses the 20% threshold — stop, snapshot, warn.
---

---

## LEARN-SES-003
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** resume, pending, session-file
**Domain:** system
**Topic:** session_management
**Source:** General

**Context:**
Documenting the session resume protocol from capability 23.

**Learning:**
When a user returns after a credit reset, the first action is to
read the `.tmp/session_[last]_IST.md` file. Show the user exactly
what is DONE and what is PENDING. Then resume from the first PENDING
sub-task — not from the beginning of the task.

**Why It Matters:**
Starting from scratch after a reset wastes the user's time and burns
credits re-doing completed work. Reading the session file provides
exact continuity — the user experiences no loss of progress.

**Apply When:**
Every session that is a continuation of a previous session. Check if
a session file exists in `.tmp/` before starting new work.
---

---

## LEARN-SYS-001
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** index-first, directory, navigation
**Domain:** system
**Topic:** session_management
**Source:** General

**Context:**
Discovered during the EA Agent system build session (LOG-001).

**Learning:**
When building any new agent system or project directory, always create
INDEX.md first. The index anchors the directory plan and prevents
file creation from becoming inconsistent or navigationally broken.

**Why It Matters:**
Creating files without an index leads to orphaned files that future
sessions cannot locate efficiently via Context Mode MCP queries.
The index is the contract that all files are written against.

**Apply When:**
Any new project or agent system initialization. INDEX.md is file #1,
before any skill, learning, or operational file is created.
---
