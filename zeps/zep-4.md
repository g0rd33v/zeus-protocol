# ZEP-4: Pealer

**Status:** Draft · **Date:** April 16, 2026
**Author:** Eugene Gordeev · **Domain:** Cognitive, Physical

---

## Prolog

Every day, millions of people with visual impairments, poor eyesight, diabetes-related vision loss, age-related degeneration, or simply glasses navigate digital products designed by people who have never considered them. Every two to three years, product teams redesign interfaces — not to improve function, but to justify their employment. Nothing new is added. Nothing broken is fixed. The layout moves. The buttons change. The user relearns the same product from scratch, again.

For sighted users, this is an annoyance. For visually impaired users, it is a wall. Every redesign destroys their learned navigation. Every decorative element — splash screens, banners, promotional overlays, CAPTCHAs, cookie dialogs, animated transitions — is an obstacle between them and the result they need.

The web today is built for designers and managers. It is not built for people.

Zeus says: the person wants a result, not an interface. Strip everything else away.

---

## Story

**Pealer** is a protocol for AI-driven interface reduction. It defines how an AI agent navigates any digital service on behalf of a person — ignoring all visual presentation, bypassing all obstacles, and delivering only the functional result the person asked for, in the format they prefer.

### Core Mechanism

The person speaks a command. The AI agent operates a headless browser — a browser with no visual display, no rendering engine for the human eye. The agent navigates the target service programmatically, interacting with the underlying DOM and APIs rather than the visual interface. It extracts the functional result, formats it for the person's preferences (voice, large text, simplified layout, structured data), and delivers it with a single confirmation: **Ok?**

The visual interface is never shown. The person never sees the website. They see only their result.

### What Pealer Strips

**Advertising.** All promotional content, banners, interstitials, sponsored placements — ignored entirely. The agent does not render, click, or acknowledge ads.

**CAPTCHAs and bot detection.** Pealer operates as a user agent on behalf of an authenticated human. Where CAPTCHAs cannot be bypassed through standard accessibility APIs or authenticated sessions, the agent escalates to the person for a single verification step — then continues.

**Redesigns.** The agent does not depend on visual layout, CSS classes, or pixel positions. It navigates by function — form fields, buttons, links, data structures. When a service redesigns its interface, Pealer continues working because it reads the semantic structure, not the visual surface.

**Cookie dialogs, consent banners, notification prompts.** Automatically dismissed or declined. The person's privacy preferences are applied by default.

**Decorative elements.** Animations, transitions, splash screens, loading indicators, hero images, promotional carousels — none of these are rendered or processed.

**Complexity.** Multi-step forms, nested menus, pagination, infinite scrolling — the agent handles the navigation complexity internally and presents the person with the flat result.

### What Pealer Delivers

The person receives only what they asked for:

- "Check my bank balance" → a number, spoken aloud or displayed in their preferred format
- "Order my usual groceries" → a confirmation of items and total, then one-step approval
- "What's the status of my package?" → a delivery date and current location, nothing else
- "Pay my electricity bill" → amount confirmed, payment executed, receipt delivered

Every result follows the same pattern: **result → confirmation → done.** No navigation. No menus. No visual complexity.

### Personalization Layer

Pealer adapts its output to the person's Zeus profile:

**Voice-first users** receive spoken results with voice confirmation.

**Large-text users** receive results in their preferred font size, contrast, and color scheme — regardless of how the source service is designed.

**Structured-data users** receive raw results in a machine-readable format for further processing.

**Simplified users** receive results stripped to the absolute minimum — one number, one date, one yes/no.

The person defines their output preferences once. Pealer applies them everywhere, across every service, permanently.

### Integration with Zeus Protocol

**ZEP-1 (Prolog-Story-Epilog):** Every Pealer interaction carries metadata — what was requested, what was delivered, and what the person might want to do next.

**ZEP-2 (Simple Sync):** Pealer results can be saved to the person's RAG via Simple Sync links. A bank balance check automatically archives itself.

**ZEP-3 (Living Memory):** Pealer interactions feed directly into the person's wiki. Repeated tasks build patterns — the system learns "my usual groceries," "my bank," "my electricity provider" from history.

### Accessibility as the Default

Pealer is designed for visually impaired users first. But the principle applies universally: every person benefits from an AI that strips interfaces to pure function.

A sighted user stuck in a meeting can voice-command their banking without looking at a screen. An elderly user who never learned modern web interfaces can access any service through a single spoken command.

Accessibility is not a feature. It is the design principle. When you build for the person who cannot see, you build something better for everyone.

### Technical Architecture

**Headless browser engine** — Chromium-based, operating without visual rendering. Navigates via DOM manipulation, form submission, and API interception.

**Semantic navigation layer** — identifies functional elements by their semantic role, ARIA labels, and structural position — not by visual appearance. Redesign-resistant by design.

**Authentication management** — stores and manages the person's credentials for each service. Handles OAuth flows, session management, and re-authentication automatically.

**Result extraction engine** — identifies the requested data within the page content, extracts it, and formats it according to output preferences.

**Voice I/O** — speech-to-text for commands, text-to-speech for results. The entire interaction can be eyes-free.

**Confirmation protocol** — every action that modifies data requires explicit confirmation. Read-only queries execute immediately.

---

## Epilog

Pealer redefines the relationship between people and digital services. Instead of the person adapting to the interface, the interface is dissolved — replaced by a direct line between intent and result.

The name comes from peeling — stripping the layers of unnecessary complexity that have accumulated on every digital service. What remains after peeling is the fruit: the function the person actually needs.

People want results, not obstacles. People want to be happy.

Open questions: legal framework for AI agents acting on behalf of authenticated users, liability when an agent takes an incorrect action, standardization of service authentication for agent access, and rate limiting policies that may need adaptation for legitimate accessibility agents.

---

*ZEP-4 · Pealer · April 16, 2026*
*Zeus: The Almighty Protocol*
