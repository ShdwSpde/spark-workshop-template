# Give Your Org a Spark: Building a Chief Agentic Officer

> *"We accidentally built the operating system for a one-person studio. Then we realized it's a product."*

---

## Overview

**What this is:** A lecture + workshop curriculum about building multi-agent AI systems for real organizational operations. Not theoretical — built from the actual Spark system running Radical Imagination (155K LOC, 17 projects, 1 founder, 8 AI agents).

**Two formats:**
1. **The Keynote (60 min):** History, architecture, demos, Q&A. Entertaining, data-driven, honest about failures.
2. **The Workshop (3 hours):** Hands-on build. Participants leave with their own working Spark — agents, state files, memory, and a session close protocol.

**Target audience:** Founders, nonprofit leaders, studio directors, technical educators, operations managers. Anyone running more ambition than headcount.

**Prerequisite:** A Claude Code subscription (or willingness to sign up during the workshop). No coding experience required for the keynote. Basic comfort with a terminal for the workshop.

**Delivery modes:** In-person facilitated (primary), virtual synchronous (Zoom with screen share)

---

## THE KEYNOTE (60 minutes)

### The Story Arc

The keynote follows the actual build history of Spark — from a one-man studio drowning in tasks to a multi-agent system that found 30 cross-project connections in one scan. It's a founder story, a technical architecture talk, and a live demo wrapped in one.

**Tone:** Funny. Self-deprecating about the failures. Data-driven about the wins. Hands-on enough that the audience can picture building their own. Not a sales pitch — a story about what happens when you give your organization a brain.

---

### Slide-by-Slide Breakdown

#### ACT 1: THE PROBLEM (10 min)

