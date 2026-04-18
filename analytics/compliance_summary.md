# compliance_summary.md — EA Agent Rolling Compliance Score
# Updated after every session by monitoring-analytics skill.
# Version: 1.0 | Created: Thursday, 17-Apr-2026 · IST

---

## What This File Is

This is the rolling compliance dashboard for the EA Agent.
The monitoring-analytics skill updates this after every session.
It shows the agent's overall adherence to its 11-point checklist over time.

The user can request a compliance report at any time.
The agent reads this file at session start to check if there are unresolved violations.

---

## Current Compliance Status

| Metric | Value |
|---|---|
| Total sessions logged | 1 |
| Sessions with CRITICAL violations | 0 |
| Sessions with WARNING violations | 0 |
| Sessions with MINOR violations | 0 |
| Clean sessions (all 11 points passed) | 1 |
| **Rolling compliance score** | **100% (11/11)** |
| Last updated | Thursday, 17-Apr-2026 · IST |

---

## Session-by-Session Score Table

| Session ID | Date | Score | Violations | Status |
|---|---|---|---|---|
| LOG-001 | 17-Apr-2026 | 11/11 | None | ✅ Clean |

---

## Score Update Format

After every session, append a row to the table above and update the summary metrics.
Do not delete any rows — keep the full history.

---

## Violation Trend

*(Not enough data yet — tracking starts from next session)*

Trend analysis available after 5+ sessions.
Tracks: most common violated checklist item, most common severity, improvement over time.

---

## How Compliance Score Is Calculated

```
Score = (Points passed / 11) × 100

Points passed = number of checklist items met during the session
Maximum = 11 points per session
```

A session is "Clean" if all 11 points pass.
A session is "WARNING" if 1–2 MINOR or WARNING violations occur.
A session is "CRITICAL" if any CRITICAL violation occurs.

---

*compliance_summary.md — Thursday, 17-Apr-2026 · IST*
