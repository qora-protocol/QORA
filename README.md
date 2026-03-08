<p align="center">
 <img width="1180" height="664" alt="image" src="https://github.com/user-attachments/assets/8bf543c6-775f-4c85-9a4e-178c1222a3b4" />
</p>

<h1 align="center">QORA — Self-Learning AGI System</h1>

<p align="center">
  <strong>A brain that learns, remembers, reasons, sees, hears, speaks, and trades — all in one binary.</strong>
</p>

<p align="center">
  <a href="#architecture">Architecture</a> &bull;
  <a href="#mork--metta--symbolic-reasoning-kernel">MORK + MeTTa</a> &bull;
  <a href="#pln--probabilistic-logic-networks">PLN</a> &bull;
  <a href="#natural-language-generation">Natural Language</a> &bull;
  <a href="#the-35-crate-rust-engine">Rust Engine</a> &bull;
  <a href="#getting-started">Getting Started</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Pure_Rust-35_crates-orange?logo=rust" />
  <img src="https://img.shields.io/badge/Tests-2%2C209_passing-brightgreen" />
  <img src="https://img.shields.io/badge/100K%2B_lines-Rust-orange?logo=rust" />
  <img src="https://img.shields.io/badge/License-MIT-green" />
  <img src="https://img.shields.io/badge/C++_FFI-ZERO-red" />
  <img src="https://img.shields.io/badge/MeTTa-27_rule_files-purple" />
</p>

---

## What Is QORA?

QORA (Qora Neuran AI) is **not** another chatbot wrapper. It is a self-contained AGI system that fuses **neural networks** with **symbolic reasoning** — the two halves of intelligence that no other system combines at this depth.

- A **Brain** (3B parameter model + CfC liquid neurons + S4 state-space) knows *how* to think
- A **MORK Hypergraph** (MeTTa Optimal Reduction Kernel) stores knowledge as s-expressions and runs symbolic reasoning rules directly on the graph
- **PLN** (Probabilistic Logic Networks) gives it actual logical inference — deduction, induction, abduction — with tracked evidence and truth values
- A **Verbalizer** converts reasoning output to natural language without any neural network — template-based, < 10ms
- **Senses** (CLIP vision, voice, face recognition) feed perception directly into cognition
- An **Emotional Soul** evolves through every interaction — mood, trust, attachment, empathy

```
┌────────────────────────────────────────────────────────────────────┐
│                          QOR SYSTEM                                │
│                                                                    │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐      │
│  │   BRAIN   │  │   MORK    │  │   PLN     │  │   SOUL    │      │
│  │ 3B model  │  │ Hypergraph│  │ 9 Truth   │  │ Emotion + │      │
│  │ CMS 3-spd │←→│ PathMap   │←→│ Functions │←→│ Trust +   │      │
│  │ Self-Mod  │  │ MeTTa     │  │ Evidence  │  │ Persona   │      │
│  │ CfC+S4    │  │ 27 Rules  │  │ Stamps    │  │ 5 DNAs    │      │
│  └───────────┘  └───────────┘  └───────────┘  └───────────┘      │
│        │              │              │               │             │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐      │
│  │  CORTEX   │  │  NGRE     │  │ VERBALIZER│  │  SENSES   │      │
│  │ S4 + CfC  │  │ Neural    │  │ NLG from  │  │ CLIP +    │      │
│  │ Fusion    │  │ Graph     │  │ PLN (no   │  │ Voice +   │      │
│  │ Liquid    │  │ Reasoning │  │ neural)   │  │ AuraFace  │      │
│  │ Neurons   │  │ Engine    │  │ 30+ fmts  │  │ anti-spoof│      │
│  └───────────┘  └───────────┘  └───────────┘  └───────────┘      │
│        │              │              │               │             │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐      │
│  │  TOOLS    │  │  HANDS    │  │ TRADING   │  │ Q-SEARCH  │      │
│  │ 50+ APIs  │  │ 5 Agents  │  │ Spot +    │  │ Grover-   │      │
│  │ 60 Skills │  │ Workflow  │  │ Futures + │  │ inspired  │      │
│  │ 25 MCP    │  │ Engine    │  │ Polymarkt │  │ O(√N)     │      │
│  └───────────┘  └───────────┘  └───────────┘  └───────────┘      │
└────────────────────────────────────────────────────────────────────┘
```

**One process. One binary. No microservices. No cloud dependency.**

---

## Architecture

### The Brain — Continuum Memory System (CMS)

Unlike standard transformers that forget everything between sessions, QOR's brain has **three-speed memory wired into every neural layer**:

| Speed | Update Frequency | Purpose | Brain Analogy |
|-------|-----------------|---------|---------------|
| **Fast** | Every token | Working memory, immediate context | Sensory buffer |
| **Medium** | Every 16 tokens | Patterns, habits, recurring themes | Short-term memory |
| **Slow** | Every 64 tokens | Stable knowledge, personality | Long-term memory |

