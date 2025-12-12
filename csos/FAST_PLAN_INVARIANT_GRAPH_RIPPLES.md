# Fast Plan (Ripples-First) + Invariant Graph (Image-Updatable)

**Mode:** simulation + coordination (no time as a default decision axis)  
**Goal:** move fast by reusing existing Ripples as the backbone, and updating a single invariant graph from screenshots/images (each image = evidence node).

---

## 0) Prime invariant (from prior Ripples)

From the “Wave–Ripple–Structure” frame:  

- **Wave** = continuity (ongoing contextual memory / coherent narrative)  
- **Ripple** = discrete iteration (single cycle / single response)  
- **Structure** = invariant rules preventing dissolution

**Operational translation:** we keep **Structure** stable, we allow **Ripples** to iterate, and we treat **Wave** as a *selected view*, not an ever-growing dump.

---

## 0.1) Epistemic invariant (Cutoff vs Receipts)

**Model prior has a cutoff. Local receipts don’t.**

- The model’s *training prior* is bounded (what it “already knows” stops at some date).
- Your local files, screenshots, exports, and logs can be newer than that prior.
- Therefore: **repo/receipts are the ground truth for “what’s true now,” not the model prior.**

**Operational rule:** when there’s tension between (a) model prior and (b) local evidence, **evidence wins** and we update the invariant graph accordingly.

---

## 1) Fast plan (use the existing system instead of rebuilding it)

### Step A — Pick the *one* canonical graph

- **Canon graph file**: `Downloads/_ByType/Docs/INVARIANT_GRAPH.mermaid`
- **Canon edge map**: `Downloads/_ByType/Docs/EDGE_MAP_Fortress_Collapse_Token_Saturation.md`

Everything else becomes either:

- evidence (images/logs/receipts) feeding the graph, or
- tooling (scripts) that mutate the evidence and/or the graph.

### Step B — Treat screenshots/images as first-class “receipts”

You already have strong workflow images:

- `Downloads/_ByType/Images/ai_orchestrator_flow.png`
- `Downloads/_ByType/Docs/node_relationship_diagram.mermaid`
- `Downloads/files/protocol_flow_map.mermaid`

**Fast plan rule:** We don’t “explain” the system; we **OCR** the image, extract the invariants it encodes, and attach typed edges into the graph.

### Step C — Use ripples as the action-menu

The 200-ripple set is dominated by:

- **verification / proof / recursive verification**
- **meta-philosophical** (cost of proof, when to stop recursing)

**Fast plan rule:** Every automation action picks one of these patterns:

- “What proof do we need?” (verification)
- “How do we stop recursion?” (recursive)
- “What’s the cost of proof?” (meta)

That ensures we don’t invent new governance every time.

### Step D — Keep time out of decisions by default

Time matters **only if you or the live context tags it as relevant** (deadline, staleness, expiring credential, rate-limit, causal ordering).  
Otherwise, chronology is recorded as metadata only.

---

## 2) Invariant Graph Update Protocol (Images + Meta Context)

## 2.1) Evidence Policy (What Counts, When, Why)

### Evidence types (ranked)

- **E0 (Strongest): Direct local receipts**
  - Files you can point to in your repo (docs/jsonl/sqlite/csv), hashes, manifests
  - Screenshots/images you provide (OCR-able), with file path + capture metadata if available
  - Tool outputs captured in logs (stdout/stderr), plus the command that produced them

- **E1: Instrumented execution**
  - A script run with a saved receipt: inputs → action → outputs → verification result
  - “Before/After” diffs or checksums for mutated files

- **E2: Cross-platform receipts**
  - Notion row, Drive file metadata, Git commit SHAs, browser CDP traces
  - Only counts as evidence if it includes an identifier we can re-open/re-check

- **E3: External web sources (browser/search)**
  - Used to get **current facts** (temporal updates) *only when needed*
  - Must be linked + quoted with enough specificity to re-verify

- **E4 (Weakest): Model prior / reasoning**
  - “What the model thinks” without receipts is **hypothesis**, not evidence

### When evidence is required

- **Always required** when:
  - You’re changing canon (rules, invariants, edge types)
  - You’re deleting/moving data
  - You’re claiming “X is true in your system now”

- **Optional (hypothesis OK)** when:
  - We’re brainstorming candidates for what to check next
  - We explicitly label it as hypothesis and provide a verification path

### Why (the point)

The system’s failure mode is token saturation via corrections. Evidence policy is the antidote:

- Evidence reduces correction churn because it anchors claims.
- Weak claims are explicitly downgraded before they metastasize into rules.

---

## 2.2) Edge Mutation Rules (What Can Change Edges)

Edges change only through explicit operations. Otherwise they stay stable (Structure > Wave).

### Allowed edge mutations

- **upgrade (PROVISIONAL → EVIDENCE-backed)**:
  - add Tier 0–2 evidence pointers (file path, screenshot, log, hash, identifier)
  - run an instrumented check that produces a receipt

