# Prompt Architecture — The 29 Asset Slots

The Learner Pack has a fixed taxonomy of 29 prompt slots across 5 asset types. Each slot has a structural pattern (the "shape" of the output) and specific grounding guidance.

## Composition Pattern

Each rendered prompt = `core + lens_suffix + format_outro`

- **`core`** — the topic-specific scaffold. This is where grounding happens. Extract actual constructs, actors, and numbers from the source material.
- **`lens_suffix`** — the audience-specific framing (see `audience-lenses.md`)
- **`format_outro`** — the asset-type-specific voice + output directive (see `brand-voices.md`)

Keep each `core` to 2-4 sentences. Compose short — NotebookLM performs better with focused prompts than with long ones.

---

## Infographics (10)

Image briefs that the user will paste into Napkin, Ideogram, or Midjourney. Output is a text prompt, not an essay.

### IG-01: Side-by-Side Comparison
**Pattern:** Two-column split-panel comparing two major entities, frameworks, or states from the source.
**Grounding:** Name both entities explicitly. List the 5-7 most operationally consequential parameters to compare.

### IG-02: Hub-and-Spoke Network
**Pattern:** Central concept with 6-10 connected spokes.
**Grounding:** Name the hub. Enumerate the actual spoke entities (stakeholders, components, dependencies) from the source. Specify the relationship/flow labels.

### IG-03: Timeline / Evolution
**Pattern:** Horizontal timeline, 5-8 nodes.
**Grounding:** Extract the actual milestone dates and events from the source. Each node: date + title + one-line significance.

### IG-04: Step-by-Step Process
**Pattern:** Vertical pipeline or waterfall, 4-7 steps.
**Grounding:** Name the specific process (e.g., target price construction, reconciliation workflow, clinical pathway). Specify the inputs, intermediate steps, and output.

### IG-05: Decision Tree / Eligibility Flow
**Pattern:** Branching logic with terminal outcomes.
**Grounding:** State the entry question. Enumerate the actual branching criteria from the source. Label terminal nodes (IN / OUT / exception categories).

### IG-06: Anatomy Breakdown
**Pattern:** Decompose one complex entity into its components.
**Grounding:** Name the entity. Enumerate its components, what's included vs. excluded, and any boundary conditions (outlier caps, cancellation triggers).

### IG-07: Tiered Hierarchy
**Pattern:** 3-5 stacked tiers multiplying into an outcome.
**Grounding:** Name the framework. Enumerate each tier's actual members/variables. Show how tiers combine.

### IG-08: Metrics Dashboard
**Pattern:** 6-10 stat cards with numbers, labels, and what they trigger.
**Grounding:** Extract the actual numerical parameters from the source — percentages, thresholds, caps, volumes, dollar amounts.

### IG-09: Three-Panel Card Set
**Pattern:** Three parallel items with parallel structure.
**Grounding:** Identify three structurally parallel entities in the source (three waivers, three pathways, three programs, three stakeholder groups). Each card: title + 3-4 lines of specific detail + tags.

### IG-10: Risk / Equity Bars
**Pattern:** Tier-based spectrum bars with qualifier lists.
**Grounding:** Identify a tiered protection, risk corridor, or qualification spectrum. State the actual percentages/thresholds. List who qualifies for each tier. Surface the equity question the design raises.

---

## Slide Decks (5)

Slide-by-slide outlines. Each slide: title + 3-5 bullets + one-line speaker note.

### SD-01: Executive Summary Deck (5–7 slides)
**Audience:** C-suite, board.
**Arc:** What this is → who it affects → key parameters → financial implications → risks → actions → timeline.

### SD-02: Teaching Deck (10–12 slides)
**Audience:** Grand rounds, CME, internal education.
**Arc:** Learning objectives → background → core concepts → worked example → implications → take-home points → references + discussion questions.

### SD-03: Conference Talk Deck (15–20 slides)
**Audience:** Peers at AAOS, AOA, Health Affairs.
**Arc:** Hook → background → design → evidence → data → implications → open questions → call to action. Assume 20 min + 5 min Q&A.

### SD-04: Strategic / Investor Deck (8–10 slides)
**Audience:** Business stakeholders, investors.
**Arc:** Market shift → why now → winners/losers → business implication → build/buy/partner → action framework → timeline. Peer-to-peer strategic tone, no sales energy.

### SD-05: Operational Playbook Deck (8–10 slides)
**Audience:** Service line leaders, operators.
**Arc:** What changed → what operators must know → workflow implications → metrics to track → roles → risks/mitigations → 30/60/90-day actions.

---

## Audio Overviews (5)

