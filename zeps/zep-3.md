# ZEP-3: Living Memory

**Status:** Draft · **Date:** April 12, 2026
**Author:** Eugene Gordeev · **Domain:** All

---

## Prolog

Zeus captures a person's entire existence across seven domains. But capture without structure is noise. Every AI system today produces conversations that vanish, context that resets, and knowledge that exists only as opaque vectors with no human-readable form. There is no standard for how a person's accumulated AI-generated knowledge should be stored, structured, linked, versioned, shared, or verified against its source material.

Without a storage standard, Zeus has no memory format — only disposable sessions.

---

## Story

**Living Memory** defines how all Zeus-generated knowledge is stored: as interconnected Markdown files organized as a personal wiki, where every file is traceable to its raw source, carries a full changelog, and can be shared, exported, or queried from any system.

### Core Principles

**Files, not vectors.** The primary storage unit is a human-readable Markdown file — not an opaque embedding. Vectors are derived from files for search purposes, but the file is the source of truth. A person can open, read, edit, and understand their own memory without any tool.

**Wiki, not folders.** Files link to each other by reference. A person page links to the projects they're mentioned in. A project page links to the people, places, and decisions involved. A decision page links to the conversations where it was made. The structure is a graph, not a tree.

**Changelog, not snapshots.** Every file carries a log of every change — what was added, when, and from which conversation or session. The person can see how any piece of knowledge evolved over time. Nothing is silently overwritten.

**Grounded, not hallucinated.** Every fact in a wiki page traces back to raw source data — a conversation transcript, a recording dump, a direct user input. If a file contains "Berlin project deadline is June," there is a traceable link to the exact conversation where that was said. Zero hallucination means zero ungrounded claims.

**Shareable, not locked.** Any file or subset of files can be shared via link, exported as standard Markdown, or made accessible to external AI systems through a retrieval endpoint. The person controls what is shared and what stays private.

**Extractable, not trapped.** The full wiki — or any individual file — can be exported at any time in standard Markdown format. No proprietary encoding, no vendor lock-in. The person owns their memory in a format that outlives any product.

### File Anatomy

Every Living Memory file contains:

- **Content** — structured Markdown with semantic sections
- **Metadata** — creation date, last modified, source session IDs, domain tags
- **Links** — references to related wiki pages (people, places, topics, decisions)
- **Changelog** — append-only log of all modifications with timestamps and source references
- **Origin** — pointer(s) to the raw conversation or recording that produced or modified this file

### How It Works

A person speaks. The system transcribes, understands, and routes the content: new information creates new wiki pages, updated information modifies existing pages and appends to their changelogs, entities (people, places, things) are cross-linked automatically. The raw conversation is stored as a session dump — the wiki pages are the structured, evolving interpretation built on top of it.

The wiki is the knowledge. The raw data is the proof.

---

## Epilog

Living Memory gives Zeus a universal storage format that is human-readable, machine-queryable, version-tracked, source-grounded, and fully portable. Every Zeus domain — Cognitive, Creative, Economic, Physical, Social, Emotional, Temporal — writes to and reads from the same wiki structure, creating one interconnected map of a person's existence.

Open questions: conflict resolution when multiple systems write to the same page simultaneously, privacy tiers within the wiki (which pages are shareable, which are locked), and retention policies (should any memory ever be automatically pruned, or is permanence the default).

---

*ZEP-3 · Living Memory · April 12, 2026*
*Zeus: The Almighty Protocol*
