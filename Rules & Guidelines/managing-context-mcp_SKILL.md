---
name: managing-context-mcp
description: Manages the Context Mode MCP token virtualization layer for the EA
             Agent. Sandboxes all tool outputs, skill reads, and learning lookups
             into a local SQLite index so only summaries enter Claude's context
             window. Use when any file is created or updated (mandatory re-index),
             when context bloat is detected, when a session resets or compacts,
             or when creating a checkpoint after delivery.
---

# Managing Context MCP
# Version: 1.0 | Created: Monday, 13-Apr-2026 · IST | Updated: —

## When to use this skill
- **Any file is created or updated** — mandatory re-index immediately after
- Session context is compacting or has just reset
- Agent needs to restore state after a context window compaction
- After Phase 6 DELIVER — create a checkpoint of completed work
- Context bloat detected — tool outputs or file reads are too large
- Initial setup — installing and configuring Context Mode MCP

## Workflow

### On every file create or update (MANDATORY INDEX LOOP)
- [ ] File written to disk — source of truth saved
- [ ] Immediately re-index into Context Mode MCP SQLite
- [ ] Verify index updated — confirm before proceeding
- [ ] Only after index confirmed → mark task step complete

### On session start
- [ ] Confirm Context Mode MCP is installed and running (`ctx doctor`)
- [ ] Verify all reads are routing through it

### On DELIVER completion
- [ ] Trigger checkpoint save — captures all decisions + files this session
- [ ] Confirm checkpoint ID — log it in agent_log.md

### On session reset / compaction
- [ ] Context Mode auto-restores last checkpoint
- [ ] Verify restored state before reading any new message

### On context bloat warning
- [ ] Identify which file or tool is over-fetching
- [ ] Fix its routing to go through Context Mode sandbox

## Instructions

### Install once
```bash
claude mcp add context-mode -- npx -y context-mode
```

Verify it is running:
```bash
ctx doctor
```

### MANDATORY INDEX LOOP — every create or update

```
Write file to disk
      ↓
Re-index into Context Mode MCP immediately
      ↓
Verify index updated
      ↓
Proceed — never skip this loop
```

Applies to every one of these without exception:
```
New skill file saved          → re-index now
Skill file updated            → re-index now
New learning entry appended   → re-index now
Feature card created          → re-index now
Feature card updated          → re-index now
PRD created or updated        → re-index now
agent_log.md entry added      → re-index now
analytics log entry added     → re-index now
Any project file changed      → re-index now
```

Rule: Write → Index → Verify → Done.
A file that is not indexed does not exist for the agent's reads.

### How it works in EA Agent

```
Agent wants to read a learning file
         ↓
Context Mode intercepts the read
         ↓
Queries SQLite index — returns only matching entries (not full file)
         ↓
Agent receives 50-200 token summary instead of 2000+ token file dump

Agent wants to load a skill resource file
         ↓
Context Mode intercepts
         ↓
Returns only the section relevant to current phase
         ↓
Full file stays in SQLite — never in context window
```

### Token savings map

| Without Context Mode | With Context Mode | Saving |
|---|---|---|
| Full learning file loaded | Matching entries only | ~85–95% |
| Full skill resource loaded | Phase-relevant slice only | ~70–90% |
| Raw tool output dumped | Summary injected | ~98% |
| Session reset loses all state | Checkpoint restored (<2KB) | 100% continuity |

### Checkpoint rules
- Fire a checkpoint after every Phase 6 DELIVER — no exceptions
- Checkpoint captures: task completed, decisions made, errors tried, current files
- Checkpoint size target: under 2KB — compact, not verbose
- On session reset: checkpoint is auto-injected before agent reads any message

Manual checkpoint trigger:
```
ctx stats          → see current savings and session report
ctx doctor         → diagnose if something is broken
```

### What gets indexed into SQLite
- All learning file entries (domain/topic/category)
- All skill resource file content (by section)
- All tool output results (summarised)
- All agent log entries (task + outcome)
- All feature card content (by section)

### What stays raw (never indexed)
- `CLAUDE.md` — always read directly, it is the root orchestrator
- `SKILL-DNA-REPORT.md` — always read directly, used before skill creation
- Active SKILL.md core files — read directly when skill is triggered
- User messages — never indexed, always raw

### Routing rule
```
If file is in learnings/      → route through Context Mode
If file is in resources/      → route through Context Mode
If file is in feature_cards/  → route through Context Mode
If file is in analytics/      → route through Context Mode
If file is in agent_log.md    → route through Context Mode
If file is CLAUDE.md          → read directly
If file is *_SKILL.md core    → read directly (it is already lean)
```

→ See `resources/managing-context-mcp_resources_sqlite-schema.md` for the full SQLite index schema used by Context Mode.

## Quality Control Measures
- [ ] Every file create or update was followed by immediate re-index
- [ ] `ctx doctor` passes cleanly — no hook errors
- [ ] Context Mode appears in `/context` output as active MCP tool
- [ ] MCP tool tokens in `/context` are under 6k (not 60k+)
- [ ] Checkpoint created after last DELIVER phase
- [ ] No raw file dumps in context — all large reads go through sandbox
- [ ] Session restore works after compaction — test with `ctx stats`
- [ ] No file is readable by agent unless it has been indexed

## Building User Trust
- Always run `ctx doctor` at session start — surface any routing issues early
- Always show checkpoint ID after DELIVER so user knows state is saved
- Always restore from checkpoint on session reset — never start blind

## Resources
- [SQLite schema](resources/managing-context-mcp_resources_sqlite-schema.md) ← When debugging what is indexed
- [Checkpoint format](resources/managing-context-mcp_resources_checkpoint-format.md) ← When reviewing or restoring a checkpoint
