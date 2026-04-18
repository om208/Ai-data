# best_practices.md — Product Management / Feature Cards
# Domain: product_management | Topic: feature_cards | Category: best_practices
# Append-only. Never delete entries.
# Version: 1.0 | Created: Thursday, 17-Apr-2026 · IST

---

## LEARN-PM-006
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** feature-card, acceptance-criteria, binary
**Domain:** product_management
**Topic:** feature_cards
**Source:** General

**Context:**
Documenting the acceptance criteria standard from capability 12.

**Learning:**
Feature card acceptance criteria checklists must be binary — each item
is either fully passed or not. No partial credit. If every checkbox
passes, the feature is approved. If any fails, it is not delivered.

**Why It Matters:**
Partial or qualitative acceptance criteria create ambiguity about
whether a feature is done. Binary checklists eliminate debate and
create a clear, unambiguous delivery standard.

**Apply When:**
Every feature card creation. Write acceptance criteria as binary
yes/no statements, not as ranges or approximations.
---

---

## LEARN-PM-007
**Timestamp:** Thursday, 17-Apr-2026 · IST
**Keywords:** feature-card, breaking-cases, pre-dev
**Domain:** product_management
**Topic:** feature_cards
**Source:** General

**Context:**
Documenting the breaking case requirement from capability 13.

**Learning:**
Breaking cases must be documented in the feature card BEFORE
development begins — not discovered after deployment. The standard
breaking case list includes: empty input, malformed input, slow API,
simultaneous triggers, missing permissions, database empty states.

**Why It Matters:**
Breaking cases discovered post-deployment require hotfixes under
pressure. Documenting them pre-dev means they are handled in
the original implementation without emergency cost.

**Apply When:**
Every feature card creation. After writing acceptance criteria,
always add a "Breaking Cases" section before any code is written.
---
