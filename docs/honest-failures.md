# Honest Failures

> What went wrong, what the system caught, and what it didn't.

Spark is powerful. It's not perfect. These are real failures from production use — the moments where the system broke, missed something, or produced output that needed human correction. They're here because the failures are as instructive as the successes.

---

## 1. The Wrong Portraits

**What happened:** Spark was tasked with sourcing archival portraits for a VR experience about a Black historical figure. It downloaded 2 portraits from the Library of Congress. Both were of white men.

**Why it happened:** The LOC search returned results by metadata proximity, not visual verification. The AI matched on names and dates but didn't verify the images showed the correct person.

**What caught it:** Human review. The founder opened the images and immediately saw the error.

**What the system didn't catch:** No agent flagged this. The Cultural Validator reviews framing and source provenance, not whether a JPEG actually depicts the right person. There was no visual verification step.

**What changed:** Visual QA is now a protocol. After any image sourcing, screenshots are taken and reviewed before images enter the build. The Technical Mentor offers: "Want me to take screenshots and check what's rendering?"

---

## 2. Box Geometry Humans

**What happened:** A VR scene required crowd silhouettes. The system generated crowd figures using box geometry with spheres for heads. The result was not recognizably human.

**Why it happened:** The build instruction said "silhouettes." The AI interpreted this as geometric primitives rather than human-shaped forms.

**What caught it:** Human review. Feedback: "bruh, can't tell those are humans."

**What changed:** The correction was logged as a Tier 2 procedural correction. Visual ambiguity in build instructions now triggers a clarification step: "When you say silhouettes, do you mean flat cutout shapes or 3D models?"

---

## 3. 81 Images Across 7 Scenes

**What happened:** An archival VR experience was built with 81 image planes distributed across 7 scenes. Each scene had 10-15 images. The result was visually overwhelming — too many images competing for attention, no focal point, no breathing room.

**Why it happened:** The AI was thorough. It found 81 relevant archival images and placed them all. More = better was the implicit assumption.

**What caught it:** Human review. "Some of these scenes are overwhelming. Thin to 3-4 per scene."

**What changed:** A curation principle was added: archival density must serve narrative pacing, not completeness. 3-4 hero images per scene, with the rest available in a gallery or supplementary view. The design thesis now includes: "Every element in a room earns its place. If removing it doesn't hurt the experience, it shouldn't be there."

---

## 4. The Missing Font Files

**What happened:** A VR project referenced a custom font in CSS (`fontFamily: "'VTC Du Bois', serif"`) but the actual font files weren't in the project's public directory. The font silently fell back to the system serif font. Nobody noticed for weeks.

**Why it happened:** The font was installed system-wide on the development machine, so it rendered correctly in local dev. But deployed builds (and any other machine) used the fallback.

**What caught it:** Cross-project intelligence scan. The scan found the font duplicated across 4 projects (8.6MB wasted) and discovered that one project referenced it without having the files.

**What changed:** Shared fonts are now a named asset class in the cross-project protocol. The scan also identified 8.6MB of duplicated font files to consolidate.

---

## 5. The Rubber-Stamp Risk

**What happened (hypothetically):** Before the Anti-Rubber-Stamp Rule was implemented, the Cultural Validator could review new content and approve it in the same pass. "Looks good" was a valid output.

**Why it's dangerous:** An AI reviewer that approves everything it first encounters provides no actual quality gate. It becomes a checkbox, not a conscience.

**What changed:** The Anti-Rubber-Stamp Rule: the Cultural Validator cannot approve something the same turn it first encounters it. First response is always findings and questions. Validation status can only change to "validated" after the human has reviewed findings and responded. No exceptions.

This is the most important governance rule in the system.

---

## 6. Grant Recommendations for Ineligible Programs

**What happened:** The Money Agent recommended an NEH Preservation grant for a born-digital project. NEH Preservation grants are for physical preservation of material artifacts — not for digital-first work.

**Why it happened:** The keyword match between "cultural heritage preservation" and "NEH Preservation" was strong. The AI didn't distinguish between physical and digital preservation in the program's eligibility criteria.

**What caught it:** Human review. The founder had read the NEH guidelines and knew the program was physical-only.

**What changed:** Logged as a Tier 2 correction in the Money Agent spec under Known Issues: "Do not suggest NEH Preservation grants for born-digital projects — those are for physical preservation only." The correction persists across all future sessions.

---

## What the Failures Teach

1. **AI doesn't have eyes.** Visual verification requires screenshots and human review. No amount of metadata matching replaces looking at the image.

2. **Thoroughness is not curation.** More images, more data, more connections — the AI's instinct is to include everything. Humans curate. The system needs to be told when less is more.

3. **Silent fallbacks hide errors.** CSS font fallbacks, default values, graceful degradation — they're good engineering but they mask problems that need human attention.

4. **Governance can't be optional.** The Anti-Rubber-Stamp Rule exists because without it, the system tells you what you want to hear. The correction protocol exists because without it, the same mistake happens twice.

5. **Human oversight is not a limitation — it's the design.** Every failure on this list was caught by a human, not by the system. The system's job is to make human review efficient, not to replace it.
