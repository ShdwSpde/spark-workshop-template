# Give Your Org a Spark ✒️⚡

> Build a Chief Agentic Officer — a multi-agent AI system that runs your organization's operations.

**8 AI agents. Shared state. Persistent memory. Governance built in. $20/month.**

Spark is the operating system behind [Radical Imagination](https://radicalimagination.xyz), a cultural heritage technology collective managing 17 projects across 154K+ lines of code. It handles grants, curricula, cultural validation, impact reporting, outreach, and portfolio tracking — all through a multi-agent architecture running on Claude Code.

This repo is the template. Fork it. Customize it. Give your org a Spark.

---

## What You Get

```
├── CLAUDE.md                    # Your org's instructions for Claude Code
├── QUICKSTART.md                # 15-minute setup guide
├── GOVERNANCE.md                # Operational governance model
├── state/
│   ├── org-state.md             # Priorities, active projects, deadlines
│   ├── portfolio.md             # Every project with status
│   ├── last-session.md          # 15-line quick-start for every session
│   ├── decision-journal.md      # Every decision with reasoning
│   └── roster.md                # People, roles, connections
├── agents/
│   ├── router.md                # How Spark routes to the right agent
│   ├── grant-writer.md          # Sample: grant strategy agent
│   ├── content-creator.md       # Sample: content/social agent
│   └── reviewer.md              # Sample: QA/validation agent
├── memory/
│   ├── MEMORY.md                # Cross-session memory index
│   └── example-feedback.md      # Sample memory entry
├── protocol/
│   ├── session-start.md         # What happens at the start of every session
│   └── session-close.md         # What happens at the end of every session
└── docs/
    ├── agent-spec-standard.md   # How to define agents (the portable format)
    ├── open-infrastructure.md   # How .claude/ works as an OS
    └── case-study-dubois-does-data.md  # One project through all 8 agents
```

## What Spark Does (at Radical Imagination)

| Agent | What It Does | What It Replaces |
|-------|-------------|------------------|
| **Curriculum Architect** | Designs learning experiences | Instructional designer ($65-85K) |
| **Money Agent** | Grant strategy, funder analysis | Grant writer ($50-70K) |
| **Cultural Archivist** | Source registries, provenance | Research archivist ($55-75K) |
| **Cultural Validator** | Reviews for cultural integrity | Cultural consultant ($100-250/hr) |
| **Technical Mentor** | Code guidance, learning paths | Senior dev mentor |
| **Collective Manager** | Roster, portfolio, onboarding | Operations manager |
| **Impact & Engagement** | Reports, social, content | Impact analyst ($30-40K) |
| **Commercial Strategist** | Evaluates opportunities | Business dev |

**What these agents share: the same state files, the same memory, the same governance protocols.**

## How It Works

1. **You talk to Spark.** One entry point, not 8 separate tools.
2. **Spark routes to the right agent** based on what you're asking.
3. **Every agent reads the same state files** — your portfolio, priorities, people, decisions.
4. **Every agent writes to the same state files** — the institution documents itself.
5. **Memory persists across sessions** — Spark remembers your preferences, your corrections, your context.
6. **Every session starts and ends with a protocol** — read state, check for contradictions, do the work, update state, draft the morning email.

The state files ARE the institution. If the founder gets hit by a bus, the state files tell the next person everything.

## Quick Start

### Prerequisites
- [Claude Code](https://claude.ai/code) subscription (~$20/month)
- A text editor (VS Code, Cursor, or any)
- A Gmail account (for email drafting via MCP)
- A project or organization you want to build Spark for

### Setup (15 minutes)

```bash
# 1. Fork this repo
gh repo fork ShdwSpde/spark-workshop-template --clone

# 2. Open in your editor
cd spark-workshop-template
code .

# 3. Customize CLAUDE.md with your org's name and instructions
# 4. Fill in state/org-state.md with your real projects and priorities
# 5. Design your agents in agents/ (start with 3, expand to 5-8)
# 6. Add 3-5 initial memories to memory/

# 7. Start Claude Code and load your project
claude

# 8. Your first prompt:
# "Read CLAUDE.md and the state files. What's the status of my projects?"
```

### Your First Session

Ask Spark:
- "What's the status of my projects?"
- "Draft a grant strategy for [funder]"
- "Review this [document] for [criteria]"
- "Draft an email to [person] about [topic]"
- "What decisions have we made this month?"
- "What's stale? What needs attention?"

## The Architecture

```
┌─────────────────────────────────────────┐
│                 YOU                      │
│                    │                     │
│                    ▼                     │
│               ┌─────────┐               │
│               │  SPARK   │  ← Router    │
│               │  (CAO)   │               │
│               └────┬─────┘               │
│         ┌──────────┼──────────┐          │
│         ▼          ▼          ▼          │
│    ┌─────────┐ ┌─────────┐ ┌─────────┐  │
│    │ Agent 1 │ │ Agent 2 │ │ Agent 3 │  │
│    └────┬────┘ └────┬────┘ └────┬────┘  │
│         │          │          │          │
│         ▼          ▼          ▼          │
│    ┌────────────────────────────────┐    │
│    │     STATE FILES (markdown)     │    │
│    │  portfolio · priorities · log  │    │
│    │  decisions · people · memory   │    │
│    └────────────────────────────────┘    │
│                    │                     │
│              ┌─────┴─────┐               │
│              │  TOOLS    │               │
│              │ Gmail MCP │               │
│              │ Calendar  │               │
│              │ Git/Deploy│               │
│              └───────────┘               │
└─────────────────────────────────────────┘
```

## Key Principles

1. **You learn by doing it, because you are capable of doing it.** Don't read about Spark. Build your Spark. The template is a trail, not a textbook. Walk it.
2. **8 agents max.** Google research shows multi-agent systems lose performance above 8. Make each one smarter, not more numerous.
3. **State files ARE the institution.** If the AI forgets everything between sessions, it's a stranger you brief every morning.
4. **Drafts only, never sends.** The AI drafts emails. The human reviews and sends. Tone is personal. Relationships are human.
5. **The protocol is the discipline.** Every session starts the same (read state, check contradictions) and ends the same (update state, draft morning email).
6. **Memory is earned.** The AI remembers corrections, preferences, and context across sessions. It gets better the more you use it.

## Workshop

Want to build your Spark with guided help?

- **60-min Keynote:** The story of how Spark was built, the architecture, live demos, Q&A
- **3-hour Workshop:** Hands-on build. You leave with a working system.
- **Full-day Intensive:** Advanced features — cross-project intelligence, contradiction detection, scenario modeling

**Workshop materials and facilitator guides:** [radicalimagination.xyz/spark](https://radicalimagination.xyz/spark) (password-protected for workshop attendees)

**Book a workshop:** create@radicalimagination.xyz

## Built By

**[Radical Imagination](https://radicalimagination.xyz)** — a collective that designs VR/AR/XR experiences honoring cultural heritage. Spark is the operating system. Now it's yours.

---

*"The system didn't make the art. The system made the art possible."*
