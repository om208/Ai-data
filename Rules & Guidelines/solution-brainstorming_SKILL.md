---
name: solution-brainstorming
description: Runs structured brainstorming to explore and prioritise solutions
             for a confirmed problem. Use when user wants to explore what to
             build, asks for feature ideas, wants to compare solution approaches,
             or needs help deciding between multiple product directions.
---

# Solution Brainstorming
# Version: 1.0 | Created: Tuesday, 14-Apr-2026 · IST | Updated: —

## When to use this skill
- Problem and target user are confirmed — now exploring what to build
- User asks "what should we build" or "what are our options"
- Multiple solution directions exist — need to compare and pick
- Feature ideas need to be generated before writing PRD

## Workflow
- [ ] Confirm problem statement and target user are defined
- [ ] Ask 2–3 scoping questions (mandatory vs optional, scale, constraints)
- [ ] Generate 3 solution directions — each with different trade-offs
- [ ] Ask user to pick a direction or combine elements
- [ ] Within chosen direction, generate feature list (mandatory only by default)
- [ ] Ask: "Do you want optional features too, or mandatory only?"
- [ ] Present features grouped: Core → Supporting → Optional (if requested)
- [ ] Confirm feature list with user
- [ ] Save as `brainstorm/solution-brainstorm.md`
- [ ] Re-index into Context Mode MCP immediately after save
- [ ] Verify index updated
- [ ] Extract learning → `learnings/product_management/brainstorming/best_practices.md`
- [ ] Re-index learning file
- [ ] Hand off to `writing-prds` as next step

## Instructions

### Scoping questions — Round 1 (pick 2–3)
```
- Is this a large application or a small focused bot?
- Is this for personal use, a small team, or public users?
- Do you want mandatory features only, or optional too?
- Any hard constraints? (tech stack, timeline, compute budget)
```

### Solution direction format
```md
## Direction A — [Name]
- Core approach: [one sentence]
- Best for: [specific use case]
- Trade-off: [what it sacrifices]

## Direction B — [Name]
...

## Direction C — [Name]
...
```

### Feature list format — after direction is confirmed
```md
## Mandatory features
| # | Feature | Why needed | Effort est. |
|---|---------|------------|-------------|

## Optional features (only if user requested)
| # | Feature | Value added | When to add |
|---|---------|-------------|-------------|
```

### Brainstorm rules
- Max 3 questions per round — never one by one
- Default mode: mandatory features only
- Never generate optional features unless user explicitly asks
- All feature suggestions grounded in the market analysis (if done)
- Never jump to PRD — confirm full feature list first

→ See `resources/solution-brainstorming_resources_ideation-patterns.md` for SCAMPER, How Might We, and Crazy 8s frameworks.

## Quality Control Measures
- [ ] Never asked more than 3 questions in a single round
- [ ] 3 solution directions presented before picking one
- [ ] Mandatory vs optional features clearly separated
- [ ] Feature list confirmed by user before handoff to PRD
- [ ] File saved and re-indexed into Context Mode MCP
- [ ] Learning extracted and stored

## Building User Trust
- Always offer 3 directions — never push a single solution
- Always label features MANDATORY or OPTIONAL explicitly
- Always confirm the final feature list before writing any PRD

## Resources
- [Ideation frameworks](resources/solution-brainstorming_resources_ideation-patterns.md) ← During feature generation
- [Trade-off analysis guide](resources/solution-brainstorming_resources_tradeoff-guide.md) ← When comparing directions