NotebookLM's native Audio Overview ("podcast") feature. The prompt configures tone, length, and focus.

### AU-01: Rapid Brief (5–7 min)
For the commute or between meetings. 3-4 most consequential takeaways + action implication.

### AU-02: Standard Overview (12–15 min)
Default format. Structure: what it is → who it affects → core mechanics → key parameters → implications → open questions.

### AU-03: Deep-Dive Expert Conversation (25–30 min)
For technical/peer audiences. Methodology, design choices, edge cases, equity implications, counterarguments, unresolved calibration questions.

### AU-04: Debate / Two Perspectives (10–12 min)
Two voices: a proponent and a thoughtful skeptic. Each takes the strongest case on 3-4 contested design choices. End with synthesis.

### AU-05: Case Study / Narrative (15–20 min)
Story-driven. One concrete scenario (a specific hospital, patient pathway, deployment, service line) walked through end-to-end.

---

## Video Storyboards (4)

Scene-by-scene text storyboards for Veo3, Runway, or Claude's video skills. Each scene: visual description + narration + any on-screen text.

### VD-01: Short Social Explainer (60–90 sec)
6-8 scenes. LinkedIn/Twitter vertical. Hook with operational stakes; end with "what to watch next."

### VD-02: Mid-Length Explainer (3–5 min)
12-18 scenes. YouTube/LinkedIn long-form. Talking-head cut with b-roll, charts, animation overlays.

### VD-03: Scenario / Story Video (2–3 min)
8-12 scenes. Built around one concrete scenario that humanizes the material.

### VD-04: Demo / Walk-Through (5–8 min)
20-28 scenes. Step-by-step walk-through with one worked example and a summary of viewer decisions.

---

## Knowledge Tests (5)

NotebookLM's native Flashcards and Quiz features. The five test types progress through Bloom's taxonomy: recall → application → diagnosis → synthesis → judgment. Use these to expose the gap between "I think I know this" and "I actually know this."

### QZ-01: Terminology Flashcards
**Pattern:** Front-of-card term, back-of-card precise definition, plus one example or implication line.
**Grounding:** Identify 12-15 vocabulary terms from the source that block comprehension. Prioritize terms learners commonly conflate (e.g., for CJR-X: gainsharing vs. alignment, MS-DRG vs. HCPCS triggers, CJR vs. CJR-X parameters).
**NotebookLM target:** Flashcards.

### QZ-02: Scenario Decision Flashcards
**Pattern:** Front-of-card concrete situation in 2-3 sentences, back-of-card answer + one-line citation.
**Grounding:** Generate 10-12 scenario cards drawn from real operational decisions the source enables (placement decisions, eligibility questions, cancellation triggers, concurrent-program participation, beneficiary incentives).
**NotebookLM target:** Flashcards.

### QZ-03: Common-Mistake Quiz
**Pattern:** Multiple choice with 4 options, one correct, plus one-paragraph explanation citing the rule.
**Grounding:** Generate 8-10 questions targeting common misconceptions about the topic. Each tempting wrong answer should reflect a real misread the source corrects (e.g., conflating CJR's 3% discount with CJR-X's 2%, missing TEAM overlap rules, assuming ASCs are included).
**NotebookLM target:** Quiz.

### QZ-04: Integration Quiz
**Pattern:** Multiple choice with 4 options, one correct, one-paragraph explanation showing how the concepts interconnect.
**Grounding:** Generate 8-10 questions that require combining 2-3 concepts from the source to answer correctly (e.g., target price + risk adjustment + reconciliation; quality scoring + discount factor + reconciliation eligibility; episode definition + concurrent ACO participation + savings retention).
**NotebookLM target:** Quiz.

### QZ-05: Tradeoff Quiz
**Pattern:** Multiple choice with 4 options, the answer that best matches the stated priority, plus one-paragraph explanation of all tradeoffs.
**Grounding:** Generate 6-8 questions presenting real strategic decisions where each option has valid pros and cons (post-acute network composition, beneficiary engagement allocation, gainsharing structure with PGP vs. ACO collaborators, telehealth waiver vs. in-person follow-up). The "correct" answer depends on stated priorities.
**NotebookLM target:** Quiz.

---

## Grounding Self-Check

Before you consider a `core` scaffold done, ask:

1. Does it name a specific entity, framework, number, or actor from the source?
2. Could I swap the topic name for a different topic and still have a coherent prompt? (If yes, it's under-grounded.)
3. Does it prioritize what's *operationally consequential*, not just what's *present*?
4. Does it avoid inventing details not supported by the source?

If any answer is "no," revise before moving on.
