<p align="center">
<img width="1180" height="664" alt="image" src="https://github.com/user-attachments/assets/8bf543c6-775f-4c85-9a4e-178c1222a3b4" />

</p>

<h1 align="center">QORA — Self-Learning AGI System</h1>

<p align="center">
  <strong>A brain that learns, remembers, reasons, sees, hears, speaks, and trades — all in one binary.</strong>
</p>

<p align="center">
  <a href="#architecture">Architecture</a> &bull;
  <a href="#features">Features</a> &bull;
  <a href="#the-35-crate-rust-engine">Rust Engine</a> &bull;
  <a href="#getting-started">Getting Started</a> &bull;
  <a href="#license">License</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Rust-35_crates-orange?logo=rust" />
  <img src="https://img.shields.io/badge/Tests-2%2C209_passing-brightgreen" />
  <img src="https://img.shields.io/badge/Python-67K_lines-blue?logo=python" />
  <img src="https://img.shields.io/badge/License-MIT-green" />
  <img src="https://img.shields.io/badge/C++_FFI-ZERO-red" />
</p>

---

## What Is QOR?

QOR (Qora Neuran AI) is **not** another chatbot wrapper. It is a self-contained AGI system where:

- A **Brain** (3B parameter model with SmolLM3 donor weights) knows *how* to think
- A **Memory Database** wired into the neural layers knows *what* to think about
- **Knowledge** grows and decays organically — the system learns from every conversation, forgets what's stale, and reasons over what it knows
- **Senses** (vision, hearing, face recognition) feed perception directly into cognition
- **Actions** (trading, web browsing, tool use, autonomous agents) let it act on the world

```
┌──────────────────────────────────────────────────────────────┐
│                        QOR SYSTEM                            │
│                                                              │
│   ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│   │  BRAIN   │  │  MEMORY  │  │  SENSES  │  │  SOUL    │   │
│   │ 3B model │←→│ Graph +  │←→│ Vision + │←→│ Emotion +│   │
│   │ CMS +    │  │ Parquet +│  │ Voice +  │  │ Trust +  │   │
│   │ Self-Mod │  │ PLN      │  │ Face     │  │ Persona  │   │
│   └──────────┘  └──────────┘  └──────────┘  └──────────┘   │
│         │              │              │              │        │
│   ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│   │  CORTEX  │  │  TOOLS   │  │  HANDS   │  │ TRADING  │   │
│   │ S4 + CfC │  │ 50+ APIs │  │ 5 Agents │  │ Spot +   │   │
│   │ Liquid   │  │ Browser  │  │ Workflow  │  │ Futures  │   │
│   │ Neurons  │  │ Skills   │  │ Engine   │  │ Predict  │   │
│   └──────────┘  └──────────┘  └──────────┘  └──────────┘   │
└──────────────────────────────────────────────────────────────┘
```

**One process. One binary. No microservices. No cloud dependency.**

---

## Architecture

### The Brain — Continuum Memory System (CMS)

Unlike standard transformers that forget everything between sessions, QOR's brain has **three-speed memory wired into every layer**:

| Speed | Update Frequency | Purpose | Analogy |
|-------|-----------------|---------|---------|
| **Fast** | Every token | Working memory, immediate context | Sensory buffer |
| **Medium** | Every 16 tokens | Patterns, habits, recurring themes | Short-term memory |
| **Slow** | Every 64 tokens | Stable knowledge, personality | Long-term memory |

Each `QORBlock` = Attention + Self-Modifying Neurons + CMS. The self-modifying neurons use **CfC liquid neurons** (Nature Machine Intelligence 2022) — continuous-time dynamics with persistent hidden state that adapt during inference.

### CORTEX — Sequential Intelligence Engine

```
C — Continuous-time reflex     (CfC liquid neurons / Amygdala)
O — Observation of deep history (S4 State-Space / Neocortex)
R — Reasoning layer            (Fusion / Prefrontal Cortex)
T — Temporal memory            (Hidden states / Hippocampus)
E — Execution decision         (Output / Cerebellum)
X — eXtended architecture     (Quantum search / Basal Ganglia)
```

