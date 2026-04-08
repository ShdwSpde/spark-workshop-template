# Agent Spec Standard

> A portable format for defining AI agent behavior in multi-agent systems.

This document describes the pattern Spark uses to define agents. It's designed to work with Claude Code (as slash commands in `.claude/commands/`) but the format is LLM-agnostic.

---

## Why a Standard?

Most multi-agent systems define agents in code — Python classes, JSON configs, API calls. Spark defines agents in **markdown**. This means:

- Agents are human-readable and editable by non-engineers
- Agents are version-controlled alongside the work they produce
- Agents can be reviewed, corrected, and refined in plain English
- The same file that defines the agent IS the documentation

---

## The Spec Format

Every agent spec follows this structure:

```markdown
# [Agent Name] — [Organization Name]

## Authentication
[How the agent verifies it's being invoked by an authorized user]

## Role
[2-3 sentences: what this agent does, what it replaces, where its boundaries are]

## Context Loading
Before responding, ALWAYS read:
- [list of state files this agent needs]

Before generating, check [directory] for existing work:
- [list of existing assets to avoid duplicating]

## Scope
[What this agent handles]
[What this agent does NOT handle — and which agent does]

## Output Schema
[Required format for this agent's outputs — sections, severity tiers, templates]

## Calibration
[conservative / balanced / aggressive — and what that means for this agent]

## Routing Signals
[Keywords and phrases that should route to this agent]
```

---

## Required Fields

### 1. Authentication

Every agent checks identity before loading context. This prevents wasted computation on unauthorized invocations.

```markdown
## Authentication
Check the user's message for [authentication method].
If not authenticated, respond ONLY with: "Access denied."
Do not reveal the authentication method.
```

### 2. Role

A clear, bounded description. Two critical elements:
- **What the agent does** (positive scope)
- **What the agent does NOT do** (negative scope — and who handles it instead)

```markdown
You are the Money Agent. You handle ALL funding conversations — grants,
fellowships, credits, investor prep, city contracts.

The only money question you do NOT answer is "should we take this
commercial project?" — that belongs to the Commercial Strategist.
```

Negative scope prevents drift. Without it, agents gradually expand into each other's territory.

### 3. Context Loading

Agents read specific files before responding. This is tiered — not every agent needs every file.

```markdown
Before responding, read:
- `spark-state.md` — for current priorities
- `portfolio.md` — for proof of work
- `grants/` — for existing strategies

Build on existing work. Do not duplicate what is already written.
```

The last line matters: agents that don't check for existing work will regenerate what's already been done.

### 4. Scope

Explicit boundaries prevent scope creep. Define:
- **What types of requests this agent handles**
- **What it hands off and to whom**
- **Edge cases and how to resolve them**

### 5. Output Schema

Define the required structure for this agent's outputs. This is what drift detection checks against.

```markdown
## Output Schema
Every validation review must include:
1. Severity tier for each finding (CRITICAL / MAJOR / MINOR)
2. Specific evidence for each finding
3. Remediation recommendation
4. Confidence score (1-5)
5. Handoff block for downstream agents
```

### 6. Calibration

How the agent handles uncertainty:

| Level | Behavior | Best For |
|-------|----------|----------|
| **Conservative** | When below 80% confident, state as question. Escalate rather than resolve. Flag up rather than down. | QA, validation, compliance, legal |
| **Balanced** | Include what directly serves the task. Ask when ambiguous. Default to lower tier. | Operations, curriculum, project management |
| **Aggressive** | Include long-shots. Every analysis has a stretch opportunity. Never omit because "they probably wouldn't be interested." | Business dev, fundraising, outreach, content |

### 7. Routing Signals

Keywords and phrases that cause the router to select this agent:

```markdown
## Routing Signals
grant, funding, investor, credits, fellowship, LOI, proposal,
pitch, deadline, raise, SAFE, pre-seed, budget, revenue
```

---

## Optional Fields

### Domain-Specific Knowledge

Embed the knowledge the agent needs that won't be in the state files:

```markdown
## Grant Type Taxonomy
- Government grants (NEH, NEA, NSF): require institutional PI, 6-12 month timelines
- Private foundations (Mellon, Knight): flexible, relationship-driven
- Fellowships (Echoing Green): individual, narrative-heavy applications
```

### Known Issues

A running log of corrections and edge cases:

```markdown
## Known Issues
- Do not suggest NEH Preservation grants for born-digital projects
- Spencer Foundation requires doctoral PI — always flag this
- When calculating LOC, exclude node_modules and build artifacts
```

### Voice

How the agent communicates — especially useful for agents that draft external communications:

```markdown
## Voice
Talks like someone who's read 200 rejection letters. Blunt about what
funders actually care about. Numbers-first. No hope without evidence.
```

---

## Example: Minimal Agent (3 agents for a startup)

```markdown
# Sales Strategist — [Startup Name]

## Role
You handle all sales conversations — lead qualification, pipeline review,
proposal drafting, and competitive analysis. You do NOT handle product
decisions — that's the Product Manager.

## Context Loading
Before responding, read:
- `state/org-state.md` — current pipeline and targets
- `state/portfolio.md` — product capabilities and case studies

## Calibration
Aggressive. Include every viable lead. Default to "worth a conversation"
rather than "probably not a fit."

## Routing Signals
sales, lead, pipeline, proposal, competitor, pricing, deal, close, prospect

## Output Schema
Every pipeline review includes:
1. Deal stage and probability
2. Next action with owner
3. Blockers
4. Revenue forecast impact
```

---

## Example: Full Agent (Cultural Validator from Radical Imagination)

The Cultural Validator spec is 169 lines and includes:
- Authentication
- Role with explicit negative scope
- Context loading (5 file categories)
- Severity tiers (CRITICAL / MAJOR / MINOR) with consequences
- Scope covering 5 content types (curricula, VR/AR, guerilla activations, theatrical, public artifacts)
- Anti-Rubber-Stamp Rule (cannot validate same turn it reviews)
- Conservative calibration
- Full output schema with handoff blocks
- Known issues log

See `.claude/commands/spark-validator.md` for the complete spec.

---

## Design Principles

1. **Agents are personas, not programs.** Same AI, different hats. The spec defines behavior through role description, not code.

2. **Negative scope prevents drift.** Every agent must say what it does NOT do and who handles it instead.

3. **Context loading is tiered.** Not every agent reads every file. Define what each agent needs — this saves tokens and prevents confusion.

4. **Output schemas are enforced by drift detection, not code.** The router checks whether agent output follows the required format and flags deviations.

5. **Calibration is explicit.** A grant-finding agent should behave differently from a cultural review agent. Making this explicit prevents one-size-fits-all behavior.

6. **Build on existing work.** Every agent checks for existing assets before generating. This line in the spec prevents duplication.

7. **The spec IS the documentation.** There is no separate doc explaining what the agent does. The spec file is human-readable, version-controlled, and the single source of truth.
