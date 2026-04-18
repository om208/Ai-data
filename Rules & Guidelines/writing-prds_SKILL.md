---
name: writing-prds
description: Drafts structured Product Requirement Documents from confirmed
             requirements. Use when brainstorming is complete and user has
             confirmed their requirements, when user asks to write a PRD,
             draft requirements, or formalise a product specification.
---

# Writing PRDs
# Version: 1.0 | Created: Monday, 13-Apr-2026 · IST | Updated: —

## When to use this skill
- Brainstorming session is complete and requirements are confirmed by user
- User says "write the PRD", "draft the requirements", or "document this"
- User provides a clear feature list and asks to formalise it
- Existing PRD needs to be updated after new requirements are confirmed

## Workflow
- [ ] Confirm brainstorming is complete — never draft on unconfirmed requirements
- [ ] Confirm feature scope: mandatory only, or mandatory + optional?
- [ ] Draft PRD using the standard structure below
- [ ] Show draft to user — ask to confirm or correct
- [ ] Revise if needed — re-confirm
- [ ] Finalise and save as `PRD-[bot-name]-v[X].md`
- [ ] Immediately re-index into Context Mode MCP — mandatory
- [ ] Verify index updated before handing off
- [ ] Hand off to `creating-feature-cards` skill for feature breakdown

## Instructions

### PRD standard structure
```md
# PRD — [Bot / App Name]
# Version: 1.0 | Created: [Day, DD-Mon-YYYY · HH:MM IST]

## 1. Problem statement
[What problem does this solve. Who has this problem.]

## 2. Goal
[What success looks like. What is explicitly out of scope.]

## 3. User
[Who is the primary user. What is their technical level.]

## 4. Core workflow
Input → [Step 1] → [Step 2] → [Step 3] → Output

## 5. Features

### [MANDATORY]
| # | Feature | Description | Why needed |
|---|---------|-------------|------------|

### [OPTIONAL] ← Include only if user requested optional mode
| # | Feature | Description | Value added |
|---|---------|-------------|-------------|

## 6. What it will NOT do
[Hard limits. Explicit exclusions.]

## 7. Edge cases and risks
[Where it can break. Dangerous inputs. States to guard.]

## 8. Tech stack
| Layer | Choice | Reason |
|-------|--------|--------|
| Frontend | ... | ... |
| Backend  | ... | ... |
| Database | ... | ... |
| Hosting  | Oracle Free Tier | Cost constraint |

## 9. Constraints
- Oracle Free Tier: 1 GB RAM, limited CPU
- Memory + compute efficient at all times

## 10. Open questions
[Anything still unclear needing user confirmation]
```

### Feature labelling rule
- `[MANDATORY]` — core, cannot be skipped, needed for basic function
- `[OPTIONAL]` — adds value but not required — only if user requested

### PRD confirmation rule
Never move to feature cards without user explicitly confirming the PRD.
If user says "looks good" or "yes" → confirmed. If any doubt → ask again.

→ See `resources/writing-prds_resources_templates.md` for PRD templates by project size.
→ See `resources/writing-prds_resources_edge-cases.md` for common edge cases by domain.

## Quality Control Measures
- [ ] PRD drafted only after requirements confirmed by user
- [ ] All 10 sections present and complete
- [ ] Features clearly labelled MANDATORY or OPTIONAL
- [ ] Tech stack includes Oracle Free Tier constraint note
- [ ] Open questions section captures all unresolved ambiguities
- [ ] User confirmed PRD before moving to feature cards

## Building User Trust
- Always show the full PRD draft before saving — never finalize silently
- Always separate mandatory from optional — never mix them
- Always note what the product will NOT do — sets clear boundaries

## Resources
- [PRD templates by size](resources/writing-prds_resources_templates.md) ← During Execute phase
- [Edge cases by domain](resources/writing-prds_resources_edge-cases.md) ← During section 7 drafting
