---
name: creating-feature-cards
description: Creates detailed feature cards with acceptance criteria, test cases,
             breaking cases, and verification checklists for every product feature.
             Use when a PRD is confirmed, when user says create a feature card,
             when breaking down features for development, or when defining done
             criteria for any functionality.
---

# Creating Feature Cards
# Version: 1.0 | Created: Monday, 13-Apr-2026 · IST | Updated: —

## When to use this skill
- PRD is confirmed and features need to be broken into cards
- User says "create a feature card" or "break down this feature"
- User needs acceptance criteria or test cases for a feature
- A feature is being iterated — card needs updating after a dev cycle

## Workflow
- [ ] Confirm PRD is finalised before creating any cards
- [ ] List all features from PRD — assign FC-[ID] to each
- [ ] For each feature, ask Round 3 depth questions if still unclear
- [ ] Draft feature card using standard structure below
- [ ] Iterate: identify breaking cases after initial draft
- [ ] Write test cases covering happy path, edge cases, breaking cases
- [ ] Build acceptance criteria checklist — every item must be verifiable
- [ ] Add browser verification checklist if feature is web-based
- [ ] Save to `feature_cards/FC-[ID]_[feature-name].md`
- [ ] Immediately re-index into Context Mode MCP — mandatory
- [ ] Verify index updated before showing card to user
- [ ] Confirm with user before marking card as ready

## Instructions

### Feature card standard structure
```md
# FC-[ID] — [Feature Name]
# Version: 1.0 | Created: [Day, DD-Mon-YYYY · HH:MM IST]

## Overview
- What this feature does
- Why it exists — user problem it solves

## Workflow
[Step-by-step flow of this feature]
Step 1 → Step 2 → Step 3 → Output

## Acceptance criteria
- [ ] Criterion 1 — specific and verifiable
- [ ] Criterion 2
- [ ] Criterion 3
[Rule: if ALL checkboxes pass → feature is approved and shippable]

## Test cases
| TC-ID | Scenario | Input | Expected output | Pass/Fail |
|-------|----------|-------|-----------------|-----------|
| TC-01 | Happy path | ... | ... | — |
| TC-02 | Edge case | ... | ... | — |
| TC-03 | Breaking case | ... | ... | — |

## Breaking cases
- Where can this feature possibly break?
- What inputs cause failure?
- What system states are dangerous?
- What happens at scale or under load?

## Dos and don'ts
| Do | Don't |
|----|-------|
| ... | ... |

## Browser verification checklist (web-based features only)
- [ ] Renders correctly on Chrome
- [ ] No console errors on load
- [ ] API responses valid and within timeout
- [ ] Edge interactions handled (empty state, error state, loading state)

## Iteration notes
[Updated after each dev cycle — what changed, what was missed, what broke]
```

### Acceptance criteria rule
- Every criterion must be independently verifiable — no vague criteria
- If all criteria pass → feature is approved. No exceptions.
- Criteria must cover: happy path, edge cases, error states

### Test case rule
- Minimum 1 happy path TC per feature
- Minimum 2 edge case TCs per feature
- Minimum 1 breaking case TC per feature
- TC-IDs are unique per card: TC-01, TC-02...

### Breaking cases thinking — iterate this list
```
- What if input is empty?
- What if input is malformed?
- What if the API is slow or returns an error?
- What if the user is on a slow connection?
- What if the database has no data?
- What if the user triggers this twice simultaneously?
- What if permissions are missing?
```

→ See `resources/creating-feature-cards_resources_breaking-cases-bank.md` for extended breaking case patterns by feature type.
→ See `resources/creating-feature-cards_resources_acceptance-criteria-patterns.md` for acceptance criteria templates.

## Quality Control Measures
- [ ] PRD confirmed before any card is created
- [ ] Every feature from PRD has an FC-[ID] assigned
- [ ] Acceptance criteria are all independently verifiable
- [ ] Minimum test cases met: 1 happy path, 2 edge, 1 breaking
- [ ] Breaking cases section is not empty
- [ ] Browser verification checklist present for all web-based features
- [ ] Card confirmed by user before marking ready

## Building User Trust
- Always iterate breaking cases after initial draft — never skip this step
- Always make acceptance criteria binary — pass or fail, never ambiguous
- Feature card is a paper-based reality of the feature — all dos/don'ts on paper before any code is written

## Resources
- [Breaking cases bank](resources/creating-feature-cards_resources_breaking-cases-bank.md) ← During breaking cases section
- [Acceptance criteria patterns](resources/creating-feature-cards_resources_acceptance-criteria-patterns.md) ← During acceptance criteria section
