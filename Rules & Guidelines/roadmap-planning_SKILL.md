---
name: roadmap-planning
description: Creates a prioritised product roadmap sequencing features across
             milestones or sprints. Use when user asks to plan the roadmap,
             prioritise features, sequence delivery, define phases, or decide
             what gets built first vs later.
---

# Roadmap Planning
# Version: 1.0 | Created: Tuesday, 14-Apr-2026 · IST | Updated: —

## When to use this skill
- PRD is confirmed and features need to be sequenced
- User asks "what do we build first" or "how do we phase this"
- User wants to prioritise a backlog of features
- User needs a milestone or sprint plan

## Workflow
- [ ] Confirm PRD is finalised — roadmap is always downstream of PRD
- [ ] Ask: what is the target delivery horizon? (MVP, quarter, 6 months)
- [ ] Score all features using ICE framework (Impact · Confidence · Ease)
- [ ] Group into milestones: MVP → V1 → V2 → Backlog
- [ ] Confirm sequencing with user — adjust if needed
- [ ] Save as `roadmap/roadmap-v1.md`
- [ ] Re-index into Context Mode MCP immediately after save
- [ ] Verify index updated
- [ ] Extract learning → `learnings/product_management/roadmap_planning/best_practices.md`
- [ ] Re-index learning file
- [ ] Hand off to `creating-feature-cards` for MVP features

## Instructions

### ICE scoring — per feature
```
Impact      (1–10): How much does this move the north star metric?
Confidence  (1–10): How sure are we this will work?
Ease        (1–10): How fast/cheap to build? (10 = easiest)
ICE Score   = (Impact + Confidence + Ease) / 3
```
Sort features by ICE score descending → highest ICE goes first.

### Roadmap structure
```md
# Product Roadmap — [Product Name]
# Version: 1.0 | Created: [Day, DD-Mon-YYYY · HH:MM IST]

## MVP — [Target date or sprint]
Goal: [What this milestone proves]
| Feature | ICE score | Owner | Status |
|---------|-----------|-------|--------|

## V1 — [Target date or sprint]
Goal: [What this milestone delivers]
| Feature | ICE score | Owner | Status |

## V2 — [Target date or sprint]
...

## Backlog — No date yet
| Feature | ICE score | Reason deferred |
```

### Oracle Free Tier constraint rule
When sequencing features, always flag compute-heavy features:
- If a feature requires heavy processing → push to V2 or later
- MVP must run comfortably within 1 GB RAM
- Never put two compute-intensive features in the same milestone

### Prioritisation rules
- ICE score drives sequencing — not personal preference
- MVP must contain only features needed to validate the north star metric
- If user pushes back on scoring, re-score together — never override silently
- Backlog is not "never" — it's "not yet"

→ See `resources/roadmap-planning_resources_ice-scoring-guide.md` for full ICE scoring examples and calibration.

## Quality Control Measures
- [ ] Every feature has an ICE score — no unscored features in roadmap
- [ ] MVP is lean — only what validates the north star metric
- [ ] Compute-heavy features flagged and staged appropriately
- [ ] Roadmap confirmed by user before saving
- [ ] File saved and re-indexed into Context Mode MCP
- [ ] Learning extracted and stored

## Building User Trust
- Always show ICE scores transparently — user can challenge any score
- Always explain why a feature was deferred — never silently drop it
- Always confirm the MVP scope before moving to feature cards

## Resources
- [ICE scoring guide](resources/roadmap-planning_resources_ice-scoring-guide.md) ← During feature scoring
- [Milestone templates](resources/roadmap-planning_resources_milestone-templates.md) ← During roadmap structure phase
