# Audience Lenses — Six Framings for Every Prompt

The Learner Pack HTML exposes a toggle that reframes every prompt on the fly for the selected audience. The JavaScript composes `core + lens_suffix + format_outro` at render time — you only write the 24 `core` scaffolds once.

## The Six Lenses

1. **ELI5** — "Explain like I'm a fifth grader"
2. **Newbie** — Assumes no prior domain knowledge but is an adult professional
3. **Practitioner** — Frame for domain practitioners; emphasize delivery and application
4. **Operator** — Default lens; program leaders, operations heads, implementation teams
5. **Finance** — Finance leaders, outcome-based delivery finance, payment mechanics
6. **Deep Dive** — Senior-peer register; rigorous analytical treatment

---

## Lens Modifier Patterns

Each lens has five suffix variants — one per asset type (general/infographic, deck, audio, video, quiz). Paste the complete `LENS_MODIFIERS` object below into the HTML JavaScript and adapt topic-specific references if needed.

### ELI5

- **General/Infographic:** "Explain as if to a curious fifth grader or complete outsider. Use plain everyday language and concrete analogies (recipes, schools, neighborhoods, sports). Avoid jargon; when a technical term must appear, add a brief plain-English explanation in parentheses. Short sentences. Focus on the 'what' and 'why it matters,' not the technical 'how.'"
- **Deck:** "Explain as if to a curious fifth grader. First slide defines the topic in one plain sentence. Use a concrete analogy on every slide. No jargon without immediate plain-English paraphrase."
- **Audio:** "Explain as if to a curious fifth grader. Conversational, plain language. Concrete analogies throughout. Assume the listener knows nothing about this topic or domain."
- **Video:** "Explain as if to a curious fifth grader. Plain language, visual analogies (a ball game, a recipe, a neighborhood). Each scene should land one simple idea."
- **Quiz:** "Explain as if to a curious fifth grader. Use plain everyday vocabulary in both the questions and the answer choices. Wrong answers should be obviously wrong rather than tricky. Explanations should use simple analogies."

### Newbie

- **General:** "Assume the reader is a new analyst or early-career professional unfamiliar with this specific domain but comfortable with adjacent fields generally. Define technical terms on first use. Use plain language, but retain real vocabulary where it's load-bearing."
- **Deck:** "Assume the audience is new to the domain. First slide defines core vocabulary. Use analogies to anchor unfamiliar concepts."
- **Audio:** "Assume the listener is new to this topic. Start with a clear definition of the central construct. Explain each technical term the first time it appears."
- **Video:** "Assume the viewer has never encountered this topic. Open with the simplest version of what it is and why it exists. Keep language plain but professional."
- **Quiz:** "Assume the test-taker is new to the domain. Define technical terms inside the questions when needed. Wrong answers should reflect common beginner confusions. Explanations should fill in the foundational context."

### Practitioner

- **General:** "Emphasize practitioner workflow, participant or client impact, and service delivery — what changes at the point of delivery. Highlight case selection, quality measure implications, and planning considerations."
- **Deck:** "Frame for practitioners. Emphasize delivery workflows, case selection, quality measures, and service considerations. Include a workflow diagram slide."
- **Audio:** "Frame for practitioners. Emphasize delivery pathway implications, quality measures, and what service teams do differently."
- **Video:** "Frame for practitioners. Show delivery workflows and team decisions. Use the point-of-delivery and planning settings as anchoring scenes."
- **Quiz:** "Frame for practitioners. Test scenarios should arise from delivery workflow, case selection, and quality measure performance. Wrong answers should reflect plausible but incorrect practitioner decisions."

### Operator (Default)

- **General:** "Emphasize operational implications — program design, staffing, partner network, metrics to track, and the 30/60/90-day actions operators should take now."
- **Deck:** "Frame for program leaders and operations heads. Emphasize operational readiness, staffing, infrastructure, metrics dashboards, and 30/60/90-day actions."
- **Audio:** "Frame for program leaders. Emphasize operational decisions, infrastructure, partner network design, and preparation timelines."
- **Video:** "Frame for program leaders and operations teams. Show operational workflows, dashboards, and decision points."
- **Quiz:** "Frame for program leaders. Test scenarios should arise from operational decisions: program design, partner network configuration, staffing, metric thresholds, and 30/60/90-day actions. Wrong answers should reflect common operator misreads of the source."

### Finance

- **General:** "Emphasize financial mechanics — target metric construction, discount factors, risk corridors, reconciliation cadence, concurrent-program savings, and margin impact. Quantify where the source permits."
- **Deck:** "Frame for finance leaders. Emphasize target metric mechanics, reconciliation cadence, discount factors, risk corridors, and margin exposure. Include a quantitative slide."
- **Audio:** "Frame for finance leaders. Emphasize target metric construction, reconciliation mechanics, discount factors, and financial exposure. Quantify where the source allows."
- **Video:** "Frame for finance leaders. Show financial flows, target metric calculations, and margin implications. Use numbers where the source permits."
- **Quiz:** "Frame for finance leaders. Test scenarios should arise from target metric mechanics, reconciliation outcomes, risk-sharing structures, exposure limits, and concurrent-program savings. Quantify where the source allows. Wrong answers should be plausible margin or mechanics misreads."

### Deep Dive

- **General:** "Apply rigorous analytical treatment — design rationale, evidence base for parameter choices, edge cases, counterarguments, equity implications, and unresolved calibration questions. Senior-peer register."
- **Deck:** "Senior-peer register. Include slides on design rationale, evidence base, edge cases and counterarguments, and open calibration questions."
- **Audio:** "Senior-peer register. Surface design rationale, evidence base, edge cases, counterarguments, and unresolved calibration questions. Assume a sophisticated listener."
- **Video:** "Senior-peer register. Surface design trade-offs, evidence base, edge cases, and open questions. Assume a sophisticated viewer."
- **Quiz:** "Senior-peer register. Test items should require integrating multiple concepts, surface design rationale, edge cases, equity implications, and unresolved calibration questions. Wrong answers should be sophisticated near-misses, not naive errors. Multiple correct interpretations are acceptable when the source supports them."

---

## Customization Per Topic

Most lens suffixes are topic-agnostic and should stay as shown. Occasionally a topic has a "native" framing per audience that's worth injecting — e.g., for a regulatory framework, the Finance lens naturally references specific metric construction and risk corridor mechanics. Keep these topic-specific edits light; the modifier should still fit in 1-3 sentences.

## Distinctness Check

Before shipping, toggle ELI5 vs. Deep Dive on the same card. The two rendered prompts should read as substantially different outputs — different vocabulary, different emphasis, different framing. If they feel like the same prompt with an adjective swapped, revise the lens suffix pattern for that lens.
