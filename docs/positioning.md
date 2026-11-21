# Why Spark, and not Notion or Gas Town

> Spark is for small organizations that publish things that have to be right. It drafts, checks claims against sources, and keeps a record of what everything costs. A person who knows the material makes the final call. Below is what we can show so far, and what we can't yet.

Last updated 2026-11-20. Spark figures come from Radical Imagination's own logs and tests, kept in RI's private repo and available on request. Figures about other tools come from their own pages or from named write-ups, and are labelled.

---

## The landscape, November 2026

The tools now agree on the shape: give AI agents a shared, organized place to work, and turn repeated work into agents that run on their own. They differ on where that place lives, what the agents are for, and who checks them.

| | **Notion (Custom Agents)** | **Gas Town** | **Spark** |
|---|---|---|---|
| What it is | Team workspace with built-in AI agents | Open-source orchestrator that runs many coding agents in parallel under one coordinator | Operating system for an organization, in plain files, run by Claude Code |
| Built for | Teams doing knowledge work in Notion | Engineering teams with large coding backlogs | Small orgs where accuracy matters: archives, education, cultural work |
| Where the context lives | Notion's database, on Notion's servers | Your code repo | Your git repo, as plain text you can read without any tool |
| What it's for | Collaboration and access | Code throughput | Accurate, sourced work, and continuity between sessions |
| How agents are defined | Configured inside Notion | Roles in the orchestrator; works with Claude Code, Codex, Gemini and others | Markdown files a non-engineer can edit |
| Price | Business plan $20 per seat a month; agents run on Notion credits (notion.com/pricing; Notion help, "How AI credits work for Custom Agents") | Free, MIT license; you pay for the model accounts underneath | A Claude subscription. RI started on Pro ($20 a month) and moved to Max ($100) as use grew |
| Who checks the work | Permissions, version history, audit log (Enterprise) | Built-in roles that watch and merge agent output; you review the code | An independent reviewer agent, a pre-deploy check, and a person's sign-off |

---

## What we can show

Spark has to earn its place against a plain AI subscription, so we tested it against one.

**1. A controlled test against plain Claude.** Same model, hidden answer keys, a game card with 8 planted errors. Plain Claude caught 6.5 on average and found almost every factual error. Spark's reviewer caught 7 to 8 (7.83 after one round of fixes to the reviewer), with no false alarms in either. The difference was the organization's own house rules and its source registry: only Spark traced claims back to the archive's records. Plain Claude caught some web issues Spark missed (viewport, contrast, fonts); those are now a script.

**2. A sweep of live pages.** In one night, 20 independent Spark reviews of RI's live pages found 13 with critical errors that had shipped without review, including composite testimony presented as one survivor's, a reversed sale, and an unsourced "a million people" claim. Seven of the worst were re-checked by hand. All held.

**3. The cost of a review.** An independent fact-check costs about 30 cents at list price in the controlled test, and a dollar or two in everyday use on real pages. Every public page can get one.

**4. Output where Spark runs, and where it doesn't.** Across 15 repos run with Spark, lines of work added per active week rose about 2.6 times after Spark started. Across the same founder's 18 other repos, same months and same models, the figure was 0.91 times. Better models alone don't explain the gap. Two confounds remain: the founder's focus moved toward this work, and lines of work measure volume, not value. Commits per week did not rise.

**5. A record of what the work cost.** Every session is logged and priced at list: about $133 for a 3D exhibit draft and $155 for a five-session course. That lets an organization budget per deliverable and put compute in a grant.

### Spark does a lot. It doesn't do it all.

Spark drafts, checks every claim against its sources, and flags what it can't confirm. The final call on whether something is true belongs to a person who knows the material. Radical Imagination leads with the projects where a scholar partner can do that verification, because that pairing is what makes the work publishable. Spark makes the human's review faster and more complete; it doesn't replace it.

### What we haven't shown yet

- **Rules hold best when a check enforces them.** Of 19 corrections we could check, 6 held every time: two are backed by a test or code, four are narrow enough to search for. Judgment rules (voice, depth, copying references) came back within a median of 12 days. Each repeated correction is being turned into a check.
- **Nothing has reached "validated."** The reviewer blocks and flags; final sign-off is a person's, and none has been given yet.
- **The pre-deploy check is partial.** It stops a page that has no review or a blocking review. A page whose review only flagged problems can still ship with the founder's go.
- **No outside client yet.** The first client case study is in progress. Until then, every number here is one studio's.