S4 state-space models capture long-range dependencies (thousands of timesteps) while CfC liquid neurons provide fast reflexive responses. The fusion layer combines both for real-time decision making.

### Zero-Hallucination Answer Pipeline

QOR **never guesses**. Every answer is grounded in real data:

```
User Question
     │
     ├── TIER 1: Template Match (< 5ms) ──→ 40+ instant patterns
     ├── TIER 2: Graph Formatter (< 50ms) ──→ Natural language from knowledge graph
     ├── TIER 2.5: PLN Verbalized (< 10ms) ──→ High-confidence inferred knowledge
     ├── TIER 3: Cache Hit (< 100ms) ──→ Recent tool results
     └── TIER 4: Full Pipeline (1-30s) ──→ 8 context sources + LLM synthesis
            │
            ├── Source 0: Fast memory (in-memory HashMap)
            ├── Source 1: Knowledge Graph (4-pass: user facts → keywords → semantic beam → deep)
            ├── Source 2: MemoryStore (Parquet + BM25 scoring)
            ├── Source 3: CacheStore (TTL-based tool results)
            ├── Source 4: Live tool execution (50+ APIs, on-demand)
            ├── Source 5: Episodic memory (Parquet + hash chain)
            ├── Source 6: Skill matching (60 bundled SKILL.md)
            ├── Source 7: Vision scene context (CLIP zero-shot)
            └── Source 8: MORK + PLN inferred reasoning
```

**60-80% of queries answered instantly** from Tiers 1-3. No LLM needed.

### PLN — Probabilistic Logic Networks

Native Rust implementation of OpenCog's PLN reasoning system. The knowledge graph doesn't just store facts — it **reasons over them**:

| Truth Function | What It Does |
|---------------|-------------|
| **Deduction** | A→B, B→C ∴ A→C |
| **Induction** | A→C, B→C ∴ A→B (shared effects) |
| **Abduction** | A→B, A→C ∴ B→C (shared causes) |
| **Modus Ponens** | A, A→B ∴ B |
| **Revision** | Merge independent evidence |
| **Negation** | ¬A from A |
| **Inversion** | B→A from A→B |
| **Equivalence→Implication** | A↔B ∴ A→B |
| **Transitive Similarity** | A~B, B~C ∴ A~C |

Every belief carries a **Simple Truth Value** (strength, confidence) with evidence stamps to prevent circular reasoning. High-confidence inferences (> 0.85) are verbalized into natural language templates — no LLM needed.

### Emotional Soul System

QOR isn't a stateless chatbot. It has persistent emotional state that evolves through every interaction:

- **Mood** — Current emotional baseline (decays toward neutral over time)
- **Trust** — Built through positive interactions, face logins, accurate answers
- **Attachment** — Grows with sustained engagement, affects greeting warmth
- **Empathy Mapping** — User sad → AI empathetic, user angry → AI calm anchor, user happy → AI celebratory
- **16 evolution patterns** — Personality adapts across 10 topic categories

### Multi-Tenant SaaS Architecture

Every user gets isolated state with **dual-key device authority**:

```
system_id = SHA-256(wallet_address + device_key)
enc_key   = PBKDF2(device_key + wallet_address, salt, 600K iterations)
```

- Wallet stays **100% offline** — nothing wallet-related on the server
- Challenge-response auth with EIP-191 signatures
- Per-user knowledge graph, memory, soul, face embeddings, voice profiles
- AES-256-GCM encryption at rest for all sensitive data

---

## Features

### Perception

| Feature | Implementation | Status |
|---------|---------------|--------|
| **Vision** | CLIP zero-shot scene classification (50 labels) | Pure Rust + ONNX |
| **Face Auth** | SCRFD detect → MiniFASNet anti-spoof → GlintR100 recognize | Pure Rust, no C++ |
| **Voice Input** | Non-blocking streaming audio capture (16kHz, 30s ring buffer) | Pure Rust |
| **Document Reading** | PDF + DOCX text extraction | Pure Rust |
| **Video Analysis** | Frame extraction → per-frame CLIP analysis | Pure Rust |

### Cognition

