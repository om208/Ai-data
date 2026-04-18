# System Skills
# EA Agent — Operational layer for session, context, analytics, and skill creation
# Version: 1.0 | Created: Friday, 18-Apr-2026 · IST

## Skills in this category

| Skill | File (source of truth) | Trigger |
|---|---|---|
| managing-session-tasks | `Rules & Guidelines/managing-session-tasks_SKILL.md` | Any new task begins — always first |
| managing-context-mcp | `Rules & Guidelines/managing-context-mcp_SKILL.md` | Context bloat / session reset / checkpoint |
| creating-skills | `Rules & Guidelines/creating-skills_SKILL.md` | Building or updating any skill |
| monitoring-analytics | `Rules & Guidelines/monitoring-analytics_SKILL.md` | Every interaction — silent background monitor |

## Notes
- Source of truth lives in `Rules & Guidelines/` (flat files)
- This README is the organized index for agent navigation
- Load skills lazily — only the skill triggered by the current task