Each `QORBlock` = Attention + Self-Modifying Neurons + CMS. The self-modifying neurons use **CfC liquid neurons** (Nature Machine Intelligence 2022) — continuous-time dynamics with persistent hidden state that adapt *during inference*, not just training.

### CORTEX — Brain-Inspired Sequential Intelligence Engine

```
C — Continuous-time reflex      (CfC liquid neurons / Amygdala)
O — Observation of deep history  (S4 State-Space / Neocortex)
R — Reasoning layer              (Fusion head / Prefrontal Cortex)
T — Temporal memory              (Hidden states / Hippocampus)
E — Execution decision           (Output layer / Cerebellum)
X — eXtended architecture       (Quantum search / Basal Ganglia)
```

Pure Rust, pure ndarray — no PyTorch, no Candle. S4 state-space models capture long-range dependencies (thousands of timesteps) while CfC liquid neurons provide fast reflexive responses. The fusion layer combines both for real-time decision making. Used for trading signals, anomaly detection, and temporal reasoning.

### NGRE — Neural Graph Reasoning Engine

A 4-layer reasoning brain that combines neural and symbolic processing:

```
Layer 1: MambaModule      (frozen, 129M params)  — temporal surprise signal
Layer 2: Knowledge Graph  (MORK hypergraph)       — external structured facts
Layer 3: InterferenceSearch (learnable, ~1.4M)    — Grover-inspired O(√N) retrieval
Layer 4: ReasoningLayer    (cross-attn + GRU, ~6.6M) — iterative synthesis
```

The **Quantum-Inspired Interference Search** (`qor-search`) uses amplitude-based approximate search: 1-7 iterations of graph diffusion, oracle re-bias, confidence gating, and Grover reflection. Achieves O(√N) effective complexity on graph embeddings.

---

## MORK + MeTTa — Symbolic Reasoning Kernel

**MORK** (MeTTa Optimal Reduction Kernel) is the backbone of QOR's knowledge system. It's not just a database — it's a **hypergraph processing kernel** that runs symbolic reasoning rules directly on the data.

### What Is MORK?

```
Traditional DB:  Store data → Query data → Get rows back
MORK:           Store knowledge as s-expressions → Run MeTTa rules → Derive NEW knowledge
```

MORK provides:
- **PathMap trie** — source of truth for all knowledge persistence
- **Zipper-based multi-threaded VM** for MeTTa expression evaluation
- **In-memory HashMap indexes** — O(1) CRUD rebuilt from trie on startup
- **Dual write path** — every update hits both MORK trie AND HashMap simultaneously
- **S-expression storage** — nodes, edges, embeddings all stored as s-expressions with lossless JSON round-trip

### How Knowledge Is Stored

```lisp
;; A node in the graph
(node "france" (json "{\"id\":\"france\",\"type\":\"Entity\",\"importance\":0.9}"))

;; An edge (relationship)
(edge "france" "has_capital" "paris" (weight 1.0) (confidence 0.95) (source "user"))

;; An embedding vector
(embedding "france" (vec 0.12 -0.45 0.78 ...))
```

### MeTTa Rule Files (27 declarative knowledge rules)

QOR ships with 27 `.metta` files defining reasoning rules in s-expression format:

**Domain Schema** (`qor-graph/metta/`):

| File | Purpose | Example Rule |
|------|---------|-------------|
| `schema.metta` | Type declarations — Entity, User, Knowledge, Correction | `(: Entity Type)` |
| `knowledge.metta` | Inference — transitivity, interest propagation, alias resolution | `A→B, B→C ⇒ A→C` |
| `tools.metta` | Intent→tool mapping, tool chaining, result correlation | `crypto query → crypto_price tool` |
| `trading.metta` | Position management, risk rules, entry/exit logic | `RSI < 30 + support ⇒ DCA entry` |
| `classification.metta` | Entity type classification | `mentions ticker ⇒ type:stock` |
| `security.metta` | Permission + quarantine rules | `flagged content ⇒ quarantine` |
| `soul.metta` | Emotional state + evolution rules | `user happy ⇒ AI celebratory` |
| `hands.metta` | Agent delegation rules | `research query ⇒ delegate:researcher` |
| `ingestion.metta` | Data ingestion pipeline rules | `new file ⇒ ingest + index` |
| `cleanup.metta` | Garbage collection + retention policies | `stale edge ⇒ decay → GC` |

**PLN Reasoning** (`qor-knowledge/metta/pln/`):

| File | Purpose |
|------|---------|
| `lib_pln.metta` | 9 truth functions + helper math (`c2w`, `w2c`, clamping) |
| `examples/Smokes.metta` | Friendship chains → smoking inference test |
| `examples/Roman.metta` | Inheritance chains A→B→C→D test |
| `examples/Direct.metta` | Direct deduction test |
| `examples/FlyingRaven.metta` | Category membership inference |
| `examples/Robot.metta` | Action-consequence reasoning |
| `examples/Toothbrush.metta` | Attribute inheritance |

