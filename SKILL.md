---
name: notebooklm-learner-pack
description: Generate branded, topic-specific HTML NotebookLM Learner Packs — 29 copy-paste prompt cards (10 infographics + 5 slide decks + 5 audio overviews + 4 video storyboards + 5 knowledge tests) with a sticky dual-filter UI that toggles between six audience lenses (ELI5, Newbie, Practitioner, Operator, Finance, Deep Dive) and five asset types. Triggers on "NotebookLM learner pack," "learner site," "learner prompts," "explainer prompt pack," "build a prompt library for [topic]," "make a NotebookLM pack on [topic] in [brand] voice," or the workflow of ingesting source material into NotebookLM and wanting a reusable prompt library to generate explainer assets and tests. Also triggers when a new standard drops, a meeting just finished, or an abstract book arrives. Supports any configured brand voice; custom brands can be defined at pack-generation time. Use liberally for turning ingested source material into on-brand explainer asset and knowledge-testing pipelines.
---

# NotebookLM Learner Pack

## What This Skill Produces

A single self-contained HTML file — the "Learner Pack" — that serves as a copy-paste prompt library tailored to a specific **topic** and rendered in a specific **brand voice**. The user runs prompts from the Pack against their own NotebookLM notebook (which they populate separately with source documents) to generate explainer assets.

Each Pack contains exactly **29 prompt cards** across five asset types:

- **10 Infographics** — text briefs that feed Napkin, Ideogram, or Midjourney
- **5 Slide Decks** — slide-by-slide outlines for the PPTX skill or Gamma
- **5 Audio Overviews** — NotebookLM native podcast-format prompts
- **4 Video Storyboards** — scene-by-scene briefs for Veo3 or Runway
- **5 Knowledge Tests** — NotebookLM Flashcards and Quiz prompts spanning recall, application, analysis, synthesis, and judgment

Every prompt has **6 audience-lens variants** that the user toggles live in the browser: ELI5, Newbie, Practitioner, Operator (default), Finance, Deep Dive.

## When To Use

Trigger on requests like:
- "Make a NotebookLM Learner Pack on [topic]"
- "Build a learner site / prompt library for [topic] in [brand] voice"
- "A new rule dropped, I'm ingesting it into NotebookLM — give me the prompt pack"
- "I just finished a meeting with [abstract book / transcript / policy PDFs], make me a learner pack"
- "Generate explainer prompts for NotebookLM on [topic]"

If the user provides source material directly, use it to ground the prompts. If they only provide a topic or context, proceed from what you know about that topic and prioritize grounded, source-referential scaffolding.

## Workflow

### 1. Capture Inputs

Before generating, confirm you have:
- **Topic** (required) — what the Pack is about
- **Brand voice** (required) — The Analyst, The Scholar, Modern Enterprise, or custom. Brand determines voice card, colors, typography, and the imperative voice woven into every prompt.
- **Source context** (optional but strongly preferred) — any documents, policy summaries, meeting notes, or analyses the user provides. Use these to make prompts **grounded and specific**, not generic.
- **Audience priorities** (optional) — if the user flags a primary audience (e.g., "this is for practitioners"), default the lens toggle to that audience.

If any of these are ambiguous, ask one focused question before proceeding — don't over-interview.

### 2. Draft the 24 Prompts (Grounding Matters Most)

This is the most important step. The prompts must be **validated and grounded in the source material** rather than generic. A prompt that says "compare two entities from the source" is weaker than "compare [Framework A] and [Framework B] side-by-side — 5-7 operationally consequential parameters each."

**Grounding rules:**

- When source material is provided, extract the *actual* constructs, actors, numbers, and thresholds. Weave them into the prompt scaffold. The reader should be able to tell this Pack was built *for this topic*, not a generic template filled with the topic's name.
- When source material isn't provided, use validated knowledge of the topic — still name the specific constructs, actors, or frameworks you expect the source material to contain. Do not hallucinate details.
- Every prompt should feel purpose-built for the topic. If a prompt could be dropped into a Pack for a different topic with only a search-and-replace, it is under-grounded.

