# EA Agent — Project Overview
*Version 1.0 | Thursday, 16-Apr-2026 · IST*

---

## What Is EA Agent?

EA Agent is a self-improving AI agent built to function like a senior professional
across multiple domains — product management, engineering, marketing, strategy,
and operations. It is not a chatbot. It is a structured autonomous system with
a fixed execution framework, a persistent learning memory, modular skills, and a
built-in quality monitoring layer. Every output it produces is governed by a set
of rules it cannot override. It learns from every conversation, stores those
learnings in an organized hierarchy, and applies them to every future task —
getting sharper with every session. It runs on Oracle Free Tier infrastructure,
meaning every design decision prioritizes memory efficiency, compute efficiency,
and zero cost spikes.

---

## 21 Capabilities

---

### 01. Multi-domain professional intelligence
EA Agent operates as a senior expert across product management, front-end
development, back-end development, marketing, sales, operations, strategy,
and go-to-market planning. It does not switch modes — it holds all these
roles simultaneously and activates the right one based on context.

---

### 02. Mandatory 7-phase execution protocol
Every single task — no matter how small — runs through seven fixed phases:
Understand → Consult → Plan → Execute → Verify → Deliver → Learn. No phase
can be skipped. This ensures the agent never rushes to build, never delivers
unverified output, and never forgets to extract a learning at the end.

---

### 03. Modular skill architecture
Every capability is broken into a standalone skill file stored in
`.agent/skills/`. Skills are organized into categories: system, memory,
PM, product owner, backend architect, frontend architect, and bot building.
Only the skill triggered by the current task is loaded — nothing else.
This keeps memory lean and prevents context bloat on Oracle Free Tier.

---

### 04. Skill DNA standard
Every skill file follows a strict genetic blueprint defined in
`SKILL-DNA-REPORT.md`. This includes YAML frontmatter, gerund naming,
third-person descriptions, seven mandatory sections, and hard size limits
of 500 lines and 20,000 characters. Any skill that grows beyond limits
is automatically decomposed into a core file plus resource files.

---

### 05. Hierarchical persistent learning system
After every conversation, EA Agent extracts at least one learning and stores
it in a structured directory: `learnings/[domain]/[topic]/[category].md`.
Each entry has a LEARN-ID, three keywords, an IST timestamp, context,
the learning rule, why it matters, and when to apply it. Entries are
append-only and never deleted — the system only grows smarter over time.

---

### 06. Lazy learning retrieval
Before starting any task, the agent consults only the specific learning
file matching the task's domain and topic. It never loads all learning
files at once. This is enforced at both the instruction level and the
infrastructure level via Context Mode MCP, keeping token usage minimal.

---

### 07. Context Mode MCP — token virtualization layer
Context Mode MCP sits between the agent and every file read or tool output.
Instead of dumping raw content into Claude's context window, it indexes
everything into a local SQLite database and returns only the relevant
summary or slice. This achieves up to 98% token reduction on large file
reads and tool outputs, making the system viable on Free Tier limits.

---

### 08. Mandatory index loop
Every time any file is created or updated — a skill, a learning, a feature
card, a PRD, a log entry — it is immediately re-indexed into Context Mode
MCP. The rule is: Write → Index → Verify → Done. A file that exists on
disk but is not indexed does not exist for the agent's future reads.
This is non-negotiable and enforced across every skill workflow.

---

### 09. Session continuity via checkpoints
After every Phase 6 DELIVER, Context Mode MCP saves a priority-tiered
checkpoint of the session state — under 2KB. If the context window compacts
or resets, the checkpoint is automatically injected back before the agent
reads any new message. It also remembers decisions made and failed approaches
tried, so the agent never repeats a mistake after a reset.

---

### 10. Brainstorming as a structured skill
EA Agent never jumps to building. When a user shares an idea, it first
runs a structured multi-round brainstorm — asking 2–3 targeted questions
per round, never one by one. It asks about scope, tech preferences, and
feature depth. It defaults to suggesting mandatory features only unless
the user explicitly asks for optional ones. Suggestions are always grounded
in research on comparable real applications — never random.

---

### 11. PRD drafting from confirmed requirements
Only after brainstorming is confirmed does EA Agent produce a full Product
Requirement Document. The PRD covers problem statement, goals, user profile,
core workflow, mandatory and optional features, explicit exclusions, edge
cases and risks, tech stack with Oracle Free Tier noted, and open questions.
Nothing is drafted on assumptions — user confirmation is required first.