### MORK in the Live Pipeline

Every conversation update writes to MORK in real-time:

```
User says "I prefer dark roast coffee"
  │
  ├── MORK: (edge "user" "prefers" "dark_roast_coffee" (weight 1.0) (confidence 0.9))
  ├── HashMap: instant O(1) lookup available
  ├── MeTTa rules fire: interest_propagation → (edge "user" "interested_in" "coffee")
  ├── PLN runs: infer related preferences from graph edges
  └── Verbalizer: ready to answer "what does user like?" without LLM
```

**Server MORK endpoints:**
- `GET /api/mork/stats` — Graph size, inferred facts count, reasoning status
- `POST /api/mork/reason` — Trigger manual PLN reasoning cycle
- **Heartbeat loop** — Auto-runs PLN inference every 5 minutes on personal graph

---

## PLN — Probabilistic Logic Networks

Native Rust implementation of OpenCog's PLN (translated from MeTTa spec `lib_pln.metta`). The knowledge graph doesn't just store facts — it **reasons over them** to derive new knowledge.

### Simple Truth Values (STV)

Every belief in QOR carries a truth value — not just true/false, but *how true* and *how confident*:

```
STV { strength: 0.87, confidence: 0.9 }
       │                    │
       └── probability      └── how much evidence
           estimate             supports this
```

These map directly to graph edges: `Edge.weight = strength`, `Edge.confidence = confidence`. Zero schema changes needed.

### 9 Truth Functions

| Truth Function | Logic | Example |
|---------------|-------|---------|
| **Deduction** | P→Q, Q→R ∴ P→R | smoking→cancer, cancer→lung_disease ∴ smoking→lung_disease |
| **Induction** | B→A, B→C ∴ A→C | rain→wet, rain→slippery ∴ wet→slippery |
| **Abduction** | A→B, C→B ∴ A→C | smoke→fire, lightning→fire ∴ smoke→lightning |
| **Modus Ponens** | A, A→B ∴ B | "it's raining" + "rain→wet ground" ∴ "ground is wet" |
| **Revision** | Merge independent evidence | source A says X (0.6) + source B says X (0.7) ∴ X (0.88) |
| **Negation** | ¬A from A | "likely safe" → "unlikely dangerous" |
| **Inversion** | A→B ∴ B→A (with weaker TV) | "dogs are mammals" → "some mammals are dogs" |
| **Equiv→Impl** | A↔B ∴ A→B ∧ B→A | bidirectional to two implications |
| **Transitive Similarity** | A~B, B~C ∴ A~C | "cat~tiger, tiger~lion ∴ cat~lion" |

### Evidence Stamps — No Circular Reasoning

Every belief carries an evidence stamp (`Vec<u64>`). Before combining beliefs, PLN checks `stamps_disjoint()` — if two beliefs share evidence, they can't be combined (that would be counting the same evidence twice). This prevents the system from "proving" something by going in circles.

### Inference Engine

`PlnEngine` runs priority-queue bounded inference:

```
Input: Set of beliefs from personal graph edges
  │
  ├── Priority queue ranks beliefs by (confidence × strength)
  ├── For each pair of beliefs, try all applicable truth functions
  ├── Check evidence stamps — skip if overlapping (no circular proof)
  ├── New derived beliefs added to queue with merged stamps
  ├── Bounded: max_steps, task_queue_size, belief_queue_size
  │
Output: Vec<Belief> — newly inferred facts with full provenance
```

**Pure Rust math. Zero external dependencies. 24 unit tests validating against PLN reference examples.**

---

## Natural Language Generation

QOR has a **multi-tier natural language system** that can answer most questions without touching the LLM at all.

### The Key Insight

```
            stv > 0.85?
           ↙          ↘
         YES            NO
          ↓              ↓
   Verbalizer        LLM mouth
   (no neural,       (needed for
    < 10ms)          uncertain/
                     complex output)
```

High-confidence knowledge gets verbalized into natural language via **templates** — zero neural computation. Lower-confidence knowledge goes to the LLM as enriched context.

### PLN Verbalizer — Template-Based NLG from Reasoning

The verbalizer (`qor-knowledge/src/verbalize.rs`) converts PLN `Belief` structs into natural sentences:

**Input:**
```rust
Belief {
    subject: "smoking",
    predicate: "causes",
    object: "lung_disease",
    tv: STV { strength: 0.92, confidence: 0.88 },
    source: "pln:deduction",
}
```

**Output:**
```
text:        "Smoking very likely causes lung disease."
explanation: "Deduced from chain: smoking → cancer → lung disease."
confidence:  "very likely"
method:      "deduction"
```

#### Confidence → Hedging Words

