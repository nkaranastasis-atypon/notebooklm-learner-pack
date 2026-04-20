# Brand Voices — Visual + Verbal Specs Per Brand

Every Learner Pack renders in a specific brand's voice. This file maps each supported brand to its CSS color variables, typography, voice card content, and the `OUTRO` voice-line injected into every prompt.

For richer brand treatment, also consult the corresponding branding skill (`the-analyst-branding`, `the-scholar-branding`, `modern-enterprise-branding`).

---

## The Analyst

**Colors (CSS variables):**
```css
--navy-dark: #1A2D42;
--navy: #2C4356;
--teal: #5BA8C9;
--teal-pale: #D4EEF7;
--cream: #F7F3ED;
```

**Typography:** Cormorant Garamond (serif display) + Source Sans Pro (sans body) + JetBrains Mono (prompt text).

**Header gradient:** `linear-gradient(135deg, #1A2D42, #2C4356)`

**Voice card:**
- **Who:** "A subject-matter expert speaking to domain operators, practitioners, policy leaders, and technologists."
- **Tone:** "Analytical, operator-focused, direct. Systems thinking. Grounded in primary sources. No dramatic openings or gravitas framing."
- **Signature move:** "Translate policy or research into operational implications — what changes for the people doing the work."
- **Avoid:** "Sales energy. Hyperbole. Unsupported generalizations."

**OUTRO voice-line for each prompt:** "Voice: The Analyst — analytical, direct, no dramatic framing."

---

## The Scholar

**Colors (CSS variables):**
```css
--duke-blue: #012169;
--duke-royal: #00539B;
--duke-blue-light: #0577B1;
--duke-gray: #333333;
--duke-warm-gray: #988675;
--cream: #F5F2EA;
```

**Typography:** The Sans (if available; fallback to Source Sans Pro) + serif display (Georgia or Playfair Display fallback).

**Header gradient:** `linear-gradient(135deg, #012169, #00539B)`

**Voice card:**
- **Who:** "Faculty at an academic research institution — researchers, policy analysts, and subject-matter specialists."
- **Tone:** "Rigorous, evidence-based, academically grounded. Systems thinking with policy depth. Careful with claims; careful with caveats."
- **Signature move:** "Connect local evidence and field research to broader policy debates, and vice versa."
- **Avoid:** "Advocacy without evidence. Sales register. Overclaiming impact."

**OUTRO voice-line for each prompt:** "Voice: The Scholar — academic, rigorous, evidence-grounded."

---

## Modern Enterprise

**Vibe:** Dynamic, empowering, professional, scientific.

**Colors (CSS variables):**
```css
--bg-paper: #f2f2eb;
--bg-heritage: #003b44;
--accent-bright-green: #00d975;
--accent-sage: #a3bfb5;
--accent-beacon-blue: #4885f7;
--accent-sky: #00ede1;
--accent-lime: #98f72d;
--data-green: #057a4b;
--insight-gold: #ffc800;
--active-red: #e52836;
--text-dark: #003b44;
--text-light: #ffffff;
```

**Typography:** Inter (display + body) + IBM Plex Mono (CTA/labels). All monospace labels uppercase with +100 tracking.

```css
/* Headline */
font: 300 clamp(2rem, 5vw, 4rem)/1.1 'Inter', 'Segoe UI', sans-serif;
letter-spacing: -0.02em;

/* Subhead */
font: 600 clamp(1.2rem, 2.5vw, 2rem)/1.2 'Inter', 'Segoe UI', sans-serif;
letter-spacing: -0.01em;

/* Body */
font: 400 clamp(1rem, 1.5vw, 1.2rem)/1.2 'Inter', 'Segoe UI', sans-serif;
letter-spacing: -0.01em;

/* CTA / Labels */
font: 400 clamp(0.8rem, 1.2vw, 1rem)/1 'IBM Plex Mono', 'Consolas', monospace;
text-transform: uppercase;
letter-spacing: 0.1em;
```

**Layout:** Centered for hero/title slides; left-aligned for content slides. Generous white space throughout.

**Header gradient:** `linear-gradient(135deg, #003b44, #057a4b)`

**Signature elements:**
- **Frame Effect (Impact lines):** 2–5 concentric rounded rectangles (border-radius ≥ 20px) with uneven gaps (e.g., 10 / 20 / 30px from edge) and 3–8px stroke weight varying per frame.
  - *Full frame:* all four edges, used on title/hero slides.
  - *Corner frames:* corner positions only, used on content slides with left-aligned text.
  - *Dark variant:* `#00d975` frames on `#003b44` background.
  - *Light variant:* `#00d975` frames on `#f2f2eb` background.
  - Implemented as absolutely-positioned `div`s or border pseudo-elements. Purpose: energy and brand recognition without competing with content.
- Line icons inside squoval (rounded-square) containers.
- Scientific, geometric, flat illustrations with subtle depth.
- Conceptual photography with clear-space overlay for text and impact lines; minimum 40% dominant brand tone in images.
- WCAG-compliant contrast: heritage green or black on light backgrounds; white on dark.

**Voice card:**
- **Who:** "An enterprise platform for domain coordination, outcome-based delivery, and workflow automation. Speaking to enterprise operators, finance leaders, and strategic decision-makers."
- **Tone:** "Dynamic, empowering, professional. Clear, confident, substantive. Peer-to-peer with sophisticated buyers."
- **Signature move:** "Connect policy or market dynamics to specific operational and product implications at the enterprise level."
- **Avoid:** "Sales energy. Vague capability claims. Jargon without substance."

**OUTRO voice-line for each prompt:** "Voice: Modern Enterprise — dynamic, operator-focused, enterprise-grade."

---

## Generic / Custom Brand

If the user specifies a brand not in this reference, ask for:
1. Two to four brand colors (primary dark, primary accent, pale/highlight, background)
2. Typography pairing
3. A 3-4 line voice description (who / tone / signature move / avoid)
4. A one-line `OUTRO` voice-line to inject into prompts

Fall back gracefully — a Pack with a generic dark-blue + neutral-gray palette and a clean Inter stack still produces a usable artifact.

---

## OUTRO Block Template

The HTML JavaScript uses an `OUTRO` object keyed by asset type. Customize the voice-line per brand, but keep the format directive consistent:

```js
const OUTRO = {
  infographic: "[BRAND_VOICE_LINE] Output as a single copy-paste prompt I can paste into Napkin or Ideogram.",
  deck: "[BRAND_VOICE_LINE] For each slide: title, 3–5 bullets, one-line speaker note.",
  audio: "[BRAND_VOICE_LINE] Open with what the topic is and who it affects. No small talk, no gravitas.",
  video: "[BRAND_VOICE_LINE] Scene-by-scene: visual description + narration + any on-screen text."
};
```

Swap `[BRAND_VOICE_LINE]` for the brand-specific line from above.