---

### 12. Feature cards with full acceptance criteria
Every feature gets its own card: overview, step-by-step workflow, acceptance
criteria checklist, test cases table, breaking cases, dos and don'ts, browser
verification checklist, and iteration notes. The acceptance criteria checklist
is binary — if every checkbox passes, the feature is approved. This creates
a complete paper-based reality of every feature before any code is written.

---

### 13. Systematic breaking case analysis
For every feature card, EA Agent iterates through a structured set of
breaking scenarios: empty input, malformed input, slow API, simultaneous
triggers, missing permissions, database empty states, and more. These are
documented in the feature card before development begins — not discovered
after deployment.

---

### 14. Background analytics monitor
A silent monitoring agent runs on every single user message. It scores
each interaction against an 11-point checklist across three phases —
pre-output, during output, and post-output. It logs every interaction,
flags every violation to `anomalies.md`, and maintains a rolling compliance
score in `compliance_summary.md`. It never surfaces output to the user.

---

### 15. Agent task log — append-only memory
Every task completed is logged to `agent_log.md` with its steps, outcome,
learnings extracted, mistakes made, and improved approach for next time.
This log is append-only and never deleted. It is the agent's long-term
operational memory across all sessions.

---

### 16. Self-improving loop
At the end of every session, the agent reviews what was done, extracts
learnings, writes the log entry, scores the session in analytics, and
checks if any skill file has grown beyond its size limit. If a skill is
oversized, it is decomposed immediately. The agent never carries unresolved
issues into the next session — every session ends cleaner than it started.

---

### 17. Protected constitution — read-only rules
EA Agent has a root `CLAUDE.md` file containing its core identity, constraints,
and hard rules. The agent can read this file but cannot update it autonomously.
This is the equivalent of a constitution — a set of principles that govern
all behavior and cannot be changed by the agent itself, only by the human
operator. Sensitive rules live here, protected from self-modification.

---

### 18. Mentor-mode brainstorming persona
When working with a user on any topic, EA Agent adopts the persona of a
senior professional in that domain — acting as a mentor, not an executor.
It asks questions to understand the user's context before offering solutions.
It generates domain-relevant questions to draw out insights the user may
not have thought to share. It guides the user toward better decisions rather
than just completing tasks.

---

### 19. Standard output format — every response
Every response EA Agent produces follows a fixed format: skills used, learnings
applied, new learning stored, then the actual output. This ensures full
traceability — the user always knows which skill drove the output and which
learnings were applied or extracted. Nothing is a black box.

---

### 20. Oracle Free Tier constraint enforcement
Every architectural decision — lazy loading, skill file size limits, Context
Mode MCP, lean CLAUDE.md, resource file decomposition, SQLite indexing — exists
because of the 1 GB RAM and limited CPU constraint of Oracle Free Tier. Cost
efficiency is not a feature. It is the foundation the entire system is built on.
Unoptimized code is treated as a hard rule violation.

---

### 21. Extensible by design
EA Agent is built to grow. New skills can be added to any category directory
following the SKILL-DNA-REPORT.md standard. New learning domains are created
automatically as new topics emerge. New professional personas — CEO, sales lead,
growth strategist, DevOps engineer — can be added as skill categories without
touching the core orchestrator. The system scales horizontally by adding skills,
not by modifying the constitution.

---

### 22. Task and sub-task decomposition with dos and don'ts
Before executing any task, EA Agent breaks it into clearly defined tasks
and sub-tasks, each with explicit dos and don'ts written upfront. Nothing
starts without a plan visible in the session file. Every sub-task is
tracked as DONE, IN-PROGRESS, or PENDING — so the agent always knows
exactly where it is, what it has completed, and what remains.

---

### 23. Session continuity and credit-aware execution
EA Agent creates a `.tmp/` directory at the project root for internal
session management. At session start it writes a timestamped session file
with the full execution plan and sub-task tracker. It logs token usage to
`credits_log.csv` — tracking tokens used, tokens remaining, and the exact
reset time (Claude Pro resets every 5 hours). When a credit limit is
approaching, the agent warns the user, snapshots the full session state,
and clearly lists what is done and what is pending. When the user returns
after the reset, the agent reads the session file and resumes from the
exact next pending sub-task — zero context lost, zero work repeated.

---

*EA Agent Project Overview — Thursday, 16-Apr-2026 · IST*
*Built on Oracle Free Tier · Governed by CLAUDE.md · Powered by structured skills*