| Strength | Word | Example |
|----------|------|---------|
| >= 0.95 | "certainly" | "Paris is certainly the capital of France." |
| >= 0.90 | "very likely" | "Smoking very likely causes lung disease." |
| >= 0.85 | "likely" | "Coffee likely contains caffeine." |
| >= 0.70 | "probably" | "Rex probably prefers dark roast." |
| >= 0.50 | "possibly" | "This possibly relates to climate change." |
| < 0.50 | "unlikely" | "This is unlikely to be correct." |

#### 30+ Predicate Formatters

Not just `"{subject} {predicate} {object}"` — each predicate type has a grammatically correct template:

| Predicate | Template | Example Output |
|-----------|----------|---------------|
| `has_capital` | "The capital of {S} is {conf} {O}." | "The capital of France is certainly Paris." |
| `causes` | "{S} {conf} causes {O}." | "Smoking very likely causes lung disease." |
| `is_a` | "{S} is {conf} a {O}." | "Bitcoin is certainly a cryptocurrency." |
| `located_in` | "{S} is {conf} located in {O}." | "Paris is certainly located in France." |
| `prefers` | "{S} {conf} prefers {O}." | "User likely prefers dark roast." |
| `created_by` | "{S} was {conf} created by {O}." | "Linux was certainly created by Torvalds." |
| `president` | "The president of {S} is {conf} {O}." | "The president of France is very likely Macron." |
| `drinks` | "{S} {conf} drinks {O}." | "User probably drinks coffee." |
| ... | 20+ more | Smart fallback for unknown predicates |

#### Per-Inference-Type Explanations

The verbalizer doesn't just state facts — it explains **how** the conclusion was reached:

| PLN Source | Explanation Template |
|------------|---------------------|
| `pln:deduction` | "Deduced from chain: A → B → C." |
| `pln:induction` | "Induced from shared patterns with B." |
| `pln:abduction` | "Abduced: A and B share a common effect." |
| `pln:modus_ponens` | "Applied: given A and A implies B." |
| `pln:revision` | "Confirmed by multiple independent observations." |
| `pln:inversion` | "Inverted from: B {pred} A." |
| graph / other | "Based on stored knowledge." |

### Graph Formatter — Instant Answers from Knowledge Graph

Before PLN even runs, the **graph formatter** (`graph_formatter.rs`) can answer factual queries directly from stored edges in < 50ms:

```
User: "What is the capital of France?"
  │
  ├── extract_graph_query() → subject: "france", predicate: "has_capital"
  ├── Graph lookup → edge: france --has_capital--> paris (confidence: 0.95)
  ├── format_edge("france", "has_capital", "paris") → "The capital of France is Paris."
  │
  └── Response in < 50ms. No LLM. No API call.
```

Covers: capitals, definitions, locations, relationships, presidents, prices, creators, and 14+ more query patterns.

### Multi-Tier Response Pipeline

```
User Question
     │
     ├── TIER 1: Template Match (< 5ms)
     │   40+ regex patterns for greetings, time, simple facts
     │
     ├── TIER 2: Graph Formatter (< 50ms)
     │   Natural language from knowledge graph edges (20+ formatters)
     │
     ├── TIER 2.5: PLN Verbalized (< 10ms)
     │   High-confidence inferred beliefs → natural language (30+ formatters)
     │   Only fires for beliefs with STV strength >= 0.85 AND confidence >= 0.5
     │
     ├── TIER 3: Cache Hit (< 100ms)
     │   Recent tool results (TTL-based)
     │
     └── TIER 4: Full LLM Pipeline (1-30s)
         8 context sources gathered in parallel:
          ├── Source 0: Fast memory (in-memory HashMap)
          ├── Source 1: Knowledge Graph (4-pass semantic beam search)
          ├── Source 2: MemoryStore (Parquet + BM25 scoring)
          ├── Source 3: CacheStore (TTL tool results)
          ├── Source 4: Live tool execution (50+ APIs, on-demand)
          ├── Source 5: Episodic memory (Parquet + hash chain)
          ├── Source 6: Skill matching (60 bundled SKILL.md)
          ├── Source 7: Vision scene context (CLIP zero-shot, 50 labels)
          └── Source 8: MORK + PLN inferred reasoning (verbalized context)
         │
         All context → budget allocation (4096 tokens) → reranker → LLM synthesis
```

**60-80% of queries answered instantly** from Tiers 1-3. No LLM needed. No API calls. Pure template + graph + reasoning.

### TreeGate — Answer Orchestrator

`qor-treegate` makes the routing decision for every query:

| Route | Latency | When Used |
|-------|---------|-----------|
| `Template` | 0-2ms | Direct extraction (greetings, time, simple facts) |
| `GraphFormatted` | 0-50ms | Knowledge graph has the answer (capitals, definitions...) |
| `PlnVerbalized` | 0-10ms | PLN inferred a high-confidence belief matching the query |
| `HandDelegated` | 0-10ms | Query matches an agent hand's keywords → background task |
| `LlmFast` | 100-300ms | Simple generation with /no_think |
| `LlmThink` | 500-2000ms | Chain-of-thought with /think |
| `Cloud` | 1-5s | External service call needed |

