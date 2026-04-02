# ZEP-2: Simple Sync
**Status:** Accepted · **Author:** Eugene Gordeev · **Date:** April 2, 2026
**Domain:** Cognitive (applies across all domains where knowledge transfer occurs)

---

## Prolog

Every AI chat is an island. Your conversation with Claude does not know what you discussed with ChatGPT. Your ChatGPT memory cannot access your Perplexity research. Your custom RAG system holds knowledge that none of your chat windows can reach. Every platform, every model, every tool operates in isolation — and the person in the middle loses context constantly.

The current solutions are complex: API integrations, custom plugins, MCP servers, OAuth flows, developer tools. They work for engineers. They do not work for the billions of people who use AI through chat interfaces and expect things to simply work.

Zeus says: sync should be as simple as clicking a link.

---

## Story

### The Mechanism

Simple Sync turns a URL into a universal bridge between any AI system and any RAG storage. The link is structured, human-readable, and executable in a browser. No integrations. No plugins. No custom code. No developer required.

A Simple Sync link contains three components:

```
https://{rag-host}/{api-key}/{function}/{query}
```

**rag-host** — the domain of the RAG service that stores or retrieves knowledge.

**api-key** — the access token for the person's knowledge base. This is portable — it works in any browser, any chat, any context.

**function** — what to do. Two core operations:
- `save` — store information into the RAG
- `retrieve` — pull information from the RAG

**query** — the payload. For save operations, this is the content to store (a snapshot, a summary, a conversation extract). For retrieve operations, this is the search query.

### How It Works

**Saving knowledge from any chat:**

1. A person is chatting with Claude, ChatGPT, Perplexity, or any AI
2. They ask: "Save this conversation summary to my knowledge base"
3. The AI outputs a Simple Sync link with the save function and the summary as the query
4. The person clicks the link — their browser opens a web page
5. The web page shows what will be saved and asks for confirmation
6. One click — the data is stored in their RAG
7. The person returns to their chat

**Retrieving knowledge into any chat:**

1. A person is chatting with any AI
2. They need context from their personal knowledge base
3. They paste a Simple Sync retrieve link (or ask the AI to generate one)
4. The AI fetches the URL, reads the retrieved content from the web page, and incorporates it into the conversation
5. The person now has their full context — regardless of which AI they're using

**Cross-platform memory sync:**

1. A person wants their Claude memory available in ChatGPT
2. They ask Claude: "Export my memory as a Simple Sync save link"
3. Claude generates the link with all memory items as the payload
4. The person clicks — data saved to their RAG
5. They then ask ChatGPT: "Retrieve my context from this link" and paste the retrieve URL
6. ChatGPT fetches the page, reads the content, and now has the person's full context
7. The person can save ChatGPT's memory the same way back to the RAG

Two chats. No integration. Just links.

### The Web Interface

Every Simple Sync link resolves to a web page. This is critical — the operation is never invisible. The person always sees:

- **For save:** A preview of what will be stored, a confirm button, and a success message. The person is always in control.
- **For retrieve:** The retrieved content displayed as readable text on a web page. Both the person and any AI that fetches the URL can read it.

This means Simple Sync works with or without AI. A person can bookmark a retrieve link and access their knowledge base directly in a browser. A developer can build a web interface on top of any RAG system using Simple Sync URLs. The link is the interface.

### Extended Use Cases

**Chat-to-chat sync:** Move context between Claude, ChatGPT, Gemini, Perplexity, or any AI — in either direction.

**Memory portability:** Export memory from one platform, import into another. No lock-in.

**Knowledge base as a service:** Any RAG provider that supports Simple Sync URLs becomes accessible from any AI chat, any browser, any device.

**Team knowledge sharing:** A team member saves research to a shared RAG. Others retrieve it from any chat they're using. No shared workspace tool required.

**AI-to-AI handoff:** An agent in one system saves its findings. An agent in another system retrieves and continues the work.

**Non-AI access:** Builders add a lightweight AI model to their RAG's web interface. Users interact with their knowledge base through the browser — searching, browsing, and working with their data without needing a separate chat app.

**Snapshot archiving:** At the end of any work session, save a snapshot of the full conversation context to the RAG. Start a new session anywhere, retrieve the snapshot, and continue exactly where you left off.

### Security Model

The API key in the URL grants access. This is simple by design — the person controls who has their key. For sensitive use cases:

- Keys can be scoped (read-only, write-only, full access)
- Keys can be rotated or revoked at any time
- The RAG provider can enforce rate limits, IP restrictions, or additional authentication
- The web confirmation page prevents accidental saves — the person always confirms

The tradeoff is explicit: maximum simplicity at the cost of URL-visible API keys. For most personal knowledge management use cases, this is the right tradeoff. For enterprise or sensitive data, providers can layer additional security on top of the basic protocol.

### Implementation Requirements for RAG Providers

To support Simple Sync, a RAG provider must:

1. Accept structured URLs in the format `https://{host}/{key}/{function}/{query}`
2. Return a human-readable web page for both save and retrieve operations
3. Require user confirmation for save operations (no silent writes)
4. Display retrieved content as clean, readable text that both humans and AI scrapers can parse
5. Support API key-based authentication at minimum

That's it. Five requirements. Any RAG provider can implement Simple Sync in a day.

---

## Epilog

ZEP-2 solves the most immediate friction point in the AI era: knowledge is trapped inside the tool that created it. Every chat, every platform, every model builds a silo. The person — the one who owns the knowledge — cannot move it freely.

Simple Sync breaks the silo with the simplest possible mechanism: a URL. No SDKs, no OAuth, no integration marketplace. A link that any chat can generate, any browser can open, and any RAG can process.

This connects directly to the Zeus protocol's mission:

- **Cognitive domain:** Your knowledge is portable. It follows you across every AI tool, every device, every conversation. You never lose context because you switched platforms.
- **Temporal domain:** Every conversation, every insight, every decision can be saved to your personal knowledge base automatically. Over a lifetime, this builds the comprehensive map of your mind that Zeus requires for persistence beyond death.
- **The Engine:** Simple Sync is the practical mechanism that keeps your personal Zeus layer current — no matter which foundation model you're using at any given moment.

The name says it: Simple Sync. Not Smart Sync, not AI Sync, not Enterprise Sync. Simple. A link. A click. Done.

**Relationship to other ZEPs:**

- ZEP-1 (Prolog-Story-Epilog): Every save operation can include Prolog-Story-Epilog metadata alongside the content, enriching the RAG with full narrative context.
- Future ZEPs may define standard query formats, content schemas, and cross-RAG federation protocols that build on Simple Sync as the transport layer.

---

*ZEP-2 · Simple Sync*
*Accepted · April 2, 2026*
*Zeus: The Almighty Protocol*
