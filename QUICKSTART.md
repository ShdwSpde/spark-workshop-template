# Quickstart — Build Your Spark in 15 Minutes

## Prerequisites

- [Claude Code](https://claude.ai/code) subscription (~$20/month)
- Git installed
- A text editor (VS Code, Cursor, or any)
- An organization, project, or practice you want to build Spark for

## Step 1: Fork the Template

```bash
# Fork and clone the template
gh repo fork ShdwSpde/spark-workshop-template --clone
cd spark-workshop-template
```

## Step 2: Define Your Mission (2 minutes)

Open `CLAUDE.md` and replace the placeholders:

```markdown
# [Your Org Name] — Claude Code Instructions

## About
[One sentence about your org and what it does.]
```

This file is loaded every time Claude Code starts. It's the system prompt for your entire organization.

## Step 3: Design Your Agents (5 minutes)

Open `agents/` and customize the sample agents. Start with 3. You can expand to 5-8 later.

Each agent needs:

```markdown
## Agent: [Name]
**Scope:** What this agent handles
**Intent signals:** Keywords that route here (e.g., "grant", "funding", "budget")
**Voice:** How this agent communicates
**Calibration:** conservative / balanced / aggressive
**Files to read:** Which state files this agent needs
**Files to write:** Which state files this agent updates
```

See [docs/agent-spec-standard.md](docs/agent-spec-standard.md) for the full specification format.

**Common starter rosters:**

| Org Type | Agent 1 | Agent 2 | Agent 3 |
|----------|---------|---------|---------|
| Nonprofit | Grant Writer | Program Manager | Communications |
| Startup | Product Manager | Sales Strategist | Operations |
| Research Lab | Literature Reviewer | Grant Writer | Data Analyst |
| Creative Studio | Project Manager | Client Strategist | Quality Reviewer |
| Education | Curriculum Designer | Assessment Lead | Outreach |

## Step 4: Fill Your State Files (5 minutes)

Open `state/` and populate with your real data:

**`state/org-state.md`** — Your priorities and active projects:
```markdown
## Quick Status
- **Active projects:** 3
- **Next deadline:** [date] — [what]
- **Team:** [who's involved]

## Active Projects
| Project | Status | Focus |
|---------|--------|-------|
| [Project 1] | in progress | [what's happening] |
```

**`state/portfolio.md`** — Everything you've built or are building.

**`state/roster.md`** — People, roles, and how they connect.

**`state/last-session.md`** — Leave blank for now. Spark fills this at the end of every session.

## Step 5: Seed Your Memory (2 minutes)

Open `memory/MEMORY.md` and add 3-5 initial memories:

```markdown
# Memory Index

- [feedback_communication_style.md](feedback_communication_style.md) — Direct communication, no corporate speak
- [project_grant_deadline.md](project_grant_deadline.md) — NEA deadline July 9, application in progress
- [user_background.md](user_background.md) — 10 years in nonprofit, new to AI tooling
```

Create one memory file as an example:

```markdown
---
name: communication_style
description: User prefers direct communication without corporate language
type: feedback
---

Be direct. No buzzwords. No "leverage" or "synergize." Say what you mean.

**Why:** User has explicitly corrected AI outputs that used corporate tone.
**How to apply:** All agent outputs — emails, reports, strategies — should be conversational and clear.
```

## Step 6: Run Your First Session

```bash
# Open Claude Code
claude

# Your first prompt:
"Read CLAUDE.md and the state files. What's the status of my projects?"
```

Spark reads your state files and responds with intelligence about YOUR organization.

**Next prompts to try:**
- "Draft a grant strategy for [funder you're interested in]"
- "Review this [document] for [quality criteria]"
- "What decisions have we made this month?"
- "Draft an email to [person] about [topic]"

## Step 7: End Your First Session

Before closing, ask:
- "Update the state files with what we did today"
- "Write a session summary to last-session.md"
- "Log any decisions we made"

This is the protocol. Every session starts by reading state and ends by updating it. The discipline is what makes it an institution instead of a chatbot.

---

## What's Next

- **Add more agents** as you discover what your org actually needs (max 8)
- **Add session protocols** — `protocol/session-start.md` and `protocol/session-close.md`
- **Connect tools** — Gmail MCP for email drafting, Google Calendar for deadline tracking
- **Build memory** — Every correction and preference you give Spark makes it sharper
- **Read the full architecture:** [docs/open-infrastructure.md](docs/open-infrastructure.md)

## Common Questions

**Can I use GPT/Gemini instead of Claude?**
The pattern works with any LLM that supports tool use. Claude Code is recommended because MCP integrations (Gmail, Calendar, Drive) are built-in.

**Does this work for teams?**
Each team member can run their own Spark instance sharing state files via git. Federated agents with shared institutional memory.

**What if I'm not technical?**
Basic comfort with a text editor and terminal is enough. No coding required. The state files are plain markdown.

**How is this different from ChatGPT?**
ChatGPT forgets everything between conversations. Spark has persistent state files, memory across sessions, multiple agent personas, governance protocols, and tool integrations. It's the difference between texting a stranger and having a COO.
