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

Post-output — LEARNING GATE (all 4 are CRITICAL — failure = CRITICAL anomaly):
8.  [ ] LEARNING EXTRACTED: YES — at minimum 1 learning stored this interaction
9.  [ ] Learning saved to correct categorized path: learnings/[domain]/[topic]/[category].md
10. [ ] Learning entry timestamped correctly in IST format
11. [ ] LEARN-ID cited in agent output under "New learning:"
```

### Learning extraction check — primary gate
After every interaction, before closing the monitoring entry, answer:

```
LEARNING EXTRACTED THIS INTERACTION: YES / NO

If NO → this is a CRITICAL violation. Log to anomalies.md immediately.
         Severity: CRITICAL
         Corrective action: extract learning now, before next message.

If YES → confirm:
  Source:    [Mistake / User-correction / New-pattern / Confirmation]
  Domain:    [product_management / bot_building / system]
  Topic:     [prd_writing / session_management / etc.]
  Category:  [best_practices / mistakes_to_avoid / efficiency_gains / etc.]
  LEARN-ID:  [assigned ID]
  Cited in output: YES / NO
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

**LEARNING EXTRACTED:** YES / NO
**LEARN-ID stored:** [LEARN-ID or NONE — CRITICAL if NONE]
**Learning source:** [Mistake / User-correction / New-pattern / Confirmation]
**Learning path:** learnings/[domain]/[topic]/[category].md

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
