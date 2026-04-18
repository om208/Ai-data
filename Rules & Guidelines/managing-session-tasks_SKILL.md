---
name: managing-session-tasks
description: Decomposes every task into structured tasks and sub-tasks with clear
             dos and don'ts. Creates and maintains a .tmp/ session directory for
             internal execution tracking. Tracks Claude Pro token usage and reset
             window so work can resume perfectly after a credit limit pause. Use
             at the start of every task, when a session limit warning appears, or
             when resuming work after a credit reset.
---

# Managing Session Tasks
# Version: 1.0 | Created: Thursday, 16-Apr-2026 · IST | Updated: —

## When to use this skill
- Any new task begins — decompose before executing
- Session starts — create .tmp/ session directory if not present
- Credit/usage limit warning appears — snapshot state immediately
- User resumes after a 5-hour reset — restore from session snapshot
- User asks "what's done, what's pending?"

## Workflow

### On every new task
- [ ] Decompose task into tasks and sub-tasks — see format below
- [ ] Write dos and don'ts for the task explicitly
- [ ] Check if `.tmp/` directory exists — create if not
- [ ] Create session file: `.tmp/session_[YYYY-MM-DD_HH-MM]_IST.md`
- [ ] Write execution plan to session file
- [ ] Track every sub-task status: DONE / IN-PROGRESS / PENDING
- [ ] Log token snapshot to `.tmp/credits_log.csv` at start
- [ ] Re-index session file into Context Mode MCP immediately

### On every sub-task completion
- [ ] Update status in session file: mark DONE with timestamp
- [ ] Update credits_log.csv with current token snapshot
- [ ] Re-index session file into Context Mode MCP

### On credit limit warning / session pause
- [ ] Immediately write final state snapshot to session file
- [ ] Mark all remaining sub-tasks as PENDING with clear next-step note
- [ ] Warn user: "Credits exhausted. Work paused. Resumes in ~5 hours."
- [ ] Show user the pending task list from session file
- [ ] Update credits_log.csv with final row for this window
- [ ] Re-index all files into Context Mode MCP

### On resume after reset
- [ ] Read last session file from `.tmp/` via Context Mode MCP
- [ ] Show user: "Here is what was done. Here is what is pending."
- [ ] Continue from first PENDING sub-task — no context lost

## Instructions

### Task decomposition format

```md
## Task: [Task name]
**Goal:** [One line — what success looks like]
**Triggered by skill:** [SKILL ID]

### Sub-tasks
| # | Sub-task | Status | Completed at |
|---|----------|--------|-------------|
| 1 | [action] | PENDING | — |
| 2 | [action] | PENDING | — |
| 3 | [action] | DONE | Thu, 16-Apr-2026 · 14:30 IST |

### Dos
- [What must be done — explicit]
- [What order to follow]

### Don'ts
- [What must never happen in this task]
- [What to skip or avoid]

### Blockers
- [Anything that would stop this task — noted upfront]
```

### .tmp/ directory structure

```
.tmp/
├── session_[YYYY-MM-DD_HH-MM]_IST.md   ← one per session
└── credits_log.csv                      ← rolling credits tracker
```

Create `.tmp/` at project root if it does not exist.
Name session file with exact start timestamp in IST.
This directory is for agent internal use only — never deliver to user.

### Session file format

```md
# Session: [YYYY-MM-DD_HH-MM] IST
# Plan: [Claude Pro / Max 5x / Max 20x]
# Reset window: 5 hours from first message
# Status: ACTIVE / PAUSED / COMPLETED

## Execution plan
[Full task breakdown — all tasks + sub-tasks]

## Status tracker
| Task | Sub-task | Status | Notes |
|------|----------|--------|-------|
| ... | ... | DONE | ... |
| ... | ... | IN-PROGRESS | ... |
| ... | ... | PENDING | Start here on resume |

## Context snapshot (written on pause)
- Last action completed: [what]
- Next action on resume: [exactly what to do first]
- Files modified this session: [list]
- Learnings extracted: [LEARN-IDs]
- Decisions made: [key choices]
```

### credits_log.csv format

```csv
serial,timestamp_IST,window_start_IST,tokens_used,tokens_remaining_est,reset_at_IST,plan,notes
1,Thu 16-Apr-2026 14:00,Thu 16-Apr-2026 14:00,0,~45000,Thu 16-Apr-2026 19:00,Pro,Session start
2,Thu 16-Apr-2026 15:30,Thu 16-Apr-2026 14:00,12000,~33000,Thu 16-Apr-2026 19:00,Pro,After PRD draft
3,Thu 16-Apr-2026 18:45,Thu 16-Apr-2026 14:00,41000,~4000,Thu 16-Apr-2026 19:00,Pro,Nearing limit
```

Fields:
- `serial` — auto-increment, row number
- `timestamp_IST` — when this row was written
- `window_start_IST` — when current 5-hour window started
- `tokens_used` — cumulative estimate for this window
- `tokens_remaining_est` — estimated remaining (Pro ~45k/window)
- `reset_at_IST` — window_start + 5 hours
- `plan` — Pro / Max5x / Max20x
- `notes` — what triggered this log entry

### Claude Pro credit facts
→ See `resources/managing-session-tasks_resources_credit-limits.md`
for full plan limits and reset rules.

Summary:
- Reset window: **5 hours** from first message of session
- Pro estimate: ~45,000 tokens per 5-hour window
- Weekly limits also apply for heavy usage
- Reset timing is NOT affected by purchasing extra usage
- Track `window_start` — add 5h to know exact reset time

### Credit warning message to user

When approaching limit, always surface this message:

```
⚠️ Credit limit approaching.

Tokens used this window:  ~[X]
Estimated remaining:      ~[Y]
Window resets at:         [time] IST (in ~[Z] hours)

Work paused at:
  ✅ DONE:    [list completed sub-tasks]
  ⏸ PENDING: [list remaining sub-tasks]

Your work is saved in .tmp/session_[timestamp].md
When you message me after [reset time], I will resume
exactly from: "[next sub-task description]"
```

## Quality Control Measures
- [ ] Every task has a decomposition before execution starts
- [ ] Every sub-task has explicit dos and don'ts written
- [ ] .tmp/ session file created at session start
- [ ] credits_log.csv updated at session start and after each major step
- [ ] On pause: context snapshot written before stopping
- [ ] On resume: session file read first via Context Mode MCP
- [ ] User always informed of pending work before session ends

## Building User Trust
- Always show the task breakdown before starting — user sees the full plan
- Always warn before credits run out — never surprise the user
- Always resume from exactly where work stopped — zero context loss

## Resources
- [Credit limits by plan](resources/managing-session-tasks_resources_credit-limits.md) ← When tracking or estimating tokens
- [Session resume guide](resources/managing-session-tasks_resources_resume-guide.md) ← When restoring after a reset