**The 29 asset slots (fixed taxonomy):** See `references/prompt-architecture.md` for the complete list of asset slots, their structural scaffolds, and grounding guidance. Knowledge Test prompts (QZ-01 through QZ-05) use NotebookLM's native Flashcards and Quiz features and progress through Bloom's taxonomy from recall to judgment.

### 3. Apply the Audience-Lens Modifiers

The HTML toggle combines each card's `core` scaffold with an audience-specific suffix and a format-specific outro. See `references/audience-lenses.md` for the six lenses and their suffix patterns. **ELI5 is important**: it means "explain like I'm a fifth grader" — plain language, concrete analogies, no jargon without parenthetical paraphrase.

Do not hand-tune each of 144 prompt variants (24 × 6). Write the 24 `core` scaffolds once; let the lens modifiers reshape them at render time. The JavaScript composes `core + lens_suffix + format_outro` on the fly.

### 4. Apply the Brand Voice

See `references/brand-voices.md` for the voice cards, color palettes, typography, and the "do/don't" rules for each supported brand. The brand determines:
- Header gradient and accent colors (CSS variables)
- Typography pairing (serif display + sans body)
- The voice card content (Who / Tone / Signature move / Avoid)
- The `OUTRO` block language injected into every prompt ("Voice: [Brand] — [tone descriptors]...")

### 5. Render the HTML

See `references/html-template.md` for the template structure, the data-driven JavaScript pattern, and the worked CJR-X + The Analyst example.

The canonical worked example lives at:
`examples/cjrx-techy-surgeon-learner-pack.html`

When in doubt about layout, rendering, or JS composition patterns, read that file and adapt.

### 6. Save and Share

Save the HTML to a location agreed with the user (or a sensible default like `output/`) with a filename pattern: `{brand-slug}-{topic-slug}-learner-pack.html`.

Examples:
- `brand-a-framework-comparison-learner-pack.html`
- `brand-b-new-policy-learner-pack.html`
- `brand-c-annual-report-learner-pack.html`

Share with a computer:// link. Do not write a long post-amble — the artifact speaks.

## Quality Bar

Before handing over:

1. **Grounding check** — Read 3 random prompts. Could they be dropped into a Pack on a different topic with only a search-and-replace? If yes, ground them more deeply in the topic's specific constructs.
2. **Lens distinctness check** — Toggle ELI5 and Deep Dive on the same card. The two variants should read as genuinely different — not a template with an adjective swapped. Different emphasis, different vocabulary, different framing.
3. **Brand voice check** — The voice card at the top of the HTML should match the brand's established voice. The `OUTRO` block injected into every prompt should carry the same voice markers consistent with the brand's tone (e.g., "analytical, direct" vs. "academic, rigorous" vs. "operator-focused, enterprise-grade").
4. **Asset fidelity** — Infographic prompts produce image briefs, not essays. Audio prompts invoke NotebookLM's native Audio Overview. Deck prompts produce slide-by-slide outlines with speaker notes. Video prompts produce scene-by-scene storyboards. Don't mix the output formats.

## What Not To Do

- **Don't put gravitas openings in the prompts.** No melodramatic scene-setting (e.g., "In the quiet corridors where decisions are made..."). No staccato fragments for emphasis. Direct, operator-focused framing.
- **Don't hallucinate specifics.** If the source material doesn't mention a specific number, threshold, or actor, don't invent one. Better to leave the prompt slightly more general than to bake in a wrong detail.
- **Don't over-elaborate the lens modifiers.** The audience suffix should be 1-3 sentences. Longer modifiers dilute the core prompt.
- **Don't skip the grounding step.** A generic Pack is a failed Pack. The value is in topic-specific scaffolding.

## Reference Files

- `references/prompt-architecture.md` — The 24 asset slots, their structural scaffolds, grounding guidance per slot
- `references/audience-lenses.md` — The six lenses with suffix patterns and composition logic
- `references/brand-voices.md` — Voice cards, colors, typography for The Analyst, The Scholar, Modern Enterprise, and generic/custom brands
- `references/html-template.md` — HTML/CSS/JS structure and the data-driven rendering pattern