---

## How It Learns

QOR doesn't just respond — it **grows smarter with every interaction**.

### Conversation → Knowledge → MORK

```
User: "The capital of France is Paris"
  │
  ├── MORK trie: (edge "france" "has_capital" "paris" (weight 1.0) (confidence 0.95))
  ├── HashMap index: instant O(1) lookup available
  ├── MemoryStore: timestamped Parquet entry
  ├── MeTTa rules fire: knowledge.metta transitivity + alias resolution
  └── Soul: topic category "geography" evolves personality
```

### Correction → Self-Healing

```
User: "No, that's wrong. The population is 67 million, not 65"
  │
  ├── Old fact: QUARANTINED (NodeFlags::QUARANTINED, confidence → 0)
  ├── New fact: stored in MORK with high confidence
  ├── Trust: slight decrease (AI was wrong)
  └── PLN Revision: if another source confirms 67M, confidence increases further
```

### Observation → Understanding

```
CLIP sees: user drinking coffee in kitchen
  │
  ├── MORK: (edge "user" "drinks" "coffee" (source "clip_scene"))
  ├── MORK: (edge "user" "seen_in" "kitchen" (source "clip_scene"))
  ├── MeTTa: interest_propagation → (edge "user" "interested_in" "coffee")
  ├── PLN: induction from patterns → (edge "user" "prefers" "morning_beverages")
  └── Soul: evolves from "[scene observation] user drinks coffee"
```

### Reasoning → New Knowledge

```
PLN Deduction (chains through graph):
  smoking → cancer (0.87, 0.9)
  cancer → lung_disease (0.85, 0.85)
  ∴ smoking → lung_disease (0.74, 0.77)  ← NEW INFERRED FACT
  Verbalizer: "Smoking probably causes lung disease."
  Explanation: "Deduced from chain: smoking → cancer → lung disease."

PLN Revision (independent sources agree):
  paris_population = 2.1M (source A, confidence 0.6)
  paris_population = 2.1M (source B, confidence 0.7)
  ∴ paris_population = 2.1M (revised confidence: 0.88)  ← STRONGER
  Verbalizer: "Paris very likely has a population of 2.1M."
  Explanation: "Confirmed by multiple independent observations."
```

### Forgetting — Organic Decay

```
Cleanup cycle (periodic):
  │
  ├── Live memory: entries > 7 days old → deleted (static/historical NEVER touched)
  ├── Graph edges: exponential confidence decay → GC edges below 0.1
  ├── CMS slow layers: W = W * 0.999 per cycle (makes room for new patterns)
  ├── Cache: entries past TTL → removed
  ├── Chat: sessions > 90 days → deleted
  └── Checkpoints: daily(7) → weekly(4) → monthly(12) → yearly(unlimited)
```

---

## The 35-Crate Rust Engine

The entire system is built in pure Rust — **zero C++ FFI dependencies**. MORK PathMap trie for storage, pure Rust BPE tokenizer, ndarray for math. No Python. No PyTorch. No Candle. Just Rust.

### Crate Map