---

## Spark and Notion

Notion's field guide, "A New Shape for Work," makes the argument Spark was built on: "Rent the intelligence. Own the context." The difference is where the context lives.

**Where Spark differs**
- **Plain files you hold.** Spark's context is text in git. If you stop paying anyone, every file still opens. Every change has an author and a date, and any two versions can be compared line by line.
- **A review step for accuracy.** Notion's controls are about access: permissions, history, audit logs. Spark adds an independent reviewer that checks claims against the organization's own sources, can't approve on its first look, and leaves a written record. For an archive or a classroom, a wrong caption is the main risk.
- **Cost per finished piece.** Notion meters agents in credits, with admin caps and budgets, and agents pause when a workspace runs out (Notion help). Spark logs list-price cost per deliverable, so an organization can see what a lesson or an exhibit draft cost.
- **Any model can read it.** Spark's files work with any model that can read text. Its connectors (mail, calendar, browser) are Claude Code features.

**Where Notion wins**
- **Team access.** Comments, mobile, permissions and a familiar editor for everyone. Spark's shared agents are partly cloud (scheduled briefings) and partly on one laptop (checks and skills), and opening it to a whole team takes setup.
- **Syncs and meetings.** Notion pulls in mail, calendars and meeting notes out of the box.

**Use both when** the team already lives in Notion. Spark can keep its records and its reviewer in git, and post summaries where people already read.

## Spark and Gas Town

Gas Town, Steve Yegge's open-source orchestrator, runs many coding agents in parallel under a coordinating agent, with roles that watch their work and merge it. It is built to finish a lot of code fast, and write-ups describe it as expensive to run.

**Where Spark differs**
- **What the output is.** Gas Town's output is code. Spark's output is often public and cultural, so an independent reviewer checks it against sources before a person signs off.
- **One focused agent.** Spark runs one agent at a time with short helper tasks, on a single subscription. It is not trying to maximize throughput.
- **Built for operators.** Running Spark means editing markdown files.

**Where Gas Town wins**
- **Throughput on a big engineering backlog.** If the job is hundreds of independent code changes, many parallel agents beat one careful one.

---

## When to use what

- **Notion** if your team needs a shared workspace first and accuracy checks are handled elsewhere.
- **Gas Town** (or its successor, Gas City) if you're an engineering team with a large, parallel coding backlog and the budget for it.
- **Spark** if you're a small organization that publishes things that have to be right, doesn't have an engineering team, and needs to know what its AI work costs.

## The honest limitation

Spark runs on Claude Code, so its connectors and scheduled agents depend on Anthropic. The state files, agent specs and protocols are plain text, and they stay readable without it.

---

## Sources

- Spark tests and audits (RI private repo, available on request): `specs/spark/2026-11-14-does-spark-help.md`, sections 1 to 7 (controlled test, live-page sweep, corrections audit, output against control repos), with fixtures in `evals/validator/`.
- Cost per piece and per review: `evals/cost_baseline.py` and the Spark A/B metrics in the same repo, as reported in the draft essay "The Price Is Right" (Archival Intelligence No. 1, unpublished).
- Notion: "A New Shape for Work," notion.com/a-new-shape-for-work, read 20 Nov 2026 (archived copy kept by RI); plan prices from notion.com/pricing, read 20 Nov 2026; credits, caps and the pause when credits run out from Notion's help page "How AI credits work for Custom Agents," notion.com/help/how-ai-credits-work-for-custom-agents.
- Gas Town: DoltHub, "A Day in Gas Town," dolthub.com/blog/2026-01-15-a-day-in-gas-town/, 15 Jan 2026; Tenzin Wangdhen, "Gas Town: The Good, The Bad, The Ugly," tenzinwangdhen.com/posts/gastown-good-bad-ugly/; Ry Walker's research notes, rywalker.com/research/gastown and rywalker.com/research/gas-city.
- Claude plans: claude.com/pricing (Pro $20, Max $100 a month), checked 19 Nov 2026; RI's own plan history per its founder.
