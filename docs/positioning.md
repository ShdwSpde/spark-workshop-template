# How Spark Differs from Other Multi-Agent Frameworks

> The short answer: Spark is infrastructure for operators. Everything else is a framework for developers.

---

## The Landscape

| Framework | What It Is | Who It's For | How Agents Are Defined |
|-----------|-----------|-------------|----------------------|
| **CrewAI** | Python framework for orchestrating role-playing AI agents | Developers | Python classes with role, goal, backstory |
| **LangGraph** | State machine framework for building agent workflows | Developers | Python graph nodes with state transitions |
| **AutoGPT** | Autonomous agent that recursively prompts itself | Enthusiasts | Config file with goals |
| **Microsoft AutoGen** | Multi-agent conversation framework | Researchers | Python agent objects with system messages |
| **OpenAI Assistants** | API-based assistants with tool use | Developers | API calls with instructions |
| **Spark** | Markdown-based operating system for organizations | Operators | Markdown files a non-engineer can edit |

---

## The Core Difference

Every framework above requires you to write code to define an agent. Spark requires you to write a text file.

```markdown
## Agent: Grant Writer
**Scope:** Finds and writes grants
**Calibration:** aggressive
**Files to read:** portfolio.md, org-state.md
**Files to write:** grants/
```

That's a working agent definition. No imports. No classes. No API keys. No deployment pipeline. A nonprofit director can customize this in a text editor.

---

## Five Structural Differences

### 1. State lives in markdown, not a database

Other frameworks store agent state in vector databases, Redis, or custom state objects. Spark stores everything in markdown files in a git repo.

**Why this matters:**
- `git blame` shows who changed what and when
- `git diff` shows exactly what changed between sessions
- Any human can read the state without tools
- No vendor lock-in — if you stop using Spark, your state files are still readable
- Version control is free and built-in

### 2. Memory is earned, not engineered

Other frameworks implement memory through embedding stores, retrieval chains, or conversation buffers. Spark's memory is a folder of markdown files that accumulate over time.

Each memory has a type (user preference, feedback, project context, reference), a description, and content. The AI reads relevant memories at session start. The human can read, edit, or delete any memory in a text editor.

**Why this matters:** The memory is transparent. There's no black box deciding what's remembered. You can open `memory/MEMORY.md` and see exactly what Spark knows about you.

### 3. Governance is built into the agent architecture

Other frameworks let agents do whatever their code allows. Spark has governance at the protocol level:

- **Risk levels:** Some actions auto-proceed. Some require human review. Some are propose-only.
- **Calibration:** Conservative agents (QA, validation) behave differently from aggressive agents (fundraising, outreach).
- **Anti-Rubber-Stamp Rule:** The validation agent cannot approve something the same turn it first reviews it.
- **Corrections protocol:** Human corrections are classified (factual, procedural, preference) and propagated appropriately.
- **Drift detection:** If an agent exceeds its scope, the system catches it.

**Why this matters:** In most frameworks, governance is your problem. In Spark, it's the system's job.

### 4. The session protocol creates institutional continuity

Other frameworks run agents on demand. Spark has a session protocol:

- **Start:** Read state files, check for contradictions, flag stale data, predict what's needed
- **End:** Update state files, log decisions, draft communications, write session summary

**Why this matters:** The protocol is what makes it an institution instead of a chatbot. Without it, every session starts from scratch. With it, the system maintains continuity across days, weeks, and months.

### 5. Agents are personas, not programs

In CrewAI, an agent is a Python class. In Spark, an agent is a persona — a role description, a voice, a scope, a calibration level, and a set of files to read.

The same AI adopts different personas based on which agent is active. There's no separate process, no API call, no microservice. One AI, eight hats.

**Why this matters:** Adding an agent takes 5 minutes (write a markdown file), not 5 hours (write a class, wire up tools, configure routing, deploy). Changing an agent's behavior means editing a text file, not redeploying code.

---

## When to Use What

**Use CrewAI / LangGraph if:**
- You're building a software product with agent features
- Your agents need to call APIs, query databases, or run code
- You have engineers who will maintain the agent infrastructure
- Your use case is technical (code generation, data pipelines, research automation)

**Use Spark if:**
- You're running an organization and need operational leverage
- Your agents manage state that humans also need to read and edit
- You don't have engineers (or don't want to spend engineering time on ops)
- Your use case is organizational (grants, curriculum, validation, portfolio management, reporting)
- You need governance, not just automation
- You want the system to be transparent and editable by non-technical team members

---

## The Honest Limitation

Spark runs on Claude Code, which means it's tied to Anthropic's subscription and API. The markdown architecture is portable (works with any LLM that can read files), but the MCP integrations (Gmail, Calendar, browser automation) are Claude Code features.

If Claude Code disappears tomorrow, the state files, agent specs, and protocols remain. The institution survives the tool.