**Slide 1: Title**
"Give Your Org a Spark: Building a Chief Agentic Officer"
Mike Spade, Radical Imagination
[Spark's self-portrait — the avatar it drew of itself + the reasoning it gave for the design choices. This is the funny opening.]

**Slide 2: The Setup**
"I'm one person running 17 projects across 155,000 lines of code with zero funding."
[Show the portfolio quick-reference table. Let the number land.]
"I needed to hire 5 people. I had $20/month."

**Slide 3: What I Actually Need**
The 5 roles Spark replaces:
- Grant writer ($50-70K)
- Instructional designer ($65-85K)
- Research archivist ($55-75K)
- Cultural consultant ($100-250/hr)
- Impact analyst ($30-40K)
"Total: ~$250K/year. My budget: one Claude subscription."

**Slide 4: The Bad Version**
"First I just asked Claude to do stuff. Like everyone."
[Screenshot of a generic ChatGPT conversation — no context, no memory, no structure. The answer is fine but useless the next day.]
"The problem isn't the AI. The problem is that it forgets everything between conversations."

**Slide 5: The Realization**
"What if the AI could remember? What if it had a job description? What if it had FILES to read? What if it had COLLEAGUES?"
[This is the moment the keynote shifts from problem to solution.]

#### ACT 2: THE ARCHITECTURE (15 min)

**Slide 6: Meet Spark**
[Spark avatar + one-line descriptions of all 8 agents]
"Spark is the Chief Agentic Officer. You talk to Spark. Spark routes to the right agent."
[Show the routing table: intent signals → agent]

**Slide 7: The 8 Agents**
| Agent | What They Do | What They Replace |
|-------|-------------|-------------------|
| Curriculum Architect | Designs learning experiences | Instructional designer |
| Money Agent | Grant strategy, funder analysis | Grant writer |
| Cultural Archivist | Source registries, provenance | Research archivist |
| Cultural Validator | Reviews for integrity | Cultural consultant |
| Technical Mentor | Learning paths, code guidance | Senior dev mentor |
| Collective Manager | Roster, portfolio, onboarding | Operations manager |
| Impact & Engagement | Reports, social, content | Impact analyst |
| Commercial Strategist | Evaluates opportunities | Business dev |

"Google's research says multi-agent systems lose performance above 8 agents. So we stopped at 8 and made each one smarter."

**Slide 8: The State Layer**
"The agents share a BRAIN. Not a database — markdown files in a git repo."
[Show the state file architecture:]
- spark-state.md (80 lines — the map of everything in motion)
- portfolio.md (every project with status, LOC, validation)
- collective-roster.md (people, roles, connections)
- validation-log.md (cultural integrity tracking)
- activity-log.md (session-by-session receipts)
- decision-journal.md (every decision with reasoning)
- source-health.md (trust scores per archive)

"Every agent reads the same files. Every agent writes to the same files. The state IS the institution."

**Slide 9: The Memory System**
"Spark remembers across conversations."
[Show MEMORY.md — 30 memory files covering user preferences, project context, feedback, references]
"I told Spark once: 'stop giving me task lists.' It never did it again. Across every future session."

**Slide 10: The Authentication**
[Show the 🔥⚡ emoji sequence]
"Yes, the CEO of my AI system is locked behind a fire emoji and a lightning bolt. Security through obscurity? No. Security through absurdity."
[This is the laugh moment.]

**Slide 11: The Session Protocol**
"Every session starts the same way: read last-session.md, check for contradictions, flag stale files, predict what I'll need."
"Every session ends the same way: update state files, draft a morning email, log what was built."
"The institution documents itself."

**Slide 12: The Email System**
[Live Gmail screenshot showing a Spark-drafted morning email]
"Spark drafts every email. I review and send. It never sends automatically."
"Why? Because tone is personal. Relationships are human. And sent emails can't be unsent."
"But the DRAFT is better than what I'd write from scratch — because Spark has the full project context."

#### ACT 3: THE SUPERPOWERS (15 min)

**Slide 13: Cross-Project Intelligence**
"Yesterday, Spark scanned 17 projects and found 30 connections I'd never seen."
[Show 3 of the best connections:]
1. A component built for one VR experience that upgrades another
2. A scholar who bridges 3 different archive projects
3. A font file duplicated across 4 projects wasting 8.6MB

"A 10-person team discovers these in weekly standups. Spark found them in one pass."

**Slide 14: The Decision Journal**
"Every non-trivial decision is logged with reasoning and alternatives."
[Show a real entry: "8th Wall over MindAR. Alternatives: WebXR (no iOS), keep MindAR (worse tracking). Reasoning: free, MIT, iOS+Android. Confidence: 5/5. Reversible: yes."]
"Six months from now, when someone asks 'why did you choose this?' — the answer is searchable."

**Slide 15: Confidence Scoring**
"Every agent output comes with a confidence score."
[Show: "Confidence: 3/5 — based on secondary sources, community consultation not yet done, significant gaps in Garvey archive."]
"The AI tells you when it doesn't know. That's rarer than you think."

**Slide 16: The Contradiction Detector**
"Spark reads all state files and flags when they disagree."
[Show a real contradiction: "portfolio says Douglass is 'feature-complete' but validation log says 'active build'"]
"No stale data survives."

**Slide 17: The Scenario Engine**
"'What if we skip Juneteenth and focus on July 4?' Spark models the downstream impact."
[Show the real scenario analysis with positive/negative consequences]
"Every major decision gets modeled against the REAL state of the organization."

**Slide 18: What It Actually Costs**
- Claude Code subscription: ~$20/month
- Gmail MCP: free (OAuth)
- Google Calendar MCP: free
- Git repo: free
- Total: $20/month for a system that replaces $250K/year of specialized labor

"The ROI is absurd. But the value isn't the cost savings. The value is that one person can operate like a ten-person company."

#### ACT 4: THE HONEST PART (10 min)

**Slide 19: What Spark Can't Do**
- Can't replace community relationships (scholars, funders, partners)
- Can't validate cultural authenticity (only communities can)
- Can't attend events (you still show up in person)
- Can't make creative judgments (it enhances yours, doesn't replace them)
- Can't send email (drafts only — human sends)
"The founder is still the founder. Spark is the COO."

