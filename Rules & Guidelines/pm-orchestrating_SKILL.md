---
name: pm-orchestrating
description: Master PM orchestrator that routes every product management task to
             the correct sub-skill. Use when any PM activity begins — idea,
             vision, market research, brainstorm, PRD, roadmap, feature card,
             success criteria, quality assurance, or strategy. This skill always
             loads first and delegates to the right sub-skill.
---

# PM Orchestrating
# Version: 1.0 | Created: Tuesday, 14-Apr-2026 · IST | Updated: —

## When to use this skill
- Any PM task begins — this is the entry point, always
- User shares an idea, problem, or product goal
- Agent needs to decide which PM sub-skill to activate
- A product workflow needs to be sequenced end to end

## Workflow
- [ ] Identify the PM activity from user input
- [ ] Match to the correct sub-skill using the routing table below
- [ ] Load that sub-skill's SKILL.md — read it fully before acting
- [ ] Execute via that sub-skill's workflow
- [ ] After delivery → re-index all outputs into Context Mode MCP
- [ ] Extract learning → store to `learnings/product_management/[topic]/`
- [ ] Log to `agent_log.md` — append only
- [ ] Monitoring-analytics scores this interaction out of 11

## Instructions

### PM sub-skill routing table

| User trigger | Sub-skill to load |
|---|---|
| "I have an idea" / "vision" / "mission" | `product-vision-crafting` |
| "analyze market" / "competitors" / "research" | `market-analyzing` |
| "brainstorm" / "explore" / "what features" | `solution-brainstorming` |
| "PRD" / "requirements" / "spec" | `writing-prds` |
| "roadmap" / "prioritize" / "quarters" | `roadmap-planning` |
| "feature card" / "break down feature" | `creating-feature-cards` |
| "success criteria" / "define done" / "KPIs" | `success-criteria-defining` |
| "QA" / "quality" / "test" / "verify" | `quality-assuring` |
| "brainstorm idea" / "what to build" | `brainstorming-features` |

### Full PM product lifecycle — phase order

```
Phase 1 → product-vision-crafting      (WHY — problem + vision)
Phase 2 → market-analyzing             (WHO — users + competitors)
Phase 3 → solution-brainstorming       (WHAT — ideas + features)
Phase 4 → writing-prds                 (SPEC — full requirements)
Phase 5 → roadmap-planning             (WHEN — sequenced plan)
Phase 6 → creating-feature-cards       (HOW — detailed cards)
Phase 7 → success-criteria-defining    (DONE — measurable goals)
Phase 8 → quality-assuring             (VERIFY — QA checklist)
```

User does not need to follow phases in order. Agent routes to
whichever phase the user is at. Always check which phases are
already done before suggesting next steps.

### Context MCP rule — mandatory on every sub-skill output
After any sub-skill produces output:
```
Output written to file
      ↓
Re-index into Context Mode MCP immediately
      ↓
Verify index updated
      ↓
Proceed to learning extraction
```

### Continuous learning — mandatory after every PM task
```
Task complete
      ↓
Extract 1+ learnings from what was done
      ↓
Store to learnings/product_management/[topic]/[category].md
      ↓
Re-index learning file into Context Mode MCP
      ↓
Reference LEARN-ID in output
```

### Monitoring — mandatory
monitoring-analytics skill scores every PM interaction out of 11.
It runs silently. No action needed — just ensure every sub-skill
cites its skill ID and learning IDs in output so monitor can score.

## Quality Control Measures
- [ ] Correct sub-skill loaded for the user's trigger
- [ ] Sub-skill's full workflow followed — not skipped
- [ ] All outputs re-indexed into Context Mode MCP after delivery
- [ ] At least 1 learning extracted and stored after each task
- [ ] Learning file re-indexed immediately after writing
- [ ] agent_log.md entry written at end of session

## Building User Trust
- Always confirm which phase of the PM lifecycle is being worked on
- Always show which sub-skill is being activated and why
- Never skip phases silently — if a phase is missing, flag it

## Resources
- [PM lifecycle phases](resources/pm-orchestrating_resources_lifecycle.md) ← Full phase detail + handoff rules
- [Routing edge cases](resources/pm-orchestrating_resources_routing-edge-cases.md) ← When trigger is ambiguous
