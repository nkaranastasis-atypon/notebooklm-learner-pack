# NotebookLM Learner Pack

A Claude skill that turns any topic and source corpus into a branded, copy-paste-ready prompt library for [NotebookLM](https://notebooklm.google.com). One invocation produces 29 prompts across 5 asset types, each with 6 audience-lens variants, in a single self-contained HTML file.

> **Companion article:** [The Learner Pack — How I Turned NotebookLM Into a Lifelong Learning Engine](#) *(Techy Surgeon Substack)*

---

## What You Get

Each generated Learner Pack is a single self-contained HTML file with:

- **29 copy-paste prompts** organized into 5 asset types
- **6 audience-lens variants** per prompt, toggled live in the browser
- **Brand voice** baked into every prompt (Techy Surgeon, Duke Health, RevelAi Modern Enterprise, or custom)
- **Topic-grounded scaffolds** — prompts name the specific constructs from your source material, not generic placeholders

### Asset Types

| Type | Count | Feeds |
|------|-------|-------|
| Infographics | 10 | Napkin, Ideogram, Midjourney |
| Slide Decks | 5 | PPTX skill, Gamma |
| Audio Overviews | 5 | NotebookLM native Audio Overview |
| Video Storyboards | 4 | Veo3, Runway |
| Knowledge Tests | 5 | NotebookLM Flashcards + Quiz |

### Audience Lenses

| Lens | For | Vocabulary |
|------|-----|-----------|
| ELI5 | Curious fifth grader | Everyday words, concrete analogies |
| Newbie | Early-career professional new to the domain | Defines terms on first use |
| Clinical | Clinicians | Care workflow, case selection, quality measures |
| Operator | Service line leaders (default) | Operations, staffing, metrics, 30/60/90-day actions |
| Finance | VBC finance leaders | Target price, reconciliation, margin, stop-loss |
| Deep Dive | Senior peers | Design rationale, edge cases, calibration questions |

### The Five Knowledge Tests (Bloom's Taxonomy Spine)

Recall → Application → Diagnosis → Synthesis → Judgment

1. **Terminology Flashcards** — vocabulary mastery
2. **Scenario Decision Flashcards** — "what would you do here"
3. **Common-Mistake Quiz** — failure-mode pattern recognition
4. **Integration Quiz** — multi-concept synthesis
5. **Tradeoff Quiz** — no-perfect-answer judgment

---

## Installation

### Option A — Direct install (Claude Desktop, Cowork)

1. Download `dist/notebooklm-learner-pack.skill` from this repo
2. Open Claude Desktop or Cowork
3. Install the `.skill` file via your skills interface

### Option B — Claude Code

1. Clone this repo
2. Move the `notebooklm-learner-pack/` folder into your `.claude/skills/` directory:
   ```bash
   git clone https://github.com/YOUR-HANDLE/notebooklm-learner-pack.git
   mv notebooklm-learner-pack/notebooklm-learner-pack ~/.claude/skills/
   ```
3. Restart Claude Code

### Option C — Manual

Copy `SKILL.md` and the `references/` folder into a new `notebooklm-learner-pack/` directory inside your Claude skills path.

---

## Usage

Once installed, invoke the skill in any Claude session with a natural-language request. The skill will ask for any missing parameters.

### Example prompts

```
Make me a Techy Surgeon Learner Pack on CJR-X.
Here are the key source documents: [attached PDFs or URLs]
```

```
Build a Duke-branded Learner Pack on hip fracture policy.
Topic is the recent Health Affairs piece on CMS fracture bundles —
I've dropped the PDF into the chat.
```

```
Generate a RevelAi Modern Enterprise Learner Pack on the TEAM model.
Audience default: Finance. Pull context from my Notion workspace
if an MCP is connected.
```

The skill returns a single HTML file. Open it in any browser, toggle the audience lens and asset type filters, copy any prompt, and paste it into your NotebookLM notebook. The notebook must already have your source documents ingested — the skill does not handle ingestion itself.

### End-to-end (NotebookLM MCP, advanced)

If you have a [NotebookLM MCP](https://modelcontextprotocol.io) connected to Claude Code, you can skip the copy-paste step entirely:

```
Create a Mind Map for me on CJR-X, clinical lens.
```

Claude Code loads the skill, composes the correct prompt, invokes the NotebookLM MCP, and the Mind Map appears inside your NotebookLM notebook. One session, zero copy-paste.

---

## Worked Example

A live worked example is included at `examples/cjrx-techy-surgeon-learner-pack.html`. Open it in a browser to see the rendered Pack with all 29 prompts and the dual-filter UI in action.

Topic: CJR-X (FY2027 IPPS Proposed Rule). Brand: Techy Surgeon.

---

## Customization

### Supported brands out of the box

- **Techy Surgeon** — analytical clinician-entrepreneur voice, navy/teal/cream palette
- **Duke Health** — academic/policy rigor, Duke royal blue palette
- **RevelAi Modern Enterprise** — operator-forward enterprise SaaS, deep purple palette

### Custom brands

Specify your own brand voice when invoking the skill. Supply: primary colors (2–4 hex values), typography pairing, a 3–4 line voice description, and a one-line signature line to inject into every prompt. See `references/brand-voices.md` for the template.

### Adding topics, asset types, or lenses

The architecture is data-driven: 29 prompt scaffolds, 6 audience modifiers, a per-brand OUTRO table. Edit `references/prompt-architecture.md` to add asset types or `references/audience-lenses.md` to add lenses. The HTML template composes prompts on the fly.

---

## Why This Exists

Every time I ingested a new source corpus into NotebookLM, I found myself re-writing the same prompts from scratch — infographic briefs, audio overview specs, deck outlines. The prompts needed to name the specific constructs in the source to produce good output. That meant real writing every time, which meant I ran fewer asset types per corpus, which meant I got less out of each one.

This skill codifies that workflow. A topic and a brand in, a grounded prompt library out. One abstraction I can apply to any new policy rule, research corpus, abstract book, or meeting transcript.

The Knowledge Tests addition is inspired by [Wyndo at AI Maker](https://wyndo.substack.com) and his observation that testing is where the gap between "I think I know this" and "I actually know this" gets exposed. NotebookLM's native Flashcards and Quiz features deserve first-class treatment in a learning workflow.

---

## Contributing

Pull requests welcome. A few directions I'd love help with:

- Additional brand voices (AOA, MSK Access, Margolis, and others)
- New asset types (e.g., Obsidian-ready outline, Anki deck export format)
- Workflow playbooks for specific trigger events (policy drop, meeting debrief, conference abstract book)
- A companion NotebookLM MCP for end-to-end asset execution

---

## License

MIT. See [LICENSE](LICENSE).

---

## Credits

- **Skill design and iteration:** Christian Pean, MD
- **Built with:** [Claude](https://claude.ai), [skill-creator](https://github.com/anthropics/skills)
- **Inspired by:** [Wyndo's viral NotebookLM tutorial](https://wyndo.substack.com)

Questions, feedback, or war stories from your own Learner Pack runs: open an issue or reply to the companion article on Substack.