| Feature | Implementation | Status |
|---------|---------------|--------|
| **Knowledge Graph** | MORK-backed weighted directed graph with typed nodes | 153 tests |
| **PLN Reasoning** | 9 truth functions, priority-queue bounded inference | 24 tests |
| **Semantic Search** | TF-IDF + BM25 + node embeddings + cosine similarity | Hybrid RRF |
| **Episodic Memory** | Parquet + hash chain, timestamped recall | Tamper-evident |
| **TreeGate Router** | Complexity-aware routing (Template/Fast/Think/Cloud) | 52 tests |
| **5-Stage Security** | Intent → Content Safety → Privacy → Rate Limit → Confirm | 152 tests |

### Action

| Feature | Implementation | Status |
|---------|---------------|--------|
| **50+ Tools** | All free public APIs, no keys needed | Built-in |
| **5 Agent Hands** | Researcher, Collector, Predictor, Trader, Browser | Autonomous |
| **Spot Trading** | Binance spot with DCA, trailing stop, partial TP | Demo + Live |
| **Futures Trading** | USDT-M perpetuals, long + short, leverage-aware | Demo + Live |
| **Polymarket** | Prediction market trading with 6 signal sources | Kelly sizing |
| **Web Browser** | Headless Chromium via Playwright | Screenshots + text |
| **60 Skills** | Markdown-based skill injection (no code) | Hot-reloadable |
| **25 Extensions** | MCP connectors (GitHub, Slack, PostgreSQL, AWS...) | TOML templates |

### Expression

| Feature | Implementation | Status |
|---------|---------------|--------|
| **Emotional TTS** | Multi-backend voice synthesis with emotion tags | ElevenLabs + local |
| **3D Avatar** | VRM model with emotion mapping, lip sync, outfit switching | Three.js in browser |
| **5 DNA Characters** | Mila, Nova, Vera, Enron, Rex — each with unique personality | Onboarding selection |
| **Video Generation** | LLM script → TTS narration → image frames → FFmpeg → .mp4 | Offline pipeline |

---

## The 35-Crate Rust Engine

The entire system is being ported to pure Rust — **zero C++ FFI dependencies**. RocksDB replaced with redb, HuggingFace tokenizers replaced with pure Rust BPE.

```
qor-rs/
├── qor-config        — Unified configuration system
├── qor-cortex        — Brain: S4 + CfC + Fusion sequential intelligence
├── qor-model         — Neural architecture: QORBlock + SelfMod + CMS
├── qor-tokenizer     — Pure Rust BPE (SmolLM3 128K vocab)
├── qor-graph         — Knowledge graph: MORK + HNSW + Hebbian learning
├── qor-knowledge     — PLN reasoning + verbalizer + knowledge base
├── qor-search        — TF-IDF + BM25 vector search
├── qor-reasoning     — Hereditary KBQA + multi-hop decomposition
├── qor-confidence    — Confidence gate + surprise measurement
├── qor-treegate      — Answer orchestration + complexity routing
├── qor-soul          — Emotional personality graph
├── qor-avatar        — 3D avatar state + emotion + lip sync + video
├── qor-voice         — Emotional TTS + voice profiles
├── qor-faceauth      — SCRFD + anti-spoof + AuraFace recognition
├── qor-multimodal    — Vision + audio encoder bridges
├── qor-tools         — 50+ built-in tools + 60 skills + 25 extensions
├── qor-hands         — 5 autonomous agent hands + workflow engine
├── qor-trading       — Binance spot trading engine
├── qor-polymarket    — Prediction market trading + signals
├── qor-browser       — Headless Chromium automation
├── qor-guardrails    — 5-stage security pipeline
├── qor-integrity     — SHA-256 hash chains for tamper detection
├── qor-wallet        — EIP-191 signing + address recovery
├── qor-stores        — Parquet-based persistent stores
├── qor-storage       — MORK PathMap trie storage
├── qor-ingest        — Data ingestion pipelines
├── qor-continual     — Continual learning (surprise-gated)
├── qor-train         — Training pipeline (mixed precision, DDP)
├── qor-eval          — Evaluation (BLEU, ROUGE-L, perplexity)
├── qor-quant         — INT8 quantization
├── qor-runtime       — Orchestrator: cleanup, scheduling, lifecycle
├── qor-server        — HTTP server: 40+ endpoints, SSE streaming
├── qor-cli           — Interactive command-line interface
├── qor-mamba         — Mamba state-space model variant
└── qor-ngre          — Neural Graph Reasoning Engine
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
| qor-graph (petgraph) | 17 | ... | ... |

---

## How It Learns

QOR doesn't just respond — it **grows smarter with every interaction**.

### Conversation → Knowledge

```
User: "The capital of France is Paris"
  │
  ├── Knowledge Graph: france --has_capital--> paris (confidence: 1.0)
  ├── MemoryStore: timestamped fact entry
  └── Soul: topic category "geography" evolves personality
