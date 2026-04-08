# Addendum: Case Study — Du Bois Does Data

> One project traced through all 8 agents.

This case study follows the Du Bois Living Archive — a conversational RAG system built on W.E.B. Du Bois's scholarly works — from concept through validation. It shows how a single project moves through Spark's agent system, with each agent contributing its domain expertise against the same shared state.

---

## The Project

**Du Bois Living Archive** — A citation-backed Q&A system grounded in 27 of Du Bois's works (1896-1920). Ask a question about Du Bois's sociology, philosophy, or activism, and get an evidence-based answer with source passages from the original texts. 11 works from Project Gutenberg + 16 Atlanta University Studies from Internet Archive.

**Tech:** RAG (Supabase + pgvector + Google AI embeddings + Claude Sonnet), React + Vite frontend, Vercel Edge Functions.

---

## Agent Contributions

### Cultural Archivist — Source Registry

The Archivist built the provenance foundation:
- Cataloged all 27 works with publication dates, source URLs, and trust levels
- Classified sources: Project Gutenberg texts (primary, high trust) vs. Internet Archive scans (primary, variable OCR quality)
- Created `archives/dubois/sources.md` — the source registry that every other agent references
- Identified 16 Atlanta University Studies that had never been digitized into a conversational system before
- Flagged OCR quality issues in Internet Archive scans — some chapters were too noisy to ingest

**Output:** `archives/dubois/sources.md`, `archives/dubois/ingestion-plan.md`

### Cultural Validator — Integrity Review

The Validator reviewed the archive and found:
- **MAJOR:** OCR audit needed for Internet Archive works — corrupted text could put wrong words in Du Bois's mouth
- **MAJOR:** Community consultation required before public release — the Du Bois Foundation in Ghana, living scholars, and HBCU Du Bois programs should review
- **MINOR:** Corpus intentionally excludes *The Crisis* magazine chapters with heavy OCR noise — document the exclusion rationale so it's not mistaken for editorial choice
- Status: **FLAGGED** (not blocked — the issues are addressable, but the archive cannot go to unrestricted public release until cleared)

**Output:** Entry in `validation-log.md`, `archives/dubois/validation-status.md`

### Money Agent — Funding Strategy

The Money Agent identified funding pathways:
- **NEH Humanities in Place** — Du Bois's Atlanta University work is place-based scholarship. Strong fit.
- **Mellon Foundation** — Humanities + digital innovation. Mapped the pathway in `grants/mellon-strategy.md`.
- **Spencer Foundation** ($50K) — Racial equity in education research. Du Bois's pedagogical works qualify. Deadline identified, calendar event created.
- **Fractured Atlas** — Du Bois Does Data is the fiscal sponsorship vehicle (501(c)(3)). All cultural heritage grants route through this arm.
- Flagged: NEH requires an institutional PI. CUNY partnership confirmed for co-sponsorship.

**Output:** Entries in `grants/deadline-research.md`, `grants/mellon-strategy.md`

### Curriculum Architect — Learning Experience

The Architect designed workshop formats:
- 60-minute data literacy session using Du Bois's 1900 Paris Exposition plates as primary sources
- Students analyze original hand-drawn charts, then query the Living Archive to explore Du Bois's methodology
- Mapped to CSTA and data literacy standards
- Flagged by Validator: must include colonial context of the 1900 Paris Exposition (it featured human zoos alongside Du Bois's counter-narrative)

**Output:** Curriculum in `curricula/`, lesson structure, facilitator guide

### Technical Mentor — Build Guidance

The Mentor guided the RAG pipeline build:
- Chunk size: 800 tokens, overlap 200 (validated across Du Bois corpus)
- Gemini embedding batch size: 50, 2-second sleep between batches (free tier rate limits)
- Dedup before corpus upserts using content hash
- `.slice(0, topK)` on vector results — never trust pgvector result counts
- Crisis magazine chapters with heavy OCR: stored as `null` rather than ingesting garbage

**Output:** Build constraints documented in CLAUDE.md, pipeline code

### Collective Manager — Portfolio Entry

The Manager maintained the project record:
- Created the portfolio entry with status, tech stack, LOC, validation state
- Tracked the project through status changes: concept → draft → flagged
- Documented exhibition history: debuted at True Zion Gospel Temple (Feb 14, 2026), presented at Oculus at WTC (Mar 27, 2026)
- Updated stats: project contributes to the portfolio's 154K+ LOC total

**Output:** Entry in `portfolio.md`, stats in `spark-state.md`

### Impact & Engagement — Visibility

Impact tracked and amplified:
- Documented the True Zion debut: children as young as seven experiencing the archive in a church setting
- Documented the CUNY PIT invitation: first institutional validation, led to Juneteenth invitation
- Queued content calendar entries for the Du Bois archive launch
- Drafted newsletter content for Beehiiv

**Output:** Entries in `activity-log.md`, content calendar

### Commercial Strategist — Revenue Assessment

The Strategist evaluated commercial viability:
- Du Bois archive is **Cultural Heritage arm** — grant-funded, not revenue-generating directly
- However: the conversational RAG system is white-label-able. Museums, universities, and libraries could license the engine for their own archives.
- This positions the cultural work as R&D for the Commercial arm
- Alignment score: 9/10 (cultural integrity preserved, commercial potential through licensing, not through the archive itself)

**Output:** Assessment in commercial evaluation framework

---

## What the Case Study Shows

1. **No agent works alone.** The Archivist built sources. The Validator checked them. The Mentor built the pipeline. The Curriculum Architect designed learning. The Money Agent found funding. Each reads the same state files, each writes to them.

2. **The Validator catches what builders miss.** OCR corruption putting wrong words in Du Bois's mouth. Colonial context of the 1900 Paris Exposition. These are the findings that prevent shipping something harmful.

3. **The state files tell the whole story.** Portfolio entry, validation log, activity log, source registry, decision journal — any of Spark's agents (or a human) can reconstruct the full history of this project from the files alone.

4. **Cultural and commercial are separated but connected.** The archive is grant-funded. The technology behind it is licensable. The Commercial Strategist sees both without compromising either.

5. **Flagged is not failed.** The Du Bois archive is flagged — community consultation and OCR audit needed. That's the system working. The archive will be validated when the community says it's ready, not when the AI says it's done.