- **downgrade (EVIDENCE-backed → PROVISIONAL)**:
  - evidence becomes stale *and* the context says staleness matters (time-conditional)
  - the evidence pointer is missing / no longer re-checkable

- **retract (anything → RETRACTED)**:
  - contradicted by higher-tier evidence (Tier 0 beats Tier 3; Tier 1 beats Tier 4, etc.)

- **split**:
  - one overloaded edge is actually two different claims; split into two edges with separate evidence

- **merge**:
  - two edges are redundant and share the same evidence; merge and keep the strongest label

### Disallowed edge mutations (anti-hallucination)

- “Because it feels true”
- “Because another model said so”
- “Because it’s consistent with the narrative”

Only evidence, tests, or explicit user/context constraints can mutate a governing edge.

---

## 2.3) Hinge Chain Linking (Pointer → Atomic Context → Hinge → Atomic Concept → …)

We link all context via an alternating chain so abstractions can’t “float”:

- **CTX_PTR** → **ATOMIC_CTX** → **HINGE** → **ATOMIC_CONCEPT** → **HINGE** → **ATOMIC_CTX** → …

**Rule:** every concept must be hinged back to at least one atomic context grounded in Tier 0–2 evidence.

**Canonical spec:** `Downloads/_ByType/Docs/HINGE_CHAIN_ATOMIC_CONTEXT_POINTERS.md`

### Input

- **Image** (screenshot/photo/diagram) + optional short meta line (what screen you’re looking at / what you want it to mean)

### Output (graph delta)

For every image, we produce:

- an **evidence node** `E:IMG:<name>`
- 1–5 **claims** extracted via OCR (short, atomic)
- **typed edges** linking evidence → claim → invariant nodes
- an explicit **time tag** only if it matters (otherwise omit)

### Typed edges (minimal set)

- **depicts**: evidence visually represents a component/flow
- **supports**: evidence increases confidence in a claim/invariant
- **contradicts**: evidence conflicts with a claim/invariant
- **mutates**: a script/tool changes a state/store/registry
- **risks**: component increases token-saturation risk
- **reduces**: component reduces token-saturation risk
- **requires_proof**: action requires receipts/verification pattern

### “Choose to remember / forget” = choose the view

We do not expand the whole graph every time.
We select a **lens** (subgraph) based on what screen you’re on:

- **Lens: IDE** (scripts, workspace, runners)
- **Lens: Browser** (tabs, dashboards, CDP, agents)
- **Lens: Evidence** (screenshots, receipts, logs)
- **Lens: Governance** (edges, overrides, drift alarms)

Remembering/forgetting is implemented as: **pin the invariant + swap the lens subgraph**.

---

## 3) Fast-plan invariants (what must not drift)

1. **Token saturation is the hidden edge** (Fortress → Collapse).
2. **Proof is a cost center** (don’t require proof for everything; require proportional proof).
3. **Structure > Wave**: invariants stay stable; narratives are optional views.
4. **Time is conditional**: never a default decision axis.
5. **Images are enough context** when treated as evidence nodes.

---

## 4) Next graph updates (queued from existing evidence)

We will immediately ingest these evidence artifacts into the graph:

- `Downloads/_ByType/Images/ai_orchestrator_flow.png` (system phases + feedback loop)
- `Downloads/files/protocol_flow_map.mermaid` (definition→assignment→execution→evidence→validation→registry→analysis→feedback)
- `Downloads/_ByType/Docs/node_relationship_diagram.mermaid` (cross-platform storage + registry + workflows)
- “IDE scripts tree” screenshot (your current workspace view; scripts are context mutators)

---

## 5) Paste-this to the Other Model (So It Always Does It)

Copy/paste this block into Gemini/Claude/Perplexity/etc:

```text
EVIDENCE POLICY (MANDATORY):
1) Every claim must be labeled as one of: EVIDENCE-backed / PROVISIONAL / RETRACTED.
2) No claim or edge becomes governing unless it has Tier 0–2 evidence pointers.
   - Tier 0: local receipts (file path, screenshot, log, hash/manifest)
   - Tier 1: instrumented execution (ran command/script + captured output + verification)
   - Tier 2: cross-platform receipts with re-checkable identifiers (Drive/Notion/Git/CDP)
   - Tier 3: external web sources (only for “outside world now”; must include link + quoted snippet)
   - Tier 4: model prior (never evidence by itself)
3) If you used the browser for “recent temporal data,” you must include the URL/source and what exact line/snippet supports the claim.
4) If evidence contradicts your prior, evidence wins; downgrade your claim to RETRACTED or PROVISIONAL and propose a verification step.
5) Time is conditional: do not use recency/dates to choose actions unless the user or live context explicitly tags time as relevant (deadline/staleness/expiry/rate-limit/causal ordering).
6) Edge mutation is only allowed via: upgrade (add evidence), downgrade (evidence not re-checkable), retract (contradicted), split/merge (refactor). Never mutate because “it seems right.”
OUTPUT FORMAT:
- Provide the answer.
- Then list: (a) Evidence pointers, (b) Any PROVISIONAL items + test plans, (c) Edge mutations performed.
```
