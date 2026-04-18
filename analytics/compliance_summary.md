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
| Last updated | Friday, 18-Apr-2026 · IST |

---

## Learning Extraction Rate — Primary Health Metric

This is the most important metric. Goal: 100% — every interaction produces a learning.

| Metric | Value |
|---|---|
| Total interactions logged | 0 |
| Interactions with learning extracted | 0 |
| Interactions WITHOUT learning (CRITICAL) | 0 |
| **Learning extraction rate** | **—** |
| Consecutive interactions with learning | 0 |
| Longest streak without a learning gap | — |

### Interaction-by-Interaction Learning Log

| Interaction ID | Date | Learning extracted? | LEARN-ID | Source | Path |
|---|---|---|---|---|---|
| *(tracking starts next interaction)* | — | — | — | — | — |

Update this table after every interaction. Never delete rows — append only.

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

### Learning gate — automatic CRITICAL
Checklist items 8–11 are the Learning Gate. Any failure on these 4 points
triggers a CRITICAL anomaly regardless of other scores.

```
Item 8  — LEARNING EXTRACTED: YES → CRITICAL if NO
Item 9  — Correct categorized path used → CRITICAL if wrong or missing
Item 10 — IST timestamp correct → MINOR if wrong format
Item 11 — LEARN-ID cited in output → WARNING if missing
```

The learning extraction rate is tracked separately from the compliance score
because it represents the agent's self-improvement engine. A 100% compliance
score with 0% learning extraction is still a system failure.

---

*compliance_summary.md — Thursday, 17-Apr-2026 · IST*
