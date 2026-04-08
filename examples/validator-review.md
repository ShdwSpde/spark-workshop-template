# Example: Cultural Validator Output — Integrity Review

> This is a real (lightly edited) output from Spark's Cultural Validator. It shows severity-tiered findings, a checklist structure, resolved/unresolved tracking, and the gating logic that prevents premature publication.

---

# Validation Status — Ida B. Wells Living Archive

**Item:** Ida B. Wells Living Archive (conversational RAG archive)
**Reviewed by:** Cultural Validator (AI)
**Date:** 2026-03-21 (re-review — OCR audit complete, portfolio expanded)
**Status:** flagged

---

## Checklist

### 1. Historical Accuracy

**PASSED.**

- 5 works documented in source registry, all by Ida B. Wells (Wells-Barnett after 1895). All correctly marked as primary sources.
- 4 works sourced from Project Gutenberg with standard proofreading — high-confidence text.
- 1 work audited for OCR quality: body text (lines 6–3131) is ~95% clean, usable for RAG. Header and back matter are garbled and should be stripped before chunking. This is NOT a null-quality text — the body is reliable for semantic retrieval.
- All works public domain (published before 1928).

**Note on corpus scope:** Wells's autobiography (published posthumously 1970) is not included. This is the correct decision — the 1970 publication date likely places it under copyright. The portfolio entry documents this as an intentional curatorial choice. The current corpus centers Wells's public anti-lynching work, which is where her impact as a journalist and statistician is most concentrated.

### 2. Representational Integrity

**PASSED.**

- Wells is represented as an investigative journalist and statistician — not a victim, not a symbol, but an agent who used data to dismantle narratives of justified violence. This is the right framing.
- The corpus spans 28 years of her public anti-lynching career (1892–1920), giving breadth to her evolving methods and arguments.
- The archive is described as enabling "citation-backed Q&A grounded in Wells's own words" — this is a tool for learning from Wells, not a tool that speaks for her.

### 3. Community Consent

**FLAGGED — COMMUNITY CONSULTATION REQUIRED. This is the gating item.**

This corpus documents lynching, mob violence, and racial terror against Black communities. Wells wrote these texts as acts of resistance — they are weapons against injustice, not academic curiosities. Building a public-facing RAG experience from this material requires consultation with communities connected to Wells's legacy.

**Why this matters:** A RAG system can surface graphic descriptions of lynching in response to conversational queries. Without thoughtful design, a user could receive detailed accounts of racial violence without adequate framing or contextual support.

**Recommended consultation contacts:**
1. **Ida B. Wells Society for Investigative Reporting** — professional organization carrying Wells's investigative legacy forward
2. **National Association of Black Journalists (NABJ)** — Wells was a pioneering Black journalist
3. **Wells-Barnett family descendants** — through the Ida B. Wells Foundation (Chicago)
4. **Equal Justice Initiative (EJI)** — operates the National Memorial for Peace and Justice. Deep expertise in responsible public presentation of anti-lynching history
5. **University of Chicago scholars** — holds relevant archival materials
6. **Elaine massacre community (Phillips County, AR)** — one text documents the 1919 Elaine massacre. The Elaine Legacy Center represents living community connection

**What consultation should cover:**
- Is a conversational RAG interface appropriate for this material?
- What content warnings, framing, or contextual scaffolding should accompany responses?
- Are there passages or topics that should be handled with special care?
- How should the system respond when users ask about graphic violence?

### 4. Source Citation

**PASSED.**

- All 5 works have documented origin, word count, trust level, date range, community connection, and OCR quality.
- Provenance gaps are honestly documented rather than fabricated.

### 5. Bias Scan

**PASSED.**

- Wells is centered as agent throughout — she investigated, she documented, she argued. Active voice, person-first.
- No romanticizing of the subject matter. The source registry explicitly calls out "graphic descriptions of racial violence."
- The term "anti-lynching" is used consistently rather than euphemistic alternatives.

---

## Previous Flags — Now Resolved

| Previous Flag | Status |
|---|---|
| Source provenance placeholder tags | **RESOLVED** — All 5 works fully documented |
| OCR needs audit | **RESOLVED** — Audited. Body text is ~95% clean. Header/footer stripped. |
| Portfolio entry minimal | **RESOLVED** — Now describes the archive fully and documents curatorial exclusions. |
| Copyright question on autobiography | **RESOLVED** — Documented as intentional curatorial decision. |

## Current Flags — Action Required

| Flag | Severity | Action |
|------|----------|--------|
| Community consultation | **High** — blocks public release | Reach out to Wells Society, NABJ, or descendants as starting point |
| Content safety design | **RESOLVED** — Three-layer system implemented: entry framing, contextual lead-ins before graphic passages, boundary query handling for sensitive material |
| Living community connections | **Medium** | Establish specific contact with Elaine Legacy Center for one specific text |

## Recommendation

**Status upgraded from `blocked` to `flagged`.** Provenance and OCR blocks are cleared. Content safety design is implemented. Community consultation is the only remaining gate — and it's the right gate.

The archive can continue in development. It cannot be made public until community consultation validates the approach.

---

## What This Example Shows

The Cultural Validator is calibrated **conservative** — false negatives preferred. It:
- **Uses a structured checklist** (5 categories, each with PASSED/FLAGGED status)
- **Tracks resolved vs. unresolved flags** (previous findings that are now cleared, current findings that remain)
- **Severity-tiers every finding** (High = blocks release, Medium = needs attention)
- **Names specific consultation contacts** (not "reach out to the community" but 6 named organizations with reasons)
- **Asks the hard questions** ("Is a conversational RAG interface appropriate for this material?")
- **Documents curatorial decisions** (why the autobiography was excluded, why that's correct)
- **Never rubber-stamps** — this is a re-review that upgraded from blocked to flagged. It still won't clear for public release without community consultation.

The Anti-Rubber-Stamp Rule is visible here: the Validator found issues on first review, tracked their resolution, and still maintains a gate. Status can only move to "validated" after human sign-off.
