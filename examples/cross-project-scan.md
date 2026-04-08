# Example: Cross-Project Intelligence Scan

> This is a real (lightly edited) output from Spark's Cross-Project Intelligence system. It shows how the CAO scans the full portfolio to find reusable components, shared assets, relationship bridges, methodology transfers, and strategic timing connections.

---

# Cross-Project Intelligence Scan

**Date:** 2026-04-06
**Scan type:** First comprehensive portfolio-wide scan
**Agent:** Spark CAO
**Projects scanned:** 17+ across VR, AR, AI, data visualization, curriculum, and infrastructure
**Method:** Code grep, file glob, and state file cross-reference

---

## Detection Pattern 1: Reusable Components

### Connection 1: Parallax Image Component — built for one VR project, needed by another

```
CROSS-PROJECT CONNECTION:
Project A --> Project B
What: A fully featured image plane component with parallax depth, fade-in animation,
      gold borders, multiple crop modes, drift, pulse, desaturate, and tint shift.
      Currently ONLY exists in one project. A second project uses flat image planes
      with none of these effects.
Action: Extract into a shared component package. Apply to second project for
        instant visual upgrade.
Priority: next session (after first project ships)
Evidence: [exact file paths in both projects, grep confirming 0 hits in target project]
```

### Connection 2: Post-Processing Mood System — portable to any VR room

```
CROSS-PROJECT CONNECTION:
Project A --> Project B
What: A mood system providing 6 scene-based post-processing configurations
      (warm-amber, cold-blue, fire, void, dawn, dust) using bloom, hue,
      saturation, brightness, contrast, vignette, and noise. A second project
      has 3 distinct rooms with NO mood system.
Action: Port mood system. Room 1 = warm-amber, Room 2 = dawn, Room 3 = intimate.
Priority: next session
Evidence: [file paths, grep confirming no post-processing in target project]
```

### Connection 3: Service Worker Pattern — exists in 2 projects, missing from 2 that need it

```
CROSS-PROJECT CONNECTION:
Projects A + B --> Projects C + D
What: Two projects have service workers for offline caching. Two OTHER projects
      (both launching at live venues) have NO service worker -- meaning they break
      completely offline. Both venues have spotty WiFi.
Action: Add service worker to both venue projects before launch dates.
Priority: NOW (launch events are 74 and 89 days away)
Evidence: [file paths showing sw.js exists in A/B, grep confirming absence in C/D]
```

---

## Detection Pattern 2: Shared Assets

### Connection 4: Font files duplicated across 4 projects — 8.6MB wasted

```
CROSS-PROJECT CONNECTION:
Project A <--> B <--> C <--> D
What: The same font directory (4.3MB, all weights/styles) is duplicated identically
      in 2 projects. A third has a curated subset. A fourth references the font in
      CSS but the files DON'T ACTUALLY EXIST in its directory.
Action: Create a single shared /fonts/ directory. Symlink or copy at build time.
        Fix the project with missing font files.
Priority: next session
Evidence: [du -sh showing identical sizes, file paths for all 4 locations]
```

---

## Detection Pattern 3: Relationship Bridges

### Connection 5: One scholar bridges 3 archive projects

```
CROSS-PROJECT CONNECTION:
Project A / Project B --> Project C --> Project D
What: A scholar at UMass Amherst (archaeology, Black feminist frameworks) has
      done work relevant to ALL THREE archive projects — her archaeological
      research connects to one, her feminist frameworks to another, and her
      academic credibility spans the full intellectual canon.
Action: When reaching out, present the FULL portfolio vision — not just one project.
        She is a multi-project advisor candidate, not a single-project consultant.
Priority: NOW (outreach emails scheduled for this month)
```

### Connection 6: One faculty member bridges 3 projects AND a grant

```
CROSS-PROJECT CONNECTION:
Project A --> Project B --> Grant proposal
What: A faculty member (10-year relationship) is listed as potential PI for a
      federal grant. Her lab could host BOTH data literacy workshops AND VR demos.
      A single partnership that serves two projects and one grant application.
Action: Frame the grant proposal to include BOTH projects as exemplars.
Priority: parked (post-launch)
```

---

## Detection Pattern 4: Methodology Transfer

### Connection 7: Data contradiction tracking → cultural source conflict resolution

```
CROSS-PROJECT CONNECTION:
Data Transparency Project --> Cultural Heritage Methodology
What: A data dashboard has a contradiction.js component that tracks when multiple
      government sources disagree about the same fact. This is exactly the pattern
      needed for cultural archive source conflict resolution — when two historical
      sources disagree, surface both and let the user see the tension.
Action: Port the contradiction pattern from the data project into the cultural
        archive framework.
Priority: next session
```

---

## Scan Summary

**19 connections found** across 5 detection patterns:
- 6 reusable components (code that works in one project and is needed in another)
- 3 shared assets (files duplicated or missing across projects)
- 4 relationship bridges (people who connect multiple projects)
- 3 methodology transfers (approaches from one domain applicable to another)
- 3 strategic timing connections (events where multiple projects converge)

**Immediate priority (NOW):** 3 connections
**Next session:** 8 connections
**Someday:** 8 connections

---

## What This Example Shows

Cross-Project Intelligence is Spark's multiplier. A 10-person team discovers these connections in weekly standups. Spark found 19 in one scan by:

- **Grepping across all project directories** for shared component names, packages, and patterns
- **Comparing file sizes** to detect duplicated assets
- **Cross-referencing the roster** to find people who bridge multiple projects
- **Reading state files** to identify deadline convergences and strategic timing

Every connection includes:
- **Exact file paths** (not vague references — the actual files)
- **Evidence** (grep results, du -sh output, line numbers)
- **Priority** (NOW / next session / someday)
- **Action items** (specific enough to execute without further research)

The format (`CROSS-PROJECT CONNECTION` blocks) is standardized so connections can be tracked, acted on, and marked resolved.
