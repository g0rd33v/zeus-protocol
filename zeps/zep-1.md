# ZEP-1: Prolog · Story · Epilog
**Status:** Accepted · **Author:** Eugene Gordeev · **Date:** April 1, 2026
**Domain:** Meta (applies to all seven domains)

---

## Prolog

Every digital output today is an orphan. A file arrives without context. A photo exists without intent. A document lands without the reasoning that shaped it. A message is read without knowing what preceded it or what should follow.

The person who created the output knows its full story — what led to it, what it is, what should happen next. But that knowledge lives exclusively in their head. When they move on, forget, or die, the output becomes a dead object. A result without origin. An artifact without future.

This is true for every file, every message, every image, every AI-generated result, every decision, every interaction. Billions of outputs produced daily, all missing the same thing: their complete narrative.

ZEP-1 proposes that every output in a Zeus-aligned system carries three layers of metadata — its full narrative — as a universal standard.

---

## Story

### The Three Layers

Every output — regardless of format, medium, or creator — has three narrative layers:

**Prolog** — what came before. The ancestry of the output. Why it exists, what problem it solves, what decisions shaped it, what alternatives were considered and rejected, what constraints applied. The Prolog answers: "How did we get here?"

**Story** — the output itself. What it is, right now, in its current form. The artifact, the file, the message, the photo, the result. Plus its essential properties: format, version, dependencies, relationships to other outputs. The Story answers: "What am I looking at?"

**Epilog** — what comes next. Guidance for anyone who interacts with this output in the future. How to modify it properly. What to preserve. What the creator intended as next steps. What tools or approaches work best. What boundaries exist. The Epilog answers: "What should I do with this?"

### Why Three Layers

The structure is not arbitrary. It mirrors the universal shape of narrative — every story ever told has a beginning, a middle, and a direction forward. Language itself operates this way. Every sentence exists in context (what was said before), carries meaning (what is being said), and implies continuation (what comes next).

Large language models — the engines of the AI era — are fundamentally narrative machines. They process sequences. They predict what follows from what came before. ZEP-1 aligns the structure of digital output with the structure of language itself. This makes every output natively intelligible to both humans and AI systems.

### What Each Layer Contains

**Prolog fields:**

| Field | Description |
|---|---|
| `origin` | What initiated this output — a request, a problem, an idea, an iteration |
| `intent` | The goal. What the creator was trying to achieve |
| `context` | Relevant background — project, conversation, constraints, prior versions |
| `decisions` | Key choices made during creation and why |
| `rejected` | Alternatives that were considered and discarded, with reasoning |
| `sources` | Inputs that informed the output — documents, data, conversations, references |

**Story fields:**

| Field | Description |
|---|---|
| `type` | What the output is — document, image, code, message, audio, decision, etc. |
| `format` | File format, encoding, technical specifications |
| `version` | Version number if applicable |
| `created` | Timestamp of creation |
| `creator` | Who or what produced it — person, AI model, system, collaboration |
| `relations` | Links to related outputs — parent, sibling, dependent |
| `content` | The output itself, or a reference to it |

**Epilog fields:**

| Field | Description |
|---|---|
| `next_steps` | What the creator intended to happen next |
| `guidance` | How to modify, extend, or iterate on this output properly |
| `preserve` | What should not be changed — the invariants |
| `boundaries` | Constraints on future modifications |
| `tools` | Recommended tools, prompts, or approaches for working with this output |
| `open_questions` | Unresolved issues the creator is aware of |

### Implementation Principles

**Automatic, not manual.** The person should not have to write Prolog and Epilog by hand. Zeus-aligned systems capture the Prolog from the process that produced the output and generate the Epilog from the Prolog and Story combined. The person reviews and approves — the labor is handled by AI.

**Layered detail.** Not every output needs full Prolog-Story-Epilog. A casual message might carry a minimal Prolog (just the `intent`) and no Epilog. A critical document might carry all fields, deeply populated. The system adapts the depth to the importance of the output.

**Machine-readable and human-readable.** The three layers must be stored in a format that both humans can scan and AI agents can parse. JSON, YAML, or embedded markdown — the format is implementation-dependent, but the structure is universal.