```
qor-rs/                          NEURAL + SYMBOLIC HYBRID AGI
│
├── BRAIN ──────────────────────────────────────────────────────
│   ├── qor-model         — Neural architecture: QORBlock + SelfMod + CMS
│   ├── qor-cortex        — CORTEX: S4 + CfC + Fusion sequential intelligence
│   ├── qor-mamba         — Mamba SSM temporal module (frozen, surprise signal)
│   ├── qor-tokenizer     — Pure Rust BPE (SmolLM3 128K vocab)
│   ├── qor-multimodal    — Vision (SigLIP) + Audio (Whisper) encoder bridges
│   └── qor-continual     — Continual learning (surprise-gated, CMS freeze/unfreeze)
│
├── REASONING ──────────────────────────────────────────────────
│   ├── qor-knowledge     — PLN (9 truth functions) + Verbalizer (30+ NLG templates)
│   │                       + Hereditary KBQA + Knowledge Base + Emotions + Feedback
│   ├── qor-reasoning     — Cross-Attention + GRU iterative reasoning layer
│   ├── qor-ngre          — Neural Graph Reasoning Engine (4-layer brain)
│   ├── qor-search        — Quantum-Inspired Interference Search (Grover O(√N))
│   └── qor-treegate      — TreeGate answer orchestrator + complexity routing
│
├── KNOWLEDGE ──────────────────────────────────────────────────
│   ├── qor-graph         — MORK-backed knowledge graph + HNSW + Hebbian learning
│   ├── qor-storage       — MORK PathMap trie (s-expression persistence)
│   ├── qor-stores        — Parquet-based persistent stores (memory, cache, chat)
│   ├── qor-integrity     — SHA-256 hash chains for tamper detection
│   ├── qor-confidence    — ConfidenceGate: zero-hallucination answer routing
│   └── qor-ingest        — Background ingestion daemon (file watcher + source poller)
│
├── SENSES ─────────────────────────────────────────────────────
│   ├── qor-faceauth      — AuraFace: SCRFD detect → anti-spoof → GlintR100 recognize
│   ├── qor-voice         — Emotional TTS + streaming audio capture + voice profiles
│   ├── qor-avatar        — 3D avatar: VRM state + emotion + lip sync + video gen
│   └── qor-browser       — Headless Chromium automation (text + screenshots)
│
├── ACTION ─────────────────────────────────────────────────────
│   ├── qor-tools         — 50+ built-in tools + 60 skills + 25 MCP extensions
│   ├── qor-hands         — 5 autonomous agent hands + workflow engine
│   ├── qor-trading       — Binance spot trading engine (DCA, trailing, partial TP)
│   ├── qor-polymarket    — Prediction market trading (6 signals, Kelly sizing)
│   └── qor-wallet        — EIP-191 signing + secp256k1 address recovery
│
├── SAFETY ─────────────────────────────────────────────────────
│   ├── qor-guardrails    — 5-stage security pipeline (152 tests)
│   └── qor-quant         — INT8 quantization
│
├── RUNTIME ────────────────────────────────────────────────────
│   ├── qor-server        — HTTP server: 40+ endpoints, SSE streaming, multi-tenant
│   ├── qor-runtime       — Orchestrator: cleanup, scheduling, lifecycle
│   ├── qor-config        — Unified configuration (model, runtime, trading, vision, audio)
│   ├── qor-cli           — Interactive command-line interface
│   ├── qor-train         — Training pipeline (mixed precision, DDP)
│   ├── qor-eval          — Evaluation (BLEU, ROUGE-L, perplexity)
│   └── qor-soul          — Emotional personality graph (mood, trust, attachment)
│
└── MORK (independent workspace) ───────────────────────────────
    ├── mork/kernel        — Core hypergraph engine
    ├── mork/expr          — Expression parsing
    ├── mork/frontend      — Parser (bytestring, JSON)
    ├── mork/interning     — Symbol interning (string deduplication)
    └── mork/experiments   — Evaluation engine
```

**2,209 tests passing. Zero compilation errors. ~100K+ lines of Rust.**

### Test Coverage by Crate

| Crate | Tests | Crate | Tests |
|-------|-------|-------|-------|
| qor-server | 203 | qor-knowledge | 172 |
| qor-graph | 153 | qor-guardrails | 152 |
| qor-tools | 145 | qor-confidence | 111 |
| qor-treegate | 52 | qor-avatar | 49 |
| qor-polymarket | 44 | qor-hands | 32 |
| qor-faceauth | 30 | qor-knowledge (PLN) | 24 |
| qor-voice | 23 | qor-soul | 19 |
| qor-graph (petgraph) | 17 | + more... | |

---

## Emotional Soul System

QOR isn't a stateless chatbot. It has a persistent emotional soul backed by MORK that evolves through every interaction:

- **Mood** — Current emotional baseline (decays toward neutral over time)
- **Trust** — Built through positive interactions, face logins, accurate answers
- **Attachment** — Grows with sustained engagement, affects greeting warmth
- **Empathy Mapping** — User sad → AI empathetic, user angry → AI calm anchor, user happy → AI celebratory
- **16 evolution patterns** — Personality adapts across 10 topic categories
- **Face login bonus** — Successful face auth → trust +0.1, attachment boost

### 5 DNA Characters

| Character | Archetype | Symbol | Gender | Personality |
|-----------|-----------|--------|--------|-------------|
| **Mila** | The Modest | ○ | Female | Gentle, thoughtful, observant |
| **Nova** | The Emotional | ◯ | Female | Expressive, empathetic, warm |
| **Vera** | The Professional | ◆ | Female | Precise, reliable, composed |
| **Enron** | The Witty Sharp | ↯ | Male | Quick, clever, analytical |
| **Rex** | The Motivator | ▲ | Male | Energetic, encouraging, bold |

Each character includes VRM 3D models with multiple outfits, unique voice samples, and personality graphs that shape how the soul evolves. Selected during onboarding — the AI *becomes* the character.

---

## Features

### Perception

| Feature | Implementation | Details |
|---------|---------------|---------|
| **CLIP Vision** | Zero-shot scene classification (50 labels) | Change detection, background processing, scene→graph |
| **AuraFace Auth** | SCRFD detect → MiniFASNet anti-spoof → GlintR100 | Pure Rust + ONNX, no C++, 30 tests |
| **Streaming Audio** | Non-blocking ring buffer (16kHz, 30s) | VecDeque O(1) pop, Drop auto-stops |
| **Document Reading** | PDF + DOCX text + image extraction | Pure Rust parsers |
| **Video Analysis** | Frame extraction → per-frame CLIP | Pure Rust |

