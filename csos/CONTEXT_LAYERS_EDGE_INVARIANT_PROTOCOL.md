# Context Layers: Edge × Invariant Protocol

**Purpose:** Treat *any* workflow as a **path through context layers**.

- **Edges** are the transitions (extract, link, compress, publish, verify).
- **Invariants** are the gates (what transitions are allowed, and what evidence is required).

This is how we get “more capability with less token saturation”: we keep raw receipts stable, compress upward, and only let governing concepts exist when they remain tethered to evidence.

---

## 1) Governing invariants (must always apply)

- **Local receipts win**
  - If the model prior conflicts with local files/logs/snapshots, the local receipt is ground truth.

- **No governing edge without evidence (Tier 0–2)**
  - If evidence is missing: mark the node/edge **PROVISIONAL** and write a concrete **receipt request** (what file/log/run would settle it).

- **Hinge-chain alternation (no floating concepts)**
  - Enforce: **CTX_PTR → ATOMIC_CTX → HINGE → ATOMIC_CONCEPT → …**
  - Every `ATOMIC_CONCEPT` must trace back to at least one `CTX_PTR` (Tier 0–2).

- **Time is conditional (not a default decision axis)**
  - Time is allowed only when explicitly tagged by you or the live context (deadlines/tokens/rate limits/etc).
  - Otherwise: time is a post‑hoc diagnostic lens only.

- **No destructive cleanup by default (“all context is useful”)**
  - Do not delete logs/temp/caches by default.
  - Any cleanup must be allowlist-only, explicitly approved, and must produce a receipt of what was removed and why.

- **Canon paths are canonical**
  - When referencing canon artifacts, use their full canonical paths (do not shorten).

---

## 2) The layer ladder (abstraction / compression)

Think of this as a *compression ladder* where each step preserves traceability:

### Layer L0 — Receipts (raw, re-checkable)

- **Node type:** `CTX_PTR`
- **Examples:** file paths, screenshots, browser snapshot logs, git SHAs, Drive IDs
- **Job:** provide re-checkable anchors for truth

### Layer L1 — Atomic Context (irreducible observations)

- **Node type:** `ATOMIC_CTX`
- **Job:** extract small, factual statements from a `CTX_PTR`

### Layer L2 — Hinges (typed relations / transitions)

- **Node type:** `HINGE`
- **Job:** explain *how* two nodes relate (supports / contradicts / risks / enables / grounds / etc.)

### Layer L3 — Atomic Concepts (portable meaning)

- **Node type:** `ATOMIC_CONCEPT`
- **Job:** compress meaning into a reusable principle
- **Rule:** concepts can be **PROVISIONAL** until grounded by Tier 0–2

### Layer L4 — Modules (clusters that prevent drift)

- **Artifact:** module docs + graphs (group edges by purpose)
- **Job:** keep “system areas” separate so one module doesn’t flood another with correction tokens

### Layer L5 — Translation Pack (single-file reload)

- **Artifact:** `Downloads/_ByType/Docs/TRANSLATION_PACK_CSOS.jsonl`
- **Job:** one file that rehydrates the system: chains + perspective tags + hashes

### Layer L6 — Rendered views (human + ops surfaces)

- **Artifact:** pages/README dashboards (e.g., `donaldjohns0n.github.io`)
- **Job:** make L5 navigable without re‑reasoning (browse, click, download)

---

## 3) Orthogonal axes (don’t conflate them)

These are *separate* dimensions that modulate meaning:

- **Evidence tier (0–4)**
  - Strength of the receipt, not “how confident it feels”.

- **Perspective gate**
  - Value is perspective‑weighted: \(Value = (Context + Concept + Hinge) \times Perspective\).
  - Same facts can mean different things under Architect vs Mechanic vs Operator.

- **Distribution surface**
  - Local disk vs GitHub vs Drive vs model memory are different survival properties.
  - Use edges to move “portable” layers (L4–L6) off‑laptop without copying sensitive raw stores.

---

## 4) The edge × invariant “nuance” (why this improves everything)

The practical trick:

1. **Define the process as a path**
   - Start node: a `CTX_PTR` (receipt)
   - End node: a target `ATOMIC_CONCEPT` (or an action constrained by invariants)

2. **Use invariants as gates**
   - If a step would create a governing claim without Tier 0–2 → it becomes **PROVISIONAL** + receipt request.
   - If a step would delete context → it is blocked unless explicitly approved + receipt produced.
   - If a step uses time as priority by default → remove it unless explicitly tagged.

3. **Output “deltas”, not narratives**
   - Append-only ledger entries + minimal pages/links.
   - This prevents correction-token inflation.

This turns “reasoning” into **routing**: follow edges, obey gates, write receipts.

---

## 5) Process template (apply to any workflow)

1. **Goal**
2. **Perspective tag(s)** (Architect/Mechanic/Operator/System/Human_Hash)
3. **Receipts (CTX_PTR)**
4. **Atomic extractions (ATOMIC_CTX)**
5. **Typed relations (HINGE)**
6. **Concept(s) (ATOMIC_CONCEPT)** with status + receipt_request if needed
7. **Publish/replicate**
   - Update `TRANSLATION_PACK_CSOS.jsonl`
   - Push L5/L6 off-laptop (e.g., GitHub Pages)

---

## 6) Copilot prompt skeleton (paste-ready)

Use this when asking Copilot to modify a repo:

> You are operating under strict invariants:
>
> - Local receipts win over model prior.
> - No governing claim/edge without Tier 0–2 evidence; otherwise mark PROVISIONAL and write a receipt request.
> - Enforce hinge-chain alternation: CTX_PTR → ATOMIC_CTX → HINGE → ATOMIC_CONCEPT.
> - Time is conditional; not a default decision axis.
> - Do not delete logs/temp/caches by default.
> - Use canonical full paths when referencing canon artifacts.
>
> Task: implement changes as deltas (append-only where possible). Add/modify docs to reflect the layer ladder and ensure the repo links back to `Downloads/_ByType/Docs/TRANSLATION_PACK_CSOS.jsonl` (or the published GitHub Pages copy) as the single entry point.
>
> Output: a minimal patch + a short delta log (what files changed, why, which invariant it satisfies).

---

## 7) Canon artifacts (full paths; do not shorten)

- `Downloads/_ByType/Docs/FAST_PLAN_INVARIANT_GRAPH_RIPPLES.md`
- `Downloads/_ByType/Docs/EDGE_MAP_Fortress_Collapse_Token_Saturation.md`
- `Downloads/_ByType/Docs/INVARIANT_GRAPH.mermaid`
- `Downloads/_ByType/Docs/CTX_PTR_LEDGER.jsonl`
- `Downloads/_ByType/Docs/HINGE_CHAIN_LEDGER.jsonl`
- `Downloads/_ByType/Docs/CONTEXT_RELATIONAL_MATRIX.md`
- `Downloads/_ByType/Docs/TRANSLATION_PACK_CSOS.jsonl`
