---
name: market-analyzing
description: Analyses the market for a product idea including target users,
             competitors, gaps, and positioning opportunities. Use when user asks
             to analyze the market, research competitors, understand users, find
             product gaps, or validate an idea against existing solutions.
---

# Market Analyzing
# Version: 1.0 | Created: Tuesday, 14-Apr-2026 · IST | Updated: —

## When to use this skill
- User wants to validate an idea against existing solutions
- User asks "who are the competitors" or "what does the market look like"
- Before finalising a PRD — market context must be understood
- User wants to find a positioning gap or differentiation angle

## Workflow
- [ ] Confirm product vision exists — if not, trigger `product-vision-crafting` first
- [ ] Identify market segment from the vision's target user
- [ ] Research 3–5 comparable products (grounded, not random)
- [ ] Build competitor comparison table
- [ ] Identify market gaps — where existing tools fail the user
- [ ] Define positioning angle based on gaps
- [ ] Save as `market/market-analysis.md`
- [ ] Re-index into Context Mode MCP immediately after save
- [ ] Verify index updated
- [ ] Extract learning → `learnings/product_management/market_research/best_practices.md`
- [ ] Re-index learning file
- [ ] Hand off to `solution-brainstorming` as next step

## Instructions

### Market analysis structure
```md
# Market Analysis — [Product Name]
# Version: 1.0 | Created: [Day, DD-Mon-YYYY · HH:MM IST]

## Target segment
[Who the market is. Size estimate if known.]

## Competitor comparison
| Product | Strengths | Weaknesses | Price | Target user |
|---------|-----------|------------|-------|-------------|
| ...     | ...       | ...        | ...   | ...         |

## Market gaps
- [Gap 1 — what existing tools fail to do for the user]
- [Gap 2]
- [Gap 3]

## Positioning angle
[How this product wins by filling the most critical gap.]

## Risks
- [What could invalidate this analysis]
- [What assumptions are being made]
```

### Research rules
- Only reference real, named comparable products — no generic examples
- Minimum 3 competitors — maximum 5 to keep it actionable
- Every gap must be tied to a specific user frustration, not a general claim
- Positioning must be unique — if it sounds like a competitor, rethink it

### Grounding rule
Before suggesting features based on market gaps, confirm with user:
"Based on this gap, should I add [X] as a mandatory feature to the PRD?"
Never add features silently — always confirm first.

→ See `resources/market-analyzing_resources_research-frameworks.md` for SWOT, Jobs-to-be-Done, and Blue Ocean frameworks.

## Quality Control Measures
- [ ] Minimum 3 real competitors researched and compared
- [ ] Market gaps are specific and user-grounded — not generic
- [ ] Positioning is differentiated from all 3+ competitors
- [ ] File saved and re-indexed into Context Mode MCP
- [ ] Learning extracted and stored
- [ ] Next phase (solution-brainstorming or PRD) suggested

## Building User Trust
- Always name real products in comparisons — never abstract examples
- Always ask before adding market-informed features to the PRD
- Always flag assumptions explicitly in the Risks section

## Resources
- [Research frameworks](resources/market-analyzing_resources_research-frameworks.md) ← During analysis phase
- [Gap identification guide](resources/market-analyzing_resources_gap-identification.md) ← When finding positioning angle