```

### Correction → Self-Healing

```
User: "No, that's wrong. The population is 67 million, not 65"
  │
  ├── Old fact: QUARANTINED (confidence → 0)
  ├── New fact: stored with high confidence
  └── Trust: slight decrease (AI was wrong)
```

### Observation → Understanding

```
CLIP sees: user drinking coffee in kitchen
  │
  ├── Graph: user --drinks--> coffee (source: clip_scene)
  ├── Graph: user --seen_in--> kitchen (source: clip_scene)
  └── Soul: evolves from "[scene observation] user drinks coffee"
```

### Reasoning → New Knowledge

```
PLN Deduction:
  smoking → cancer (0.87, 0.9)
  cancer → lung_disease (0.85, 0.85)
  ∴ smoking → lung_disease (0.74, 0.77)  ← NEW INFERRED FACT

PLN Revision (two independent sources agree):
  paris_population = 2.1M (source A, confidence 0.6)
  paris_population = 2.1M (source B, confidence 0.7)
  ∴ paris_population = 2.1M (revised confidence: 0.88)  ← STRONGER
```

### Forgetting — Organic Decay

```
Cleanup cycle (periodic):
  │
  ├── Live memory: entries > 7 days old → deleted
  ├── Graph edges: exponential confidence decay → GC below 0.1
  ├── CMS slow layers: W = W * 0.999 (makes room for new patterns)
  ├── Cache: entries past TTL → removed
  ├── Chat: sessions > 90 days → deleted
  └── Checkpoints: daily(7) → weekly(4) → monthly(12) → yearly(∞)
```

---

## Getting Started

### Prerequisites

- **Rust** 1.75+ (for the Rust engine)
- **Python** 3.10+ (for the Python codebase)
- **Node.js** 18+ (for the frontend)

### Build the Rust Engine

```bash
cd qor-rs
cargo build --release
```

### Run the Python Runtime

```bash
# First-time setup
python -m qor setup

# Load SmolLM3-3B donor weights
python -m qor load-donor

# Full runtime (tools + knowledge + trading + chat)
python -m qor run --size qor3b --checkpoint checkpoints/qor3b.pt
```

### Run Tests

```bash
# Rust — all 2,209 tests
cd qor-rs
cargo test --workspace

# Python — full integration (115 checks)
python scripts/test_full_binary.py
```

### Key Commands

```bash
# Interactive chat with full knowledge pipeline
python -m qor run --size qor3b --checkpoint checkpoints/qor3b.pt

# REST API server
python -m qor serve

# Knowledge graph operations
python -m qor graph --action stats
python -m qor graph --action semantic-query --query "what causes lung disease?"

# Continual learning
python -m qor learn --checkpoint checkpoints/qor3b.pt
python -m qor watch --checkpoint checkpoints/qor3b.pt  # auto-learn new files

