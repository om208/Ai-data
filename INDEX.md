# EA Agent — Master System Index
# Version: 1.0 | Created: Thursday, 17-Apr-2026 · IST

---

## What This File Is

This is the single entry point for the EA Agent operational system.
Every directory, file, and workflow is mapped here.
When in doubt about where something lives — start here.

---

## System Architecture at a Glance

```
System/
├── INDEX.md                        ← You are here — master navigation
├── CLAUDE.md                       ← Constitution — core identity + hard rules
├── SKILL-DNA-REPORT.md             ← Blueprint for creating any new skill
├── agent_log.md                    ← Append-only task history (every session)
│
├── Rules & Guidelines/             ← Flat skill files (source of truth)
│   ├── [skill]_SKILL.md            ← All 14 skills live here as flat files
│   └── credits_log.csv             ← Token usage tracking
│
├── .agent/                         ← Agent operational layer
│   └── skills/                     ← Organized skill categories (READMEs)
│       ├── system_skills/          ← Session, context, analytics, creation
│       ├── memory_skills/          ← Learning storage and retrieval
│       ├── pm_skills/              ← All product management skills
│       ├── product_owner_skills/   ← (Reserved for future skills)
│       ├── backend_architect_skills/  ← (Reserved for future skills)
│       ├── frontend_architect_skills/ ← (Reserved for future skills)
│       └── bot_building_skills/    ← (Reserved for future skills)
│
├── learnings/                      ← Hierarchical persistent memory
│   ├── README.md                   ← Learning system rules
│   ├── product_management/         ← PM domain learnings
│   ├── bot_building/               ← Bot building domain learnings
│   └── system/                     ← Agent system learnings
│
├── analytics/                      ← Background monitoring layer
│   ├── anomalies.md                ← Flagged violations (append-only)
│   └── compliance_summary.md       ← Rolling 11-point compliance score
│
└── .tmp/                           ← Internal session management
    ├── session_template.md         ← Template for each session file
    └── [session files created at runtime]
```

---

## Quick-Load Reference — What to Read First

| Situation | File to open |
|---|---|
| Starting any new session | `CLAUDE.md` → then `.tmp/session_template.md` |
| Creating a new skill | `SKILL-DNA-REPORT.md` |
| Any PM task | `Rules & Guidelines/pm-orchestrating_SKILL.md` |
| Storing or retrieving a learning | `Rules & Guidelines/managing-learnings_SKILL.md` |
| Context bloat or session reset | `Rules & Guidelines/managing-context-mcp_SKILL.md` |
| Credit limit approaching | `Rules & Guidelines/managing-session-tasks_SKILL.md` |
| Scoring or logging interaction | `Rules & Guidelines/monitoring-analytics_SKILL.md` |

---

## All Skills — Complete Inventory

### System Skills (4)
| Skill | File | Trigger |
|---|---|---|
| managing-session-tasks | `Rules & Guidelines/managing-session-tasks_SKILL.md` | Any new task begins |
| managing-context-mcp | `Rules & Guidelines/managing-context-mcp_SKILL.md` | Context bloat / reset |
| creating-skills | `Rules & Guidelines/creating-skills_SKILL.md` | Building a new skill |
| monitoring-analytics | `Rules & Guidelines/monitoring-analytics_SKILL.md` | Every interaction (silent) |

### Memory Skills (1)
| Skill | File | Trigger |
|---|---|---|
| managing-learnings | `Rules & Guidelines/managing-learnings_SKILL.md` | Storing or retrieving learnings |

### PM Skills (9)
| Skill | File | Trigger |
|---|---|---|
| pm-orchestrating | `Rules & Guidelines/pm-orchestrating_SKILL.md` | Any PM task — always first |
| brainstorming-features | `Rules & Guidelines/brainstorming-features_SKILL.md` | "What to build?" / idea exploration |
| solution-brainstorming | `Rules & Guidelines/solution-brainstorming_SKILL.md` | "Brainstorm" / explore features |
| product-vision-crafting | `Rules & Guidelines/product-vision-crafting_SKILL.md` | Vision / mission / WHY |
| market-analyzing | `Rules & Guidelines/market-analyzing_SKILL.md` | Competitors / market / research |
| writing-prds | `Rules & Guidelines/writing-prds_SKILL.md` | "Write PRD" / requirements |
| roadmap-planning | `Rules & Guidelines/roadmap-planning_SKILL.md` | Roadmap / prioritize / quarters |
| creating-feature-cards | `Rules & Guidelines/creating-feature-cards_SKILL.md` | "Break down feature" / feature card |
| success-criteria-defining | `Rules & Guidelines/success-criteria-defining_SKILL.md` | "Define done" / KPIs |
| quality-assuring | `Rules & Guidelines/quality-assuring_SKILL.md` | QA / test / verify |

---

## The 7-Phase Execution Protocol — Always Active

```
Phase 1 — UNDERSTAND  → Restate the request. Ask WHY. Confirm intent.
Phase 2 — CONSULT     → Load learnings/[domain]/[topic]/ via Context Mode MCP.
Phase 3 — PLAN        → Decompose into sub-tasks with dos/don'ts. Write session file.
Phase 4 — EXECUTE     → Build. Follow the loaded skill exactly. No improvising.
Phase 5 — VERIFY      → Run acceptance checklist. Test edge cases.
Phase 6 — DELIVER     → Full output. Cite skill IDs + learning IDs. Checkpoint.
Phase 7 — LEARN       → Store 1+ learnings. Write agent_log.md entry.
```

No phase can be skipped. No exceptions.

---

## Standard Output Format — Every Response

```
Skills used:       [SKILL IDs]
Learnings applied: [LEARN IDs or "None"]
New learning:      [LEARN-ID — rule in one line]

[Actual output starts here]
```

---

## Learning Domain Map

| Domain | Directory | Topics inside |
|---|---|---|
| product_management | `learnings/product_management/` | prd_writing, brainstorming, feature_cards, roadmap, vision |
| bot_building | `learnings/bot_building/` | oracle_free_tier, architecture, integrations |
| system | `learnings/system/` | session_management, context_mcp, skill_creation |

---

## Hard Rules Snapshot (Full rules in CLAUDE.md)

```
❌ Never skip any of the 7 phases
❌ Never start without decomposing into sub-tasks first
❌ Never load skills not triggered by current task
❌ Never bypass Context Mode MCP — all reads go through it
❌ Never create/update a file without re-indexing into Context Mode immediately
❌ Never build before brainstorming and confirming requirements
❌ Never ask more than 3 questions at a time
❌ Never delete any learning or log entry — append only

✅ Always lazy load — per phase, not upfront
✅ Always create .tmp/ session file at session start
✅ Always checkpoint after every Phase 6 DELIVER
✅ Always cite skill IDs and learning IDs in every output
✅ Always extract minimum 1 learning per session
✅ Always write agent_log.md entry at session end
```

---

*EA Agent Master Index — Thursday, 17-Apr-2026 · IST*
*Built on Oracle Free Tier · Governed by CLAUDE.md · Powered by structured skills*