**Slide 20: The Failures**
[Be honest. Show real failures:]
- "Spark downloaded 2 portraits of white men from the Library of Congress and put them in a Black liberation VR experience. I had to check every image by hand."
- "The crowd silhouettes in the Douglass experience were box geometry with spheres for heads. My founder feedback: 'bruh, can't tell those are humans.'"
- "We built 81 image planes into 7 scenes and the founder said 'some of these scenes are overwhelming.' We had to thin to 3-4 per scene."
"The system is powerful. It's not perfect. Human oversight isn't a limitation — it's the design."

**Slide 21: The Anti-Rubber-Stamp Rule**
"The Cultural Validator cannot approve something the same turn it first encounters it."
"First response is always findings and questions. Never 'looks good.'"
"This is the most important rule in the system. Without it, the AI just tells you what you want to hear."

#### ACT 5: THE CLOSE (10 min)

**Slide 22: What You Can Build**
"Every organization with more ambition than headcount needs this."
- Nonprofits with one program manager and 5 programs
- Studios with one creative director and 10 projects
- Startups with one founder and zero employees
- Research labs with one PI and 20 projects
"If you have a Claude subscription and a git repo, you can have a Spark by end of day."

**Slide 23: The Workshop Preview**
"In 3 hours, you will build:"
1. Your own agent roster (3-5 agents tailored to YOUR org)
2. Your state file system (portfolio, priorities, people)
3. Your memory layer (cross-session persistence)
4. Your session protocol (how every work session starts and ends)
5. Your first Gmail-integrated email draft
"You leave with a working system. Not a slide deck about a system."

**Slide 24: The Ops Dashboard**
[Live screenshot of ops.radicalimagination.xyz]
"Everything Spark knows is visible on the dashboard. The calendar. The budget. The war room. The handoff docs."
"The institution doesn't need the founder in the room to know what's happening."

**Slide 25: The Line**
"155,000 lines of code. 17 projects. 1 founder. 0 funding. 8 AI agents. $20/month."
"The system didn't make the art. The system made the art POSSIBLE."

**Slide 26: Q&A**
[Open floor. 10 minutes.]

---

## THE WORKSHOP (3 hours)