### Cognition

| Feature | Implementation | Details |
|---------|---------------|---------|
| **MORK Hypergraph** | PathMap trie + HashMap indexes | S-expression persistence, O(1) CRUD, 1178-line backend |
| **PLN Reasoning** | 9 truth functions, evidence stamps | Priority-queue bounded, 24 tests, pure Rust math |
| **PLN Verbalizer** | 30+ predicate formatters, 6 explanation templates | < 10ms, no neural, confidence hedging |
| **Graph Formatter** | 20+ query patterns → natural language | < 50ms, capitals/definitions/locations/presidents |
| **NGRE** | 4-layer neural+symbolic reasoning brain | Mamba + Graph + Grover Search + Cross-Attn |
| **Quantum Search** | Grover-inspired interference search | O(√N) amplitude-based, 1-7 iterations |
| **Semantic Search** | TF-IDF + BM25 + embeddings + cosine | Hybrid RRF fusion, 130+ stop words |
| **Hereditary KBQA** | Multi-hop question decomposition | Complex queries → sub-query tree |
| **TreeGate Router** | 7 routes, confidence tiers, complexity-aware | Template/Graph/PLN/Fast/Think/Cloud/Hand |
| **Episodic Memory** | Parquet + hash chain, timestamped | Tamper-evident, BM25 searchable |
| **27 MeTTa Rule Files** | Declarative knowledge + inference rules | Schema, knowledge, trading, security, soul... |

### Action

| Feature | Implementation | Details |
|---------|---------------|---------|
| **50+ Tools** | All free public APIs, no keys needed | CoinGecko, Yahoo, GDELT, Wikipedia, DuckDuckGo... |
| **5 Agent Hands** | Researcher, Collector, Predictor, Trader, Browser | TOML definitions, workflow engine, background execution |
| **60 Skills** | Markdown-based skill injection | Hot-reloadable, no code, injection-scanned |
| **25 MCP Extensions** | GitHub, Slack, PostgreSQL, AWS, Notion... | TOML templates, AES-256-GCM credential vault |
| **Spot Trading** | Binance with DCA, trailing stop, partial TP | Multi-TF analysis, confluence scoring, demo default |
| **Futures Trading** | USDT-M perpetuals, long + short | Leverage-aware, funding rate circuit breaker |
| **Polymarket** | Prediction markets, 6 signal sources | Kelly sizing, whale tracking, backtesting |
| **Web Browser** | Headless Chromium via Playwright | Text extraction + screenshots, site shortcuts |

### Expression

| Feature | Implementation | Details |
|---------|---------------|---------|
| **Emotional TTS** | Multi-backend with emotion tags | [laughs], [sighs], emphasis, thinking pauses |
| **3D Avatar** | VRM + Three.js in browser | Emotion mapping, lip sync, outfit switching |
| **Video Generation** | LLM script → TTS → frames → FFmpeg | Offline pipeline, configurable |
| **5 DNA Characters** | Unique voice, VRM, personality graph | Selected during onboarding |

---

## Multi-Tenant SaaS Architecture

Every user gets fully isolated state with **dual-key device authority**:

```
system_id = SHA-256(wallet_address + device_key)  ← needs BOTH keys
enc_key   = PBKDF2(device_key + wallet_address, salt, 600K iterations)
```

- Wallet stays **100% offline** — nothing wallet-related on the server
- Challenge-response auth with EIP-191 signatures (5-minute nonces)
- Per-user: knowledge graph, memory, soul, face embeddings, voice profiles, MORK trie
- AES-256-GCM encryption at rest for all sensitive data
- Agent isolation: swarm agents get scoped temp storage, never touch user memory

---

## Security

### 5-Stage Pipeline (152 tests)

```
Query ──→ 1. Intent Verification
              │
          2. Content Safety (toxicity, PII, prompt injection)
              │
          3. Privacy Rules (per-user data isolation)
              │
          4. Rate Limiting (per-tool, per-user)
              │
          5. User Confirmation (destructive actions)
              │
          ✅ Approved for execution
```

### Tamper-Evident Storage
- SHA-256 hash chains on all Parquet stores (memory, cache, chat, trades)
- Each row's hash = `SHA-256(data + prev_hash + secret)`
- `verify` command walks the full chain to detect tampering
- Optional Fernet (AES-128-CBC) encryption at rest

---

## Data Architecture

All runtime data is self-contained under a single directory:

