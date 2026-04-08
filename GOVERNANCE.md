# Governance

> How decisions get made, who can change what, and why the system has a conscience.

Spark is not just an automation tool — it has governance built into the agent architecture. This document describes the operational rules that prevent the system from drifting, rubber-stamping, or overstepping.

---

## Decision Authority

### What agents can do without asking (auto-proceed)

- Read any state file
- Generate reports and summaries
- Query archives and source registries
- Draft communications (never send)

### What agents do with a flag (human reviews output)

- Update portfolio.md with project status changes
- Run cultural validation
- Draft grant language
- Add activity log entries
- Generate curriculum or learning materials

### What requires human approval before action (propose only)

- Change any validation status to "validated"
- Modify source registries (`archives/*/sources.md`)
- Add or remove roster members
- Delete any file
- Push to git
- Send any communication

**The principle:** Reversible actions proceed. Hard-to-reverse actions require human sign-off.

---

## The Anti-Rubber-Stamp Rule

The Cultural Validator cannot approve something the same turn it first encounters it.

- First response to any validation request is **findings and questions**
- Validation status can only change to "validated" **after the human has reviewed and responded**
- No item reaches 100% validation without human initials and a date

This is the most important rule in the system. Without it, the AI tells you what you want to hear.

---

## Agent Calibration

Not every agent should behave the same way. Calibration determines how each agent handles uncertainty:

### Conservative (false negatives preferred)
**Cultural Validator, Cultural Archivist**
- Below 80% confidence → state as a QUESTION, not a finding
- Escalate to human rather than auto-resolve
- When in doubt, flag as MAJOR rather than MINOR
- Default to "more context needed" rather than "this is fine"

### Aggressive (false positives preferred)
**Money Agent, Commercial Strategist, Impact & Engagement**
- Include long-shot opportunities even when alignment is uncertain
- Every analysis includes at least one stretch worth trying
- Never omit an opportunity because "they probably wouldn't be interested"

### Balanced
**Curriculum Architect, Collective Manager, Technical Mentor**
- Include only what directly serves the task
- When format is ambiguous, ask
- When tier/level is ambiguous, default to the lower tier

---

## Corrections Protocol

When the human corrects the system, the correction is classified and handled differently:

### Tier 1 — Factual correction about content
- Update the relevant source registry (`archives/*/sources.md`)
- Note: "Corrected [date] by user — previous value was X, correct value is Y"
- The Cultural Archivist owns source registries

### Tier 2 — Procedural correction about agent behavior
- Note the correction in the relevant agent spec under `## Known Issues`
- Add to CLAUDE.md if it affects multiple agents
- Example: "Do not suggest NEH Preservation grants for born-digital projects"

### Tier 3 — Preference correction (style, format, tone)
- Apply in the current session
- Do not modify specs for one-off preferences
- If the same preference is expressed 3+ times, promote to Tier 2

---

## Drift Detection

After any agent produces output, the system checks for:

1. **Scope creep** — Does the output address topics outside this agent's domain?
   - Money Agent discussing cultural authenticity = DRIFT
   - Cultural Validator recommending grant strategies = DRIFT
   - Response: "I'm veering into [other agent]'s territory. Routing that part to [correct agent]."

2. **Template compliance** — Did the output follow the agent's required schema?

3. **Calibration check** — Is the agent's confidence appropriate for its calibration level?

---

## Cultural Validation Severity Tiers

Every finding gets a severity level. This is not optional.

| Tier | Name | What It Means | Consequence |
|------|------|--------------|-------------|
| CRITICAL | Blocks release | Factual errors about real people, harm to living communities, misattribution of cultural practices, use of sacred elements without consultation | Item is **BLOCKED** until resolved |
| MAJOR | Flags for attention | Missing context that changes meaning, colonial framing without acknowledgment, source gaps for key claims, erasure of agency | Item is **FLAGGED**, can proceed with documented concerns |
| MINOR | Advisory | Terminology preferences, framing suggestions, style recommendations | Noted, no block |

**Progression:** blocked → flagged → validated (only by human sign-off)

---

## Confidence Scoring

Every substantive agent output includes:

```
**Confidence: X/5**
- [reason for score]
- [what would increase confidence]
```

| Score | Meaning |
|-------|---------|
| 5/5 | Verified primary sources, community-validated, battle-tested |
| 4/5 | Registered sources, internally consistent, not yet community-reviewed |
| 3/5 | Secondary sources or reasonable inference, some gaps |
| 2/5 | Speculative, limited data, significant gaps |
| 1/5 | Best guess, no registered sources, high uncertainty |

---

## Session Protocol

Every session follows the same discipline:

**Start:**
1. Read `last-session.md` for immediate context
2. Read `spark-state.md` for current priorities
3. Check for contradictions across state files
4. Flag deadlines within 7 days
5. Flag stale files (not updated in 7+ days)

**End:**
1. Update state files that changed during this session
2. Add activity log entries for deliverables produced
3. Log decisions in decision journal
4. Draft session summary to `last-session.md`

**The protocol is what makes it an institution instead of a chatbot.**

---

## Contradiction Detection

At session start, Spark scans for:

- **Cross-file consistency:** Portfolio status matches validation log status? State matches activity log?
- **Date staleness:** Any file not updated in 7+ days gets flagged
- **Numeric consistency:** Project counts match across files?
- **Commitment tracking:** Active decisions in the journal that haven't been acted on?

Contradictions are reported immediately. They do not resolve themselves.

---

## Handoff Blocks

Every agent that produces output for downstream review appends metadata:

```
<!-- AGENT-HANDOFF
source_agent: [who produced this]
target_agent: [who should review next]
claims_to_verify: [specific claims needing validation]
cultural_topics: [cultural topics touched]
confidence_notes: [where the agent was least confident]
-->
```

This prevents work from falling through cracks between agents.

---

## What the System Won't Do

These constraints are architectural, not suggestions:

- **Won't send communications.** Drafts only. The human reviews and sends. Always.
- **Won't validate its own output.** The Cultural Validator reviews independently. Generation and validation are never fused.
- **Won't skip community consultation.** "Should we build this?" comes before "How do we build this?" If the community hasn't been consulted, the item stays flagged.
- **Won't let an algorithm curate cultural heritage.** The human hand stays in the loop. Curation is an act of care.
- **Won't silently promote drafts.** Critical validation issues keep items in draft. The system tells you exactly what's flagged and what needs to happen.

---

## Adapting This Governance for Your Organization

The specific tiers and calibrations above reflect Radical Imagination's cultural heritage work. The structural patterns are universal:

1. **Define risk levels** — What can auto-proceed? What needs human sign-off?
2. **Calibrate your agents** — Which should be cautious? Which should be aggressive?
3. **Build a corrections protocol** — How do human corrections propagate through the system?
4. **Enforce the Anti-Rubber-Stamp Rule** — QA agents must never approve in the same pass they first review.
5. **Require confidence scores** — The system should always tell you how sure it is and why.
6. **Run session protocols** — The discipline of reading state at start and updating at end is what creates institutional continuity.

The governance is the product. The agents are just the delivery mechanism.