### Prerequisites
- Claude Code installed (or Claude.ai account for non-technical participants)
- A Gmail account
- A text editor (VS Code recommended, any works)
- A project or organization they want to build Spark for (even if it's just an idea)

### Materials Provided
- Workshop template repo (GitHub link) with:
  - Empty state file templates (spark-state.md, portfolio.md, etc.)
  - Example agent skill files
  - Example memory files
  - Session protocol template
  - CLAUDE.md template
- This curriculum as a facilitator guide
- Spark architecture diagram (printable)

---

### Session Flow

#### HOUR 1: Design Your Agents (60 min)

**Warm-Up: Who Does Your Work? (10 min)**
- Participants list every role their organization needs but can't afford
- Group share: what patterns emerge? (everyone needs a grant writer, everyone needs a content person)
- "These roles become your agents."

**Skill-Building: Agent Design (20 min)**
- Walk through Spark's routing table: intent signals → agent
- Explain the persona model: each agent has a voice, a scope, a calibration (conservative vs aggressive)
- Show a real agent spec (the Cultural Validator — 100 lines that define behavior)
- Key principle: agents are PERSONAS, not separate programs. Same AI, different hats.

**Build Session: Your Agent Roster (25 min)**
- Participants design 3-5 agents for their own organization
- Template provided:
```markdown
## Agent: [Name]
**Scope:** [what this agent handles]
**Intent signals:** [keywords that route to this agent]
**Voice:** [how this agent communicates]
**Calibration:** conservative / balanced / aggressive
**Files to read:** [which state files matter to this agent]
**Files to write:** [which state files this agent updates]
```
- Walk the room. Help people name their agents. The naming matters — it makes the agent feel real.

**Check-in (5 min)**
- 2-3 participants share their agent rosters. Group feedback.

---

#### HOUR 2: Build Your State Layer (60 min)

**Intro: The State IS the Institution (5 min)**
- Show how Spark's state files work: every agent reads and writes to the same files
- "If your AI forgets everything between sessions, it's not a colleague — it's a stranger you brief every morning."

**Skill-Building: State File Design (15 min)**
- Walk through each RI state file and what it does:
  - spark-state.md → "The map of everything in motion"
  - portfolio.md → "Every project, its status, its health"
  - last-session.md → "15 lines that give you a running start"
  - decision-journal.md → "Why we chose what we chose"
- Show the hot/cold split: 80 lines of live state, archives for history
- Show the memory system: feedback, preferences, project context

**Build Session: Your State Files (30 min)**
- Participants create their own state files using templates:
  1. `[org]-state.md` — Quick status, active projects, priorities
  2. `portfolio.md` — Their projects/programs with status
  3. `last-session.md` — Template for session summaries
  4. `CLAUDE.md` — Project instructions for Claude Code
- They populate with REAL data from their own organization
- Walk the room. The portfolio is the hardest — most people have never written down all their projects in one place.

**Build Session: Your Memory Layer (10 min)**
- Create MEMORY.md with 3-5 initial memories:
  - One user preference ("I prefer direct communication, no corporate speak")
  - One project context ("We're applying for X grant by Y deadline")
  - One feedback memory ("Don't suggest Z, we tried it and it failed")

---

#### HOUR 3: Connect and Operate (70 min)

**Skill-Building: Gmail MCP Integration (15 min)**
- Live demo: connect Gmail MCP to Claude Code
- Show: search email, read a thread, create a draft
- Key principle: "Drafts only. Never sends. The human reviews everything."
- Participants connect their own Gmail (optional — can do this after the workshop)

**Skill-Building: The Session Protocol (10 min)**
- Walk through RI's session close checklist:
  - Update state files that changed
  - Draft morning email
  - Log decisions in the journal
  - Check for contradictions
- "The protocol is the discipline. Without it, the system drifts."

**Build Session: Your First Spark Session (25 min)**
- Participants open Claude Code (or Claude.ai)
- Load their CLAUDE.md, state files, and agent roster
- Run a test prompt: "What's the status of my projects?"
- The AI reads their state files and responds in the voice of their agent
- Then: "Draft an email to [someone] about [project]"
- The AI drafts from context. The participant sees it work.
- THIS IS THE MOMENT. When the AI reads their own data and responds with intelligence about THEIR organization, it clicks.

**Reality Check: The Stack You Don't Own (10 min)**
- The truth participants need before they leave the room. Every connector they wired up is a permission a third party can revoke.
- The math: 14 connectors × 95% reliability = 49% daily success rate. Five = 77%. Three = 86%. Compounding failure is the actual ceiling on agentic AI for non-power users.
- The three responses:
  1. **Reduce** — pick ≤3 load-bearing connectors per workflow. For Spark that's Gmail + file store + newsletter platform. Everything else is opportunistic.
  2. **Localize** — OS keychain over cloud OAuth wherever possible.
  3. **Sovereign** — pick tools the org actually owns. Listmonk over Mailchimp. Matrix over Slack. CryptPad over Google Docs.
- The political read: "Every connector is a permission someone else can revoke. Agentic AI is only as autonomous as the stack underneath it. Other workshops are selling the magic. We're selling the discipline."
- Bridge: "If running this stack alone feels heavy — that's correct. RI runs a managed ops tier. Talk to us after."
- **Facilitator: don't soften this module.** If a connector is broken in your own setup right now, show the live failure. The honest disclosure is what builds trust the other AI workshops can't buy.

**Reflection + Close (10 min)**
- "What surprised you?"
- "What's the first thing you'll use this for tomorrow?"
- "What's the agent you need that you didn't design today?"
- Share: workshop template repo link, this curriculum, RI's Spark architecture as reference
- "You just built the skeleton. The muscle grows every session you use it."

---

## FACILITATOR NOTES

### Timing Adjustments
- **For 1-hour keynote only:** Slides 1-26 as written. No build time.
- **For 90-minute keynote:** Add live demo after Slide 18 — actually show Spark working in Claude Code (search email, read state, draft response).
- **For 3-hour workshop:** Full build session. Can extend to 4 hours if participants want more Gmail integration time.
- **For half-day seminar (4-5 hours):** Add a fourth hour: "Advanced Spark" — cross-project intelligence, contradiction detection, confidence scoring. Participants implement one advanced feature in their own system.
- **For full-day intensive (6-8 hours):** Morning = keynote + workshop. Afternoon = advanced features + each participant presents their system to the group + feedback round.

### Common Questions
- **"Can I use GPT/Gemini instead of Claude?"** Yes, the pattern works with any LLM that has tool use. Claude Code is recommended because MCP integrations (Gmail, Calendar, Drive) are built-in.
- **"Does this work for a team, not just a solo founder?"** Yes — each team member can have their own Spark instance that shares state files via git. Federated agents with shared institutional memory.
- **"What if I'm not technical?"** The keynote requires nothing. The workshop requires basic comfort with a text editor and terminal. No coding.
- **"Is this the same as using ChatGPT?"** No. ChatGPT forgets everything between conversations. Spark has persistent state files, memory across sessions, multiple agent personas, and tool integrations. It's the difference between texting a stranger and having a COO.
- **"Will my workflow break?"** Yes, regularly. Connectors rotate tokens, scopes drift, vendors change policy. Module 3.4 (Reality Check) walks through why and the three responses: reduce connectors, localize credentials, prefer sovereign tools your org owns. Plan for breakage; don't be surprised by it.

### What Participants Leave With
1. A working CLAUDE.md with their org's instructions
2. 3-5 agent definitions tailored to their organization
3. State files populated with their real data
4. A memory layer with initial entries
5. A session protocol template
6. (Optional) Gmail MCP connected
7. The workshop template repo for reference
8. The confidence that this is buildable in a weekend

---

## WORKSHOP TEMPLATE REPO

Create a public GitHub repo: `radical-imagination/spark-workshop-template`

Contents:
```
spark-workshop-template/
├── README.md                    # Setup instructions
├── CLAUDE.md                    # Template project instructions
├── state/
│   ├── org-state.md             # Template: priorities, projects, status
│   ├── portfolio.md             # Template: project listing
│   ├── last-session.md          # Template: session summary
│   ├── decision-journal.md      # Template: decision logging
│   └── roster.md                # Template: people and roles
├── agents/
│   ├── example-router.md        # How to route between agents
│   ├── example-grant-writer.md  # Sample agent: grant strategy
│   ├── example-content.md       # Sample agent: content/social
│   └── example-validator.md     # Sample agent: review/QA
├── memory/
│   ├── MEMORY.md                # Memory index template
│   └── example-feedback.md      # Sample memory entry
└── protocol/
    ├── session-start.md         # What to do at session start
    └── session-close.md         # What to do at session end
```

---

## REVENUE MODEL

| Format | Duration | Price | Audience |
|--------|----------|-------|----------|
| **Keynote** | 60 min | $2,500-5,000 speaking fee | Conferences, meetups, corporate events |
| **Workshop** | 3 hours | $150/person (cap 25) = $3,750 | Founders, nonprofit leaders, studios |
| **Half-day seminar** | 4-5 hours | $250/person (cap 20) = $5,000 | Technical educators, operations teams |
| **Full-day intensive** | 6-8 hours | $500/person (cap 15) = $7,500 | Studios, labs, organizations ready to implement |
| **Custom org build** | 2 days on-site | $10,000-15,000 | Enterprise: RI builds their Spark for them |

**First workshop:** Free at CUNY PIT or a partner venue. Build the case study. Get testimonials. Then price it.

---

## PORTFOLIO ENTRY

### Give Your Org a Spark: Building a Chief Agentic Officer
- **Topic:** Multi-agent AI system design for organizational operations
- **Builders:** Mike Spade
- **Tech:** Claude Code, Gmail MCP, Google Calendar MCP, markdown state files, git
- **Status:** curriculum complete
- **Validation:** N/A (technology curriculum, not cultural heritage content)
- **Delivery modes:** in-person facilitated, virtual synchronous
- **Date completed:** 2026-04-06
- **Formats:** 60-min keynote, 3-hour workshop, half-day seminar, full-day intensive
