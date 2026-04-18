# anomalies.md — EA Agent Violation Log
# Append-only. Never delete entries.
# Version: 1.0 | Created: Thursday, 17-Apr-2026 · IST

---

## What This File Is

This file logs every rule violation, quality failure, or anomaly detected
by the monitoring-analytics skill during any interaction.

It is written to silently — the user never sees this file unless they explicitly
request an analytics report. It is re-indexed into Context Mode MCP after every entry.

---

## Anomaly Entry Format

```md
---
## ANOM-[SESSION-ID]-[3-digit sequence]
**Timestamp:** [Full Day Name, DD-Mon-YYYY · HH:MM IST]
**Session:** [session ID]
**Phase detected:** [Pre-output / During-output / Post-output]
**Checklist item failed:** [Exact item from 11-point checklist]
**Severity:** [CRITICAL / WARNING / MINOR]

**What happened:**
[1–2 sentences describing the violation]

**Impact:**
[What effect this had on the output or user experience]

**Corrective action taken:**
[What was done to correct it mid-session, or "None — flagged for review"]
---
```

---

## Severity Levels

| Level | Definition |
|---|---|
| CRITICAL | A hard rule was broken (e.g. phase skipped, unverified delivery, raw file load) |
| WARNING | A quality standard slipped (e.g. output not cited, learning not stored) |
| MINOR | A style or format inconsistency (e.g. wrong timestamp format, missing skill ID) |

---

## The 11-Point Monitoring Checklist

The monitoring-analytics skill scores every interaction against these 11 points:

**Pre-output (3 points)**
1. Task decomposed into sub-tasks before execution began
2. Correct skill loaded for the trigger
3. Learnings consulted before starting (Phase 2 CONSULT)

**During output (4 points)**
4. All 7 phases executed in order — none skipped
5. Context Mode MCP used for all file reads
6. No more than 3 questions asked at once
7. Output verified before delivery (Phase 5 VERIFY)

**Post-output — LEARNING GATE (4 points — all CRITICAL)**
8.  LEARNING EXTRACTED: YES — minimum 1 learning stored this interaction
9.  Learning saved to correct categorized path: learnings/[domain]/[topic]/[category].md
10. Learning entry timestamped correctly in IST format
11. LEARN-ID cited in agent output under "New learning:"

⚠️ Checks 8–11 are CRITICAL. Failure on any = CRITICAL anomaly logged immediately.
   Goal: agent improves on every conversation, every day — no interaction is wasted.

---

## Anomaly Log — Entries Below

*(No anomalies recorded yet — system initialized Thursday, 17-Apr-2026)*

---

*anomalies.md — Thursday, 17-Apr-2026 · IST*
