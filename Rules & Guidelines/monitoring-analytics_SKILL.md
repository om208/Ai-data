---
name: monitoring-analytics
description: Silently monitors, scores, and logs every agent interaction against
             an 11-point quality checklist. Use automatically on every message
             received. Never surfaces output to user. Writes to analytics/ only.
---

# Monitoring Analytics
# Version: 1.0 | Created: Monday, 13-Apr-2026 · IST | Updated: —

## When to use this skill
- Triggered automatically on every user message — no exception
- When scoring a completed interaction out of 11
- When logging a violation to anomalies.md
- When updating the rolling compliance_summary.md

## Workflow
- [ ] On message received → increment message counter, open new INTERACTION-[ID]
- [ ] During pre-output → monitor skills loaded, learnings consulted (checks 1–4)
- [ ] During output → verify workflow followed, IDs cited (checks 5–7)
- [ ] Post-output → verify learning stored, timestamped, categorised (checks 8–11)
- [ ] Calculate score: [checks passed] / 11
- [ ] If score < 11 → log violation to `analytics/anomalies.md`
- [ ] Append entry to `analytics/interaction_logs/YYYY-MM/DD-Mon-YYYY.md`
- [ ] Update `analytics/compliance_summary.md`

## Instructions

### Analytics directory
```
analytics/
├── interaction_logs/
│   └── YYYY-MM/
│       └── DD-Mon-YYYY.md
├── checklist_reports/
│   └── YYYY-MM/
│       └── DD-Mon-YYYY_report.md
├── compliance_summary.md
└── anomalies.md
```

### The 11-point checklist
```
Pre-output:
1. [ ] Relevant skills identified and loaded
2. [ ] Only needed skills loaded — no over-fetching
3. [ ] Relevant learning files consulted
4. [ ] Only needed learnings loaded — no over-fetching

During output:
5. [ ] Output followed loaded skill workflow
6. [ ] Learnings referenced in output shown to user
7. [ ] Applied skill IDs mentioned in output

Post-output:
8.  [ ] New learnings extracted from this interaction
9.  [ ] Learnings saved to correct file and path
10. [ ] Learning entry timestamped correctly in IST
11. [ ] Learning correctly categorised by domain/topic
```

### Interaction log entry format
```md
## INTERACTION-[ID]
**Timestamp:** [Full Day Name, DD-Mon-YYYY · HH:MM IST]
**Message #:** [running count]
**Input summary:** [1-line summary]

**Score:** [X/11]
**Skills loaded:** [IDs or None]
**Learnings consulted:** [IDs or None]
**New learnings:** [IDs or None]
**Violations:** [describe each or None]
```

### Anomaly entry format
```md
## ANOMALY-[ID]
**Interaction:** INTERACTION-[ID]
**Timestamp:** [Full Day Name, DD-Mon-YYYY · HH:MM IST]
**Violation:** [what was skipped or done wrong]
**Checkpoint failed:** [checkpoint number]
**Severity:** Low / Medium / High
```

→ See `resources/monitoring-analytics_resources_severity-guide.md` for severity definitions.

## Quality Control Measures
- [ ] Every message receives an interaction log entry — no exceptions
- [ ] Score is always out of 11 — never rounded or estimated
- [ ] Violations always logged to anomalies.md — no silent passes
- [ ] compliance_summary.md updated after every interaction
- [ ] Monitor output never shown to user — silent always

## Building User Trust
- Silent monitoring ensures agent self-accountability without interrupting flow
- Compliance scores are available on request via compliance_summary.md
- Violations are traceable — every anomaly links back to its interaction

## Resources
- [Severity guide](resources/monitoring-analytics_resources_severity-guide.md) ← When classifying anomaly severity
- [Compliance report template](resources/monitoring-analytics_resources_report-template.md) ← When generating a compliance report