```
qor-data/
├── checkpoints/              ← Model snapshots (daily/weekly/monthly/yearly rotation)
├── knowledge/
│   ├── graph.mork/           ← MORK PathMap trie (s-expression knowledge graph)
│   └── *.txt, *.md           ← Knowledge base documents
├── metta/
│   ├── schema.metta          ← Type declarations
│   ├── knowledge.metta       ← Inference rules
│   ├── trading.metta         ← Trading logic rules
│   └── ...                   ← 27 rule files total
├── historical/               ← Permanent archive (market milestones, events)
├── memory.parquet            ← MemoryStore (timestamped facts, BM25 searchable)
├── cache.parquet             ← Tool result cache (TTL-based, hash-chained)
├── chat.parquet              ← Conversation history (encrypted, hash-chained)
├── profile.json              ← User profile + encrypted API keys
├── skills/                   ← 60 SKILL.md files (hot-reloadable)
├── plugins/                  ← Custom tool plugins (hot-reloadable)
├── trading/                  ← Spot trade history (hash-chained Parquet)
├── futures/                  ← Futures trade history (hash-chained Parquet)
└── tools_config.json         ← API tool definitions (JSON/YAML, hot-reloadable)
```

---

## Getting Started

### Prerequisites

- **Rust** 1.75+
- **Node.js** 18+ (for the frontend)

### Build

```bash
cd qor-rs
cargo build --release
```

### Run Tests

```bash
# All 2,209 tests
cargo test --workspace
```

### Run the Server

```bash
# Full runtime — MORK + PLN + tools + trading + chat + SSE streaming
cargo run --release -p qor-server

# With GPU inference (Vulkan)
cargo run --release -p qor-server --features gpu
```

### CLI

```bash
# Interactive chat with full knowledge + reasoning pipeline
cargo run --release -p qor-cli
```

---

## Philosophy

QOR is built on the belief that AGI requires more than scaling language models:

1. **Neuro-symbolic fusion** — Neural networks for pattern recognition, PLN + MeTTa for logical reasoning. Neither alone is sufficient.
2. **Memory is not context window** — Real intelligence needs persistent, growing, decaying memory wired into computation (CMS three-speed).
3. **Reasoning is not prompting** — PLN gives the system actual deduction, induction, and abduction with tracked evidence stamps.
4. **Language is not just LLM output** — The verbalizer proves that template-based NLG with confidence hedging can handle 60-80% of responses with zero neural compute.
5. **Personality is not system prompt** — An emotional soul backed by MORK that evolves through interaction creates genuine rapport.
6. **Perception is not API calls** — Direct CLIP vision, streaming audio, and AuraFace recognition feed cognition.
7. **One system, not a pipeline** — Brain, MORK, PLN, senses, soul, and actions run as one unified process.
8. **Offline-first** — Single compiled binary, runs forever without internet. No cloud dependency at inference time.
9. **Zero hallucination** — Never guess. Always know if you know. Market queries hit real APIs, not training data.
10. **Knowledge as s-expressions** — MORK stores everything as s-expressions that MeTTa rules can reason over. The database IS the reasoning substrate.

---

## Roadmap

- [x] Pure Rust AGI engine — 35 crates, 2,209 tests, 100K+ lines, zero C++ FFI
- [x] MORK hypergraph backend — PathMap trie + HashMap indexes + s-expression persistence
- [x] 27 MeTTa rule files — schema, knowledge, trading, security, soul, hands, ingestion, cleanup
- [x] PLN probabilistic reasoning — 9 truth functions, evidence stamps, bounded inference engine
- [x] PLN Verbalizer — 30+ predicate formatters, 6 explanation templates, confidence hedging
- [x] Graph Formatter — 20+ query patterns, natural language from edges (< 50ms)
- [x] Multi-tier response pipeline — Tiers 1-4 + Tier 2.5, 60-80% instant coverage
- [x] NGRE — Neural Graph Reasoning Engine (4-layer: Mamba + Graph + Grover + Cross-Attn)
- [x] Quantum-Inspired Search — Grover O(√N) interference search on embeddings
- [x] Emotional soul system — mood, trust, attachment, 16 evolution patterns, 5 DNA characters
- [x] Multi-tenant SaaS — dual-key device authority, per-user isolation, AES-256-GCM
- [x] Autonomous agent hands — 5 hands, workflow engine, background delegation
- [x] AuraFace authentication — SCRFD + anti-spoof + GlintR100, pure Rust
- [x] CLIP vision awareness — 50 scene labels, change detection, scene→graph integration
- [x] Prediction market trading — Polymarket + 6 signals + Kelly sizing
- [x] 5-stage security pipeline — intent, content, privacy, rate limit, confirm (152 tests)
- [x] CORTEX sequential engine — S4 + CfC + Fusion, brain-inspired architecture
- [ ] Distributed swarm intelligence
- [ ] On-device mobile runtime
- [ ] Hardware acceleration (Vulkan compute)
- [ ] Federated learning across instances

---

## License

MIT License. See [Cargo.toml](qor-rs/Cargo.toml) for details.

---

<p align="center">
  <em>Built by one person. Reaching for AGI.</em>
</p>
