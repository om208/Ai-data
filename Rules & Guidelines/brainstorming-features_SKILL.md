---
name: brainstorming-features
description: Runs structured multi-round brainstorming sessions to extract clear
             product requirements from the user before any building begins. Use
             when the user shares a new idea, wants to explore a concept, mentions
             building something, or when requirements are unclear or incomplete.
---

# Brainstorming Features
# Version: 1.0 | Created: Monday, 13-Apr-2026 · IST | Updated: —

## When to use this skill
- User shares a new idea or concept they want to build
- User says "I want to build X" — no matter how vague
- Requirements are unclear before writing a PRD
- User asks what features their product should have
- User is unsure what to include — needs guided exploration

## Workflow
- [ ] Acknowledge the idea — do not evaluate yet
- [ ] Ask Round 1 questions (scope + vision) — max 3 questions
- [ ] Wait for answers — process before proceeding
- [ ] Ask Round 2 questions (tech + preferences) — max 3 questions
- [ ] Wait for answers
- [ ] Ask Round 3 questions (feature depth) — max 3 questions
- [ ] Summarise what was understood — ask user to confirm
- [ ] If confirmed → hand off to `writing-prds` skill
- [ ] If not confirmed → ask one more focused round of questions

## Instructions

### Core rule — never jump to building
Always brainstorm before PRD. Always PRD before feature cards.
Never assume what the user wants. Always confirm before proceeding.

### Question rules
- Max 3 questions per round — never one by one
- Ask only mandatory questions — skip optional unless user requests
- Ground all suggestions in real comparable applications
- Default mode: mandatory features only
  - Ask first: "Do you want optional features too, or mandatory only?"

### Round 1 — Scope and vision
```
- Is this a large application or a small focused bot?
- Is this for personal use, a small team, or public users?
- Do you want it to do one thing very well, or handle multiple workflows?
- Mandatory features only, or should I suggest optional enhancements too?
```
Pick the 2–3 most relevant for the context.

### Round 2 — Tech and preferences
```
- Do you have a preferred frontend? (React, Vue, plain HTML, none)
- Do you have a preferred backend? (Python/FastAPI, Node, other)
- Any libraries or tools you already use or want to avoid?
- Any infrastructure preferences? (We are on Oracle Free Tier.)
```
Pick the 2–3 most relevant. If user has no preference → suggest
the most compute-efficient option for Oracle Free Tier.

### Round 3 — Feature depth
Ask these when user mentions a specific feature:
```
- What exactly should this feature do for the user?
- What should it NOT do? Any hard limits?
- Have you seen this done well in another app? Which one?
```
Never build a feature card without answering these first.

### Suggestion rule
- Never give random recommendations
- Always research comparable apps first, then suggest grounded features
- Label every suggestion clearly:
  - `[MANDATORY]` — core, cannot be skipped
  - `[OPTIONAL]` — nice to have (only if user requested optional mode)

### Clarification loop
```
After every round of answers:
  → Still unclear? → ask next batch of 2–3 focused questions
  → Clear enough? → summarise understanding → ask user to confirm
  → Confirmed?    → hand off to writing-prds skill
```

→ See `resources/brainstorming-features_resources_question-bank.md` for extended question sets by domain.

## Quality Control Measures
- [ ] Never asked more than 3 questions in a single round
- [ ] Never suggested optional features without user requesting them
- [ ] Never moved to PRD without user confirming requirements
- [ ] Suggestions grounded in real comparable apps — not generic
- [ ] Mandatory vs optional clearly labelled in all suggestions

## Building User Trust
- Always show what was understood before moving forward — let user correct it
- Never build on assumptions — every ambiguity gets a question
- Never overwhelm — 2–3 questions at a time, always

## Resources
- [Question bank by domain](resources/brainstorming-features_resources_question-bank.md) ← Round 1–3 extended questions per domain
- [Comparable apps reference](resources/brainstorming-features_resources_comparable-apps.md) ← When suggesting features grounded in real apps