**Non-destructive.** The metadata layer never modifies the output itself. Prolog and Epilog wrap the Story — they do not alter it. The original artifact remains untouched.

**Portable.** The three layers travel with the output. When a file is shared, copied, or transferred, its Prolog and Epilog go with it. The narrative is never separated from the artifact.

### Example: This Landing Page

To make ZEP-1 concrete, here is the Prolog-Story-Epilog for the Zeus protocol landing page:

**Prolog:**
- `origin`: Eugene Gordeev conceived Zeus as an open-source protocol for extending human capability through AI, across all dimensions of existence
- `intent`: Create a landing page for zeus.labs.co that communicates the protocol's thesis, domains, maturity model, and open-source nature
- `context`: Follows the Zeus Protocol document v0.3. Part of the Labs.vc venture studio portfolio. Design must feel monumental and mythological — not SaaS, not corporate
- `decisions`: Dark theme with warm gold accents (not Atom's blue). Cormorant Garamond serif for carved/monumental feel. Lightning bolt as sole visual motif. Seven domain cards with custom SVG icons. Prolog-Story-Epilog narrative structure throughout
- `rejected`: Light theme (too casual for a protocol manifesto), purple/gradient schemes (generic AI aesthetic), Inter/system fonts (too corporate), multiple decorative elements (dilutes the monolithic feel)
- `sources`: Zeus Protocol v0.3, conversation history from conception through ZEP-1, Atom.me design system as negative reference (deliberately different identity)

**Story:**
- `type`: Landing page
- `format`: Single HTML file, self-contained, no external dependencies except Google Fonts
- `version`: v0.3
- `creator`: Claude (Opus) in collaboration with Eugene Gordeev
- `relations`: Parent: Zeus Protocol v0.3. Sibling: zeus-v0.3.md

**Epilog:**
- `next_steps`: Add ZEP governance section to the page. Connect "Read the Protocol" CTA to hosted protocol document. Set up GitHub repository for ZEPs
- `guidance`: Maintain the monolithic aesthetic — no bright colors, no playful elements, no SaaS patterns. Every section should feel like it belongs on a monument. When adding new sections, follow the existing pattern: section-divider, section-icon (custom SVG, 36x36, gold stroke), section-label, section-title with one em-italic gold word, prose paragraphs
- `preserve`: The hero structure (protocol label → Zeus → line → The Almighty Protocol → description). The gold-on-black color system. The Cormorant Garamond + IBM Plex Mono font pairing. The lightning bolt motif. The mission line "Empowering human life and beyond"
- `boundaries`: Do not add product-style elements (pricing, signup forms, feature comparisons). Do not use the Atom.me blue accent. Do not add photographs or stock imagery
- `tools`: Edit as raw HTML/CSS. No build system required. Test by opening the file directly in a browser. SVG icons are inline — modify directly in the HTML
- `open_questions`: GitHub repository structure for ZEPs not yet defined. Protocol document hosting solution not yet decided. Community discussion platform not yet chosen

---

## Epilog

ZEP-1 establishes the foundational metadata standard for the Zeus protocol. Every subsequent ZEP, every output produced within a Zeus-aligned system, and every contribution to the protocol itself should carry Prolog-Story-Epilog metadata.

This proposal has implications across all seven domains:

- **Cognitive**: Prolog preserves the reasoning chain behind decisions, making knowledge retrievable and auditable
- **Creative**: Epilog carries creative intent forward, so collaborators and future versions honor the original vision
- **Economic**: Business outputs (proposals, contracts, analyses) carry their full decision history, reducing miscommunication and rework
- **Physical**: Health data carries context — not just the measurement, but why it was taken and what to watch for next
- **Social**: Messages and communications carry intent and suggested follow-up, improving relationship quality
- **Emotional**: Personal reflections and journal entries carry their emotional context, enriching long-term self-knowledge
- **Temporal**: Every output a person produces throughout their life, fully annotated with Prolog and Epilog, becomes part of their preserved legacy — not just what they made, but how they thought and what they intended

ZEP-1 is the first proposal. It will not be the last. The structure it defines — Prolog, Story, Epilog — is itself the format for all future ZEPs.

---

*ZEP-1 · Prolog · Story · Epilog*
*Accepted · April 1, 2026*
*Zeus: The Almighty Protocol*
