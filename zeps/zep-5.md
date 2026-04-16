# ZEP-5: Edge Memory Cache

**Status:** Draft · **Date:** April 16, 2026
**Author:** Eugene Gordeev · **Domain:** Cognitive, Temporal

---

## Prolog

ZEP-3 (Living Memory) defines how a person's knowledge is stored: as a personal wiki in the cloud — interconnected Markdown files, fully versioned, source-grounded, portable. That wiki grows for a lifetime. It can reach gigabytes of text, millions of cross-links, and dense embedding indices.

A phone cannot hold all of that. A smartwatch cannot hold any of it. A voice-only earpiece has no storage at all. Yet these are the devices people carry every minute of the day — and these are the moments when personal context matters most.

The cloud is the source of truth. But the cloud is not always reachable, not always fast, and not always private. The person needs their memory on the device in their hand — not all of it, but the right slice, compressed to fit, formatted for the local model, and fresh enough to be useful.

Without a standard for edge caching, every device either runs without personal context (generic) or requires a permanent cloud connection (fragile, slow, privacy-exposed).

---

## Story

**Edge Memory Cache** defines how a person's cloud-based Living Memory is compressed, tailored, and synchronized to any edge device — so that a local small language model can operate with full personal context, offline, at hardware speed.

### Architecture

**One source of truth.** The full Living Memory wiki lives in the cloud: raw documents, complete embeddings, full wiki-graph, changelogs, session dumps. This is the canonical store defined by ZEP-3. It never moves to the device in full.

**Multiple Edge Memory Caches.** Each device the person owns maintains its own cache — a compressed, optimized subset of the full memory, generated specifically for that device's constraints and use case. A phone gets one cache. A laptop gets a different one. A wearable gets a minimal one. Each is independently generated and independently updated.

**Cache as a derivative, not a copy.** The cache is not a truncated mirror of the cloud. It is a purpose-built artifact — re-ranked, re-embedded, and re-structured for the target device. The generation process decides what to include, what to summarize, what to omit, and how to encode it for the local model.

### Cache Generation Parameters

Every Edge Memory Cache is generated using these parameters:

**Device constraints** — available memory, CPU/GPU capability, storage budget, battery state. A 4GB phone gets a different cache than a 32GB laptop.

**Target model** — the specific SLM running on the device (Gemma 2B, Phi-3 Mini, Parakeet, Qwen-1.5, etc.). The cache format — embedding dimensions, tokenization, quantization level — matches the model's architecture. No adapter layer needed. The cache is native to the model.

**Modality** — what the device is used for. Voice-only devices (earpieces, smart speakers) get caches weighted toward conversational context, names, recent events, and quick-recall facts. Multimodal devices get richer caches including visual references and document summaries. Text-only devices get dense informational caches.

**Time horizon** — how far back the cache reaches. A wearable for daily use might cache the last 24 hours plus persistent essentials (identity, contacts, active projects). A laptop for deep work might cache the last year plus full project histories.

**Domain weighting** — which Zeus domains are prioritized. A health-tracking wearable weights Domain IV (Physical). A work laptop weights Domain III (Economic) and Domain I (Cognitive). The person can set this explicitly or let the system infer from usage patterns.

### Sync Protocol

Caches are small by design — kilobytes to low megabytes. This makes frequent updates practical:

**Delta sync.** Only changes since the last update are transmitted. The cloud tracks which wiki pages changed, generates the relevant cache deltas, and pushes them to the device. Full cache rebuilds happen only when parameters change (new device, new model, changed time horizon).

**Sync frequency.** Configurable per device. A phone might sync every 15 minutes when on Wi-Fi. A wearable might sync hourly. A laptop might sync on every wake. The person sets the cadence. The system respects battery and bandwidth constraints.

**Offline resilience.** The cache is fully functional without a cloud connection. The person loses nothing when they're on a plane, in a tunnel, or in a location without service. The cache was built to be self-sufficient for its time horizon. When connectivity returns, it syncs.

### Cache Format

The cache contains two layers:

**Structured layer** — a compressed subset of the Living Memory wiki in a standardized format. Key entities (people, projects, events, decisions), their relationships, and their most recent state. Stored as structured data (JSON or MessagePack) that any compliant SLM can parse without additional training.

**Vector layer** — pre-computed embeddings matched to the target model's embedding space. These enable semantic search within the cache — the person asks a question, the local model retrieves relevant context from the cache vectors without calling the cloud.

Both layers use a standardized container format so that any device, any model, and any implementation can read any compliant cache. The format specification is part of this ZEP and will be published as an open standard.

### Privacy Model

Edge Memory Cache strengthens privacy by design:

**Minimum data principle.** The device holds only what it needs for its specific use case. A voice assistant doesn't need your financial history. A fitness tracker doesn't need your project documents. The cache generation process enforces this — data that doesn't match the device's modality, domain weighting, and time horizon never reaches the device.

**On-device inference.** With the cache present, the local SLM can answer personal questions without sending data to the cloud. The person's query and the retrieved context stay on the device. Only sync operations touch the network.

**Cache expiry.** Caches have a defined TTL (time to live). If a device goes unsynchronized beyond its TTL, the cache self-invalidates. A lost or stolen device doesn't carry a permanent copy of the person's memory.

**Encryption at rest.** The cache is encrypted on the device using a key derived from the person's authentication. Raw cache data is unreadable without the person's credentials.

---

## Epilog

Edge Memory Cache solves the last-meter problem of personal AI: your knowledge lives in the cloud, but your life happens on devices. Without edge caching, personal context is either unavailable offline, slow through cloud round-trips, or privacy-exposed through constant API calls.

With ZEP-5, every device the person owns becomes contextually aware — running a local model that knows who they are, what they're working on, and what matters to them right now. The cloud holds the complete picture. The edge holds exactly what's needed, exactly when it's needed.

This connects to the full Zeus stack:

- **ZEP-3 (Living Memory)** is the source — the cloud wiki that the cache is derived from
- **ZEP-2 (Simple Sync)** can trigger cache updates — a save operation in one chat can propagate to edge caches within minutes
- **ZEP-1 (Prolog-Story-Epilog)** metadata travels with cache entries, so the local model knows the context behind every piece of cached knowledge
- **ZEP-4 (Pealer)** can operate on-device using the edge cache for authentication and preference data, reducing cloud dependency for routine tasks

Open questions: standardization of the cache container format across SLM vendors, handling conflicts when the person modifies knowledge on-device while offline (edge writes back to cloud), maximum recommended cache sizes per device category, and governance of which data categories are eligible for edge caching (some data may be too sensitive to ever leave the cloud).

---

*ZEP-5 · Edge Memory Cache · April 16, 2026*
*Zeus: The Almighty Protocol*