# Build multimodal checkpoint (SigLIP + Whisper + SmolLM3)
python -m qor build-multimodal
```

---

## Data Architecture

All runtime data is self-contained under a single directory:

```
qor-data/
├── checkpoints/          ← Model snapshots (daily/weekly/monthly/yearly rotation)
├── knowledge/
│   ├── graph.rocksdb/    ← Knowledge graph (entity → predicate → entity)
│   └── *.txt, *.md       ← Knowledge base documents
├── historical/           ← Permanent archive (market milestones, events)
├── memory.parquet        ← MemoryStore (timestamped facts, BM25 searchable)
├── cache.parquet         ← Tool result cache (TTL-based)
├── chat.parquet          ← Conversation history (encrypted at rest)
├── profile.json          ← User profile + encrypted API keys
├── skills/               ← 60 SKILL.md files (hot-reloadable)
├── plugins/              ← Custom tool plugins (hot-reloadable)
├── trading/              ← Spot trade history (hash-chained Parquet)
├── futures/              ← Futures trade history (hash-chained Parquet)
└── tools_config.json     ← API tool definitions
```

Every Parquet store uses **SHA-256 hash chains** for tamper detection. Sensitive data is encrypted with **AES-256-GCM**. The `verify` command checks integrity across all stores.

---

## DNA Characters

QOR ships with 5 distinct AI personalities, each with unique voice, appearance, and behavioral traits:

| Character | Archetype | Symbol | Gender | Personality |
|-----------|-----------|--------|--------|-------------|
| **Mila** | The Modest | ○ | Female | Gentle, thoughtful, observant |
| **Nova** | The Emotional | ◯ | Female | Expressive, empathetic, warm |
| **Vera** | The Professional | ◆ | Female | Precise, reliable, composed |
| **Enron** | The Witty Sharp | ↯ | Male | Quick, clever, analytical |
| **Rex** | The Motivator | ▲ | Male | Energetic, encouraging, bold |

Each character includes VRM 3D models with multiple outfits, unique voice samples, and personality graphs that influence how the soul evolves through conversation.

---

## Trading Intelligence

QOR includes autonomous trading engines for spot, futures, and prediction markets:

### Spot + Futures (Binance)
- Multi-timeframe technical analysis (weekly → 5min)
- AI-driven entry/exit decisions with confluence scoring
- DCA (dollar cost averaging) at support levels
- Trailing stop loss with ATR + support ratcheting
- Partial take profit with break-even SL after TP1
- Funding rate awareness for futures positions
- **Demo mode by default** — testnet trading, opt-in to live

### Prediction Markets (Polymarket)
- 6 independent signal sources: Weather, Sports, Crypto, News (GDELT), Aggregator (Metaculus + Manifold), Whale tracking
- Kelly criterion position sizing
- Edge detection with copy trader consensus
- Historical backtesting with equity curves and Sharpe ratios

---

## Security

### 5-Stage Pipeline

```
Query ──→ Intent Verification
              │
          Content Safety (toxicity, PII, injection)
              │
          Privacy Rules (per-user data isolation)
              │
          Rate Limiting (per-tool, per-user)
              │
          User Confirmation (destructive actions)
              │
          ✅ Approved
```

### Dual-Key Device Authority
- **Device key** (32 bytes, on device) + **wallet signature** (EIP-191) = both required
- Challenge-response authentication with 5-minute nonces
- Per-user AES-256-GCM encrypted data vaults
- Agent isolation: swarm agents get scoped temp storage, not user memory

### Tamper-Evident Storage
- SHA-256 hash chains on all Parquet stores
- Each row's hash depends on the previous row
- `verify` command walks the full chain to detect tampering

---

## Philosophy

QOR is built on the belief that AGI requires more than scaling language models:

1. **Memory is not context window** — Real intelligence needs persistent, growing, decaying memory wired into computation
2. **Reasoning is not prompting** — PLN gives the system actual logical inference with tracked evidence
3. **Personality is not system prompt** — An emotional soul that evolves through interaction creates genuine rapport
4. **Perception is not API calls** — Direct vision, hearing, and face recognition feed cognition
5. **One system, not a pipeline** — Brain, memory, senses, soul, and actions run as one unified process
6. **Offline-first** — Build once with internet, run forever without it. No cloud dependency at inference time
7. **Zero hallucination** — Never guess. Always know if you know. Market queries hit real APIs, not training data

---

## Roadmap

- [x] Python prototype — all features working (67K lines)
- [x] Rust port — 35 crates, 2,209 tests, 100K+ lines
- [x] PLN probabilistic reasoning engine
- [x] Emotional soul system
- [x] Multi-tenant SaaS architecture
- [x] Autonomous agent hands
- [x] Face authentication (AuraFace)
- [x] CLIP vision awareness
- [x] Prediction market trading
- [x] 5-stage security pipeline
- [ ] MORK Space reasoning (MeTTa integration)
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
