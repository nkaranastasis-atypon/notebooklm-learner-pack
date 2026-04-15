# Audience Lenses — Six Framings for Every Prompt

The Learner Pack HTML exposes a toggle that reframes every prompt on the fly for the selected audience. The JavaScript composes `core + lens_suffix + format_outro` at render time — you only write the 24 `core` scaffolds once.

## The Six Lenses

1. **ELI5** — "Explain like I'm a fifth grader"
2. **Newbie** — Assumes no prior domain knowledge but is an adult professional
3. **Clinical** — Frame for clinicians; emphasize care delivery
4. **Operator** — Default lens; service line leaders, COOs, operational teams
5. **Finance** — CFOs, VBC finance leaders, payment mechanics
6. **Deep Dive** — Senior-peer register; rigorous analytical treatment

---

## Lens Modifier Patterns

Each lens has five suffix variants — one per asset type (general/infographic, deck, audio, video, quiz). Paste the complete `LENS_MODIFIERS` object below into the HTML JavaScript and adapt topic-specific references if needed.

### ELI5

- **General/Infographic:** "Explain as if to a curious fifth grader or complete outsider. Use plain everyday language and concrete analogies (recipes, schools, neighborhoods, sports). Avoid jargon; when a technical term must appear, add a brief plain-English explanation in parentheses. Short sentences. Focus on the 'what' and 'why it matters,' not the technical 'how.'"
- **Deck:** "Explain as if to a curious fifth grader. First slide defines the topic in one plain sentence. Use a concrete analogy on every slide. No jargon without immediate plain-English paraphrase."
- **Audio:** "Explain as if to a curious fifth grader. Conversational, plain language. Concrete analogies throughout. Assume the listener knows nothing about healthcare policy or medicine."
- **Video:** "Explain as if to a curious fifth grader. Plain language, visual analogies (a ball game, a recipe, a neighborhood). Each scene should land one simple idea."
- **Quiz:** "Explain as if to a curious fifth grader. Use plain everyday vocabulary in both the questions and the answer choices. Wrong answers should be obviously wrong rather than tricky. Explanations should use simple analogies."

### Newbie

- **General:** "Assume the reader is a new analyst or early-career professional unfamiliar with this specific domain but comfortable with healthcare generally. Define technical terms on first use. Use plain language, but retain real vocabulary where it's load-bearing."
- **Deck:** "Assume the audience is new to the domain. First slide defines core vocabulary. Use analogies to anchor unfamiliar concepts."
- **Audio:** "Assume the listener is new to this policy area. Start with a clear definition of the central construct. Explain each technical term the first time it appears."
- **Video:** "Assume the viewer has never encountered this topic. Open with the simplest version of what it is and why it exists. Keep language plain but professional."
- **Quiz:** "Assume the test-taker is new to the domain. Define technical terms inside the questions when needed. Wrong answers should reflect common beginner confusions. Explanations should fill in the foundational context."

### Clinical

- **General:** "Emphasize clinical workflow, patient impact, and care delivery — what changes at the bedside, in the OR, in the post-op course. Highlight case selection, quality measure implications, complication management, and discharge planning."
- **Deck:** "Frame for clinicians. Emphasize care pathways, case selection, quality measures, and complication management. Include a workflow diagram slide."
- **Audio:** "Frame for clinicians. Emphasize care pathway implications, clinical quality measures, and what care teams do differently."
- **Video:** "Frame for clinicians. Show clinical workflows and care team decisions. Use the OR, clinic, and post-op home as anchoring settings."
- **Quiz:** "Frame for clinicians. Test scenarios should arise from clinical workflow, case selection, complication management, and quality measure performance. Wrong answers should reflect plausible but incorrect clinical decisions."

### Operator (Default)

- **General:** "Emphasize operational implications — service line design, staffing, post-acute network, metrics to track, and the 30/60/90-day actions operators should take now."
- **Deck:** "Frame for service line leaders and COOs. Emphasize operational readiness, staffing, infrastructure, metrics dashboards, and 30/60/90-day actions."
- **Audio:** "Frame for service line leaders. Emphasize operational decisions, infrastructure, post-acute network design, and preparation timelines."
- **Video:** "Frame for service line leaders and operations teams. Show operational workflows, dashboards, and decision points."
- **Quiz:** "Frame for service line leaders. Test scenarios should arise from operational decisions: service line design, post-acute network configuration, staffing, metric thresholds, and 30/60/90-day actions. Wrong answers should reflect common operator misreads of the source."

### Finance

- **General:** "Emphasize financial mechanics — target price construction, discount factor, stop-loss/stop-gain corridors, reconciliation cadence, concurrent-program savings retention, and margin impact. Quantify where the source permits."
- **Deck:** "Frame for CFOs and VBC finance leaders. Emphasize target price mechanics, reconciliation cadence, discount factors, stop-loss corridors, and margin exposure. Include a quantitative slide."
- **Audio:** "Frame for VBC finance leaders. Emphasize target price construction, reconciliation mechanics, discount factors, and financial exposure. Quantify where the source allows."
- **Video:** "Frame for finance leaders. Show financial flows, target price calculations, and margin implications. Use numbers where the source permits."
- **Quiz:** "Frame for VBC finance leaders. Test scenarios should arise from target price mechanics, reconciliation outcomes, gainsharing/alignment structures, stop-loss exposure, and concurrent-program savings retention. Quantify where the source allows. Wrong answers should be plausible margin or mechanics misreads."

### Deep Dive

- **General:** "Apply rigorous analytical treatment — design rationale, evidence base for parameter choices, edge cases, counterarguments, equity implications, and unresolved calibration questions. Senior-peer register."
- **Deck:** "Senior-peer register. Include slides on design rationale, evidence base, edge cases and counterarguments, and open calibration questions."
- **Audio:** "Senior-peer register. Surface design rationale, evidence base, edge cases, counterarguments, and unresolved calibration questions. Assume a sophisticated listener."
- **Video:** "Senior-peer register. Surface design trade-offs, evidence base, edge cases, and open questions. Assume a sophisticated viewer."
- **Quiz:** "Senior-peer register. Test items should require integrating multiple concepts, surface design rationale, edge cases, equity implications, and unresolved calibration questions. Wrong answers should be sophisticated near-misses, not naive errors. Multiple correct interpretations are acceptable when the source supports them."

---

## Customization Per Topic

Most lens suffixes are topic-agnostic and should stay as shown. Occasionally a topic has a "native" framing per audience that's worth injecting — e.g., for CJR-X, the Finance lens naturally references "target price construction, discount factor, stop-loss corridors." Keep these topic-specific edits light; the modifier should still fit in 1-3 sentences.

## Distinctness Check

Before shipping, toggle ELI5 vs. Deep Dive on the same card. The two rendered prompts should read as substantially different outputs — different vocabulary, different emphasis, different framing. If they feel like the same prompt with an adjective swapped, revise the lens suffix pattern for that lens.
