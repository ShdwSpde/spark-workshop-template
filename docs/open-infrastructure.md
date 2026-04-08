# Open Infrastructure — How `.claude/` Works as an Operating System

> Most people using Claude Code have a blank CLAUDE.md. Spark has an operating system.

This document explains how the `.claude/` directory structure, combined with markdown state files, creates persistent multi-agent infrastructure that survives between sessions.

---

## The Three Layers

```
Layer 1: INSTRUCTIONS (loaded every session)
├── CLAUDE.md                    # Project-level instructions — rules, tech constraints, workflow
├── .claude/commands/*.md        # Agent definitions (invoked as /slash-commands)
└── .claude/rules/*.md           # Protocols loaded contextually by file type or topic

Layer 2: STATE (read and written by agents)
├── spark-state.md               # The map of everything in motion
├── portfolio.md                 # Every project with status
├── collective-roster.md         # People, roles, contributions
├── validation-log.md            # Cultural integrity tracking
├── activity-log.md              # Session-by-session work receipts
├── decision-journal.md          # Decisions with reasoning
└── source-health.md             # Trust scores per archive

Layer 3: MEMORY (persists across sessions)
└── .claude/projects/*/memory/
    ├── MEMORY.md                # Index of all memories
    ├── user_*.md                # Who the user is
    ├── feedback_*.md            # Corrections and preferences
    ├── project_*.md             # Project context and decisions
    └── reference_*.md           # External system pointers
```

---

## Layer 1: Instructions

### CLAUDE.md — The System Prompt

Loaded every time Claude Code starts. Contains:
- **Tech constraints** — "f-strings cannot contain dict literals", "Supabase batch ≤2000 rows"
- **Workflow rules** — "Plan first, then code", "Verify everything"
- **Security rules** — "Never read .env", "Never hardcode API keys"
- **Build/test commands** — Per-project run and test commands
- **When-to-use tables** — Which skill/agent for which task

This file is the error log. When the AI does something wrong, it goes here immediately. The team updates it multiple times per week.

### .claude/commands/ — Agent Definitions

Each file in this directory becomes a `/slash-command`:
- `spark.md` → `/spark` (the router)
- `spark-grants.md` → `/spark-grants` (Money Agent)
- `spark-validator.md` → `/spark-validator` (Cultural Validator)

See [agent-spec-standard.md](agent-spec-standard.md) for the specification format.

### .claude/rules/ — Contextual Protocols

Rules files are loaded when relevant. They contain:
- **Corrections protocol** — How human corrections propagate (3 tiers)
- **Drift detection** — How the system catches agents exceeding their scope
- **Agent calibration** — Conservative, balanced, aggressive behavior settings
- **Anti-Rubber-Stamp Rule** — Validation cannot happen in the same turn as first review
- **Session close checklist** — What gets updated at end of every session
- **Cross-project intelligence** — How Spark finds connections across the portfolio

---

## Layer 2: State

The state layer is what makes Spark an institution instead of a chatbot.

### Design Principles

**Markdown, not databases.** State files are version-controlled, human-readable, diffable, and portable. No vendor lock-in. No schema migrations. `git blame` shows who changed what and when.

**Hot/cold split.** `spark-state.md` is ~80 lines of live state. Historical entries move to `spark-state-archive.md`. This keeps the active state file fast to read.

**Every agent reads the same files.** There's no agent-specific database. The portfolio is the portfolio. The roster is the roster. Agents see the same truth.

**Every agent writes to the same files.** When the Money Agent finds a deadline, it updates `spark-state.md`. When the Collective Manager onboards someone, it updates `collective-roster.md`. The state evolves through use.

**Versioned and timestamped.** Every state file has frontmatter:

```yaml
---
version: 5
last_modified: 2026-04-03
last_agent: Spark CAO
---
```

### File Roles

| File | What It Tracks | Who Writes It |
|------|---------------|---------------|
| `spark-state.md` | Priorities, deadlines, active projects, team status | Any agent |
| `portfolio.md` | Every project — status, tech, LOC, validation | Collective Manager (primary) |
| `collective-roster.md` | People — roles, skills, availability, contributions | Collective Manager |
| `validation-log.md` | Cultural integrity — flagged, blocked, validated | Cultural Validator |
| `activity-log.md` | What was built each session (one-liners) | Any agent |
| `decision-journal.md` | Decisions with reasoning, alternatives, confidence | Any agent |
| `source-health.md` | Trust scores per archive topic | Cultural Archivist |

### Contradiction Detection

At session start, Spark reads all state files and checks:
- Portfolio status matches validation log status?
- Project counts are consistent across files?
- Any file not updated in 7+ days?
- Active decisions that haven't been acted on?

Contradictions are reported immediately. This is how the system self-heals.

---

## Layer 3: Memory

Memory persists across conversations. It's how Spark learns your preferences, remembers corrections, and maintains context about ongoing work.

### Memory Types

| Type | What It Stores | Example |
|------|---------------|---------|
| `user` | Role, goals, expertise, preferences | "Deep Go expertise, new to React" |
| `feedback` | Corrections and confirmed approaches | "Don't give unsolicited task lists" |
| `project` | Ongoing work, deadlines, decisions | "Merge freeze begins Mar 5" |
| `reference` | Pointers to external systems | "Bugs tracked in Linear project INGEST" |

### How Memory Works

Each memory is a markdown file with frontmatter:

```markdown
---
name: communication_style
description: User prefers direct, no corporate language
type: feedback
---

Be direct. No buzzwords. Say what you mean.

**Why:** User corrected corporate tone 3 times in first week.
**How to apply:** All outputs — emails, reports, strategies.
```

`MEMORY.md` is the index — one line per memory, loaded every session. The full memory files are read on demand when relevant.

### What Makes Memory Different from State

- **State** = the organization's current reality (projects, people, decisions)
- **Memory** = how to work with this specific user (preferences, corrections, context)

State changes every session. Memory accumulates over weeks and months.

---

## How to Adopt This Structure

### Minimum viable setup (15 minutes)

```
your-project/
├── CLAUDE.md              # Your rules and constraints
├── .claude/commands/
│   └── router.md          # Your agent router (start with 3 agents inline)
└── state/
    ├── org-state.md       # Priorities and projects
    └── last-session.md    # Session continuity
```

### Full setup (1-2 hours)

```
your-project/
├── CLAUDE.md
├── .claude/
│   ├── commands/          # One file per agent
│   └── rules/             # Protocols (corrections, drift, session close)
├── state/
│   ├── org-state.md
│   ├── portfolio.md
│   ├── roster.md
│   ├── decision-journal.md
│   └── last-session.md
└── memory/
    ├── MEMORY.md
    └── [memory files]
```

### The key insight

The `.claude/` directory is not configuration. It's infrastructure. The commands are your org chart. The rules are your operating manual. The state files are your institutional brain. Together, they make the AI a colleague instead of a tool.
