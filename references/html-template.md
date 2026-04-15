# HTML Template — Structure, JS Pattern, and Worked Example

## Canonical Worked Example

Read this file when you need to see the complete pattern in action:

`/sessions/eloquent-happy-archimedes/mnt/RevelAi Health/NotebookLM Learner Pack/one-pagers/techy-surgeon-learner-pack.html`

Topic: CJR-X. Brand: Techy Surgeon. 24 prompts, 6 audience lenses, dual sticky filter.

When building a new Pack, the fastest path is:
1. Copy the canonical example
2. Swap the brand CSS variables and voice card per `brand-voices.md`
3. Replace the 24 `PROMPTS` entries with topic-grounded versions per `prompt-architecture.md`
4. Keep the `LENS_MODIFIERS` and composition logic untouched unless you're adjusting for topic-specific lens framing

## File Structure

Single self-contained HTML. No external JS. Google Fonts CDN for typography. Embedded CSS and embedded JavaScript.

## Top-Level Sections

1. **`<style>`** — CSS variables (brand colors), typography import, component styles
2. **`<div class="header">`** — brand name, topic tag, subtitle
3. **`<div class="how-to">`** — 4-step how-to-use grid (ingest source → pick lens → copy prompt → paste into downstream tool)
4. **`<div class="voice-card">`** — navy/brand-dark card with voice specs (Who / Tone / Signature / Avoid)
5. **`<div class="filter-bar">`** (sticky) — two rows: audience lens buttons + asset type buttons
6. **`<div id="promptGrid">`** — rendered by JS from the PROMPTS data
7. **`<script>`** — PROMPTS data, LENS_MODIFIERS, OUTRO, render function

## Data Model

```js
const OUTRO = {
  infographic: "[brand voice-line] Output as a single copy-paste prompt I can paste into Napkin or Ideogram.",
  deck: "[brand voice-line] For each slide: title, 3–5 bullets, one-line speaker note.",
  audio: "[brand voice-line] Open with what the topic is and who it affects. No small talk, no gravitas.",
  video: "[brand voice-line] Scene-by-scene: visual description + narration + any on-screen text."
};

const LENS_MODIFIERS = {
  eli5:     { label, suffix, deck_suffix, audio_suffix, video_suffix },
  newbie:   { ... },
  clinical: { ... },
  operator: { ... },
  finance:  { ... },
  deepdive: { ... }
};

const PROMPTS = [
  {
    cat: "infographics",          // one of: infographics | slidedecks | audio | video
    id: "IG-01",                  // display ID
    title: "Side-by-Side Comparison — [Topic-specific subtitle]",
    tag: "Compare",               // short tag shown in corner of card
    desc: "For comparing [specific entities from source].",
    core: "From the source material, [topic-specific scaffold]...",
    outroKey: "infographic"       // one of: infographic | deck | audio | video
  },
  // ... 23 more
];
```

## Composition Logic

```js
function buildPromptText(p, lens) {
  const mod = LENS_MODIFIERS[lens];
  const suffix = p.outroKey === "deck" ? mod.deck_suffix
    : p.outroKey === "audio" ? mod.audio_suffix
    : p.outroKey === "video" ? mod.video_suffix
    : mod.suffix;
  return `${p.core} ${suffix} ${OUTRO[p.outroKey]}`;
}
```

## State Management

Two globals: `currentLens` (default `"operator"`) and `currentAsset` (default `"all"`).

- `setLens(lens)` updates `currentLens`, toggles the audience button active state, and calls `render()`
- `setAsset(asset)` updates `currentAsset`, toggles the asset button active state, and calls `render()`
- `render()` filters `PROMPTS` by `currentAsset` and rebuilds the DOM with the selected lens

## Copy Button

Uses `navigator.clipboard.writeText` when available in a secure context; falls back to `document.execCommand('copy')` via a hidden textarea for `file://` contexts. This dual path is important — users open these files locally and the modern API fails silently.

## Filter Bar Styling

Audience buttons use navy-dark active state. Asset buttons use brand-accent (teal for Techy Surgeon, royal blue for Duke, purple for RevelAi ModEnt) active state. This visual differentiation makes the two filters read as distinct controls.

## Responsive

Mobile breakpoint at 700px:
- `.how-to-steps` collapses from 4 columns to 2
- Header font sizes scale down
- Filter bar buttons wrap naturally

## Filename Convention

`{brand-slug}-{topic-slug}-learner-pack.html`

Examples:
- `techy-surgeon-cjrx-learner-pack.html`
- `duke-hip-fracture-policy-learner-pack.html`
- `revelai-modern-enterprise-team-model-learner-pack.html`

## Save Location

`/sessions/eloquent-happy-archimedes/mnt/RevelAi Health/NotebookLM Learner Pack/one-pagers/`

This folder is the canonical home for Learner Packs.
