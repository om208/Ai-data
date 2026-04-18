---
name: quality-assuring
description: Runs structured QA across feature cards, PRDs, and delivered
             outputs. Verifies acceptance criteria, executes test cases, checks
             breaking cases, and signs off on delivery. Use when a feature needs
             QA, when verifying a build is complete, when running browser checks,
             or when the user asks to test or verify anything.
---

# Quality Assuring
# Version: 1.0 | Created: Tuesday, 14-Apr-2026 · IST | Updated: —

## When to use this skill
- A feature card's acceptance criteria need to be run
- User says "test this", "QA this", or "verify this works"
- A build is complete and needs sign-off before delivery
- Browser-based or web features need UI verification
- Breaking cases need to be identified and documented

## Workflow
- [ ] Load the feature card for the feature being tested
- [ ] Run acceptance criteria checklist — tick each item
- [ ] Execute all test cases from the TC table
- [ ] Run breaking cases — attempt to break the feature deliberately
- [ ] Run browser verification checklist (if web-based)
- [ ] Record pass/fail for every item
- [ ] If any item fails → log it + block delivery until fixed
- [ ] If all items pass → sign off and mark feature as verified
- [ ] Update feature card with QA results and date
- [ ] Re-index updated feature card into Context Mode MCP immediately
- [ ] Verify index updated
- [ ] Extract learning → `learnings/testing/qa/best_practices.md`
- [ ] Re-index learning file

## Instructions

### QA sign-off rule
```
ALL acceptance criteria ticked ✅
ALL test cases passed ✅
ALL breaking cases handled ✅
Browser checklist complete ✅ (web only)
           ↓
Feature is VERIFIED — safe to deliver
```
If ANY item fails → feature is BLOCKED. Do not deliver.

### Breaking cases checklist — always run these
```
- [ ] Empty input submitted
- [ ] Malformed or unexpected input submitted
- [ ] API returns error or timeout
- [ ] User triggers action twice simultaneously (race condition)
- [ ] Database has no records (empty state)
- [ ] User has no permissions
- [ ] Feature used on slow connection (3G simulation)
- [ ] Feature used with max data load (stress test)
```

### Browser verification checklist (web features only)
```
- [ ] Renders correctly on Chrome latest
- [ ] No console errors on load
- [ ] No console errors on all user interactions
- [ ] API responses return within acceptable timeout
- [ ] Empty state renders correctly (no data)
- [ ] Error state renders correctly (API failure)
- [ ] Loading state renders correctly (slow response)
- [ ] Mobile viewport renders without overflow
```

### QA result log format
```md
## QA Log — FC-[ID] [Feature Name]
Date: [Day, DD-Mon-YYYY · HH:MM IST]
Status: PASS / FAIL / BLOCKED

| Item | Type | Result | Notes |
|------|------|--------|-------|
| AC-01 | Acceptance | PASS | — |
| TC-01 | Test case | PASS | — |
| BC-01 | Breaking | FAIL | Empty input crashes — bug filed |
```

→ See `resources/quality-assuring_resources_test-patterns.md` for extended test patterns by feature type.

## Quality Control Measures
- [ ] Every acceptance criterion explicitly ticked or failed — no skips
- [ ] Every test case in the TC table executed
- [ ] All 8 breaking cases attempted
- [ ] Browser checklist run for all web features
- [ ] Feature card updated with QA log and date
- [ ] Updated card re-indexed into Context Mode MCP
- [ ] Learning extracted and stored

## Building User Trust
- Never sign off unless all items pass — never partial approval
- Always log failures with specific notes — not just "failed"
- Always update the feature card after QA — card is the source of truth

## Resources
- [Test patterns by feature type](resources/quality-assuring_resources_test-patterns.md) ← During test case execution
- [Bug filing template](resources/quality-assuring_resources_bug-template.md) ← When logging a failure
