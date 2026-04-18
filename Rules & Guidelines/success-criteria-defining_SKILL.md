---
name: success-criteria-defining
description: Defines measurable success criteria and KPIs for a product or
             feature. Use when user asks how to measure success, wants to define
             done, needs KPIs or OKRs, asks what a good outcome looks like, or
             when a feature card needs its success criteria completed.
---

# Success Criteria Defining
# Version: 1.0 | Created: Tuesday, 14-Apr-2026 · IST | Updated: —

## When to use this skill
- Feature card needs success criteria completing
- User asks "how do we know this worked" or "what does success look like"
- OKRs or KPIs need to be defined for a product or sprint
- Post-launch — measuring whether a feature achieved its goal

## Workflow
- [ ] Confirm the north star metric exists in the product vision
- [ ] Identify which metric this feature or product directly influences
- [ ] Define primary success metric (must be measurable, time-bound)
- [ ] Define 2–3 supporting metrics
- [ ] Define failure threshold — below this = the feature failed
- [ ] Define leading indicators — early signals before the main metric moves
- [ ] Save criteria in the relevant feature card or `success/success-criteria.md`
- [ ] Re-index into Context Mode MCP immediately after save
- [ ] Verify index updated
- [ ] Extract learning → `learnings/product_management/success_criteria/best_practices.md`
- [ ] Re-index learning file

## Instructions

### Success criteria structure
```md
## Success criteria — [Feature or Product Name]
Created: [Day, DD-Mon-YYYY · HH:MM IST]

### Primary metric
- Metric: [exact measurement]
- Target: [specific number or %]
- Timeframe: [by when]
- Baseline: [current state before this feature]

### Supporting metrics
| Metric | Target | Timeframe |
|--------|--------|-----------|
| ...    | ...    | ...       |

### Failure threshold
If [primary metric] is below [X] after [Y days] → feature is failing.
Next action: [rollback / iterate / investigate]

### Leading indicators (early signals)
- [Signal 1 — visible within first 48 hours]
- [Signal 2]
```

### Metric quality rules — SMART check
Every metric must pass all 5:
```
S — Specific    : Not "more users" → "DAU increases by 20%"
M — Measurable  : Can be tracked with existing analytics
A — Achievable  : Realistic given current scale and resources
R — Relevant    : Directly tied to the north star metric
T — Time-bound  : Has a clear deadline
```

### Common PM metric categories
- Acquisition: signups, installs, traffic
- Activation: first meaningful action completed
- Retention: D1/D7/D30 retention rates
- Revenue: conversion rate, ARPU, LTV
- Referral: NPS, share rate, organic growth

→ See `resources/success-criteria-defining_resources_metric-library.md` for a full metric reference by product type.

## Quality Control Measures
- [ ] Primary metric is SMART — passes all 5 checks
- [ ] Failure threshold is explicit — not left open
- [ ] Leading indicators are visible within 48 hours of launch
- [ ] Criteria confirmed by user before saving
- [ ] File saved and re-indexed into Context Mode MCP
- [ ] Learning extracted and stored

## Building User Trust
- Always tie success criteria back to the north star metric
- Always define failure — not just success — so decisions are clear
- Never use vanity metrics (page views, likes) as primary metrics

## Resources
- [Metric library by product type](resources/success-criteria-defining_resources_metric-library.md) ← When choosing metrics
- [OKR templates](resources/success-criteria-defining_resources_okr-templates.md) ← When defining quarterly OKRs
