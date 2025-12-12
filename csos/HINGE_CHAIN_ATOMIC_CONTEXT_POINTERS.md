# Hinge Chain: Context Pointers ↔ Atomic Context ↔ Atomic Concept

## Purpose

Standardize how we link everything via an alternating chain:

## Alternation rule (the chain)

Context Pointer → Atomic Context → Hinge → Atomic Concept → Hinge → Atomic Context → Hinge → …

This gives you a single traversable graph where every “meaning unit” has a receipt and every abstraction is explicitly hinged to its sources.

---

## Node types

- **CTX_PTR (Context Pointer)**: a resolvable pointer to evidence (local file path, screenshot, log entry, URL, hash, ID).
- **ATOMIC_CTX (Atomic Context)**: an atomic, evidence-backed slice of context (small enough to re-verify; big enough to act on).
- **HINGE**: the *bridge/gate* that transforms or links contexts/concepts (rule, mapping, dependency, translation, justification step).
- **ATOMIC_CONCEPT**: a minimal abstraction derived from one or more ATOMIC_CTX nodes (kept falsifiable and small).

---

## Edge types (typed edges)

- **points_to**: CTX_PTR → evidence (file/image/log/URL)
- **grounds**: evidence/CTX_PTR → ATOMIC_CTX (this context is grounded in that receipt)
- **hinges_to**: ATOMIC_CTX → HINGE → ATOMIC_CONCEPT (transformation/link)
- **instantiates**: ATOMIC_CONCEPT → ATOMIC_CTX (concept re-applied to generate a new atomic context)
- **supports / contradicts**: evidence or context shifts confidence
- **requires_proof**: declares verification requirement before promotion
- **promotes / demotes / retracts**: canonical state changes (must follow Evidence Policy)

---

## Alternation rule (the chain)

We always alternate:

1) **Pointer** (where the receipt lives)  
2) **Atomic Context** (what the receipt means, minimally)  
3) **Hinge** (how we translate/link)  
4) **Atomic Concept** (the smallest abstraction)  
5) **Hinge** (how we apply/route)  
6) **Atomic Context** (the resulting actionable slice)  
… repeat

**Why:** this prevents “concept drift” and blocks hallucinated abstractions from becoming governing edges.

---

## Minimal templates

### CTX_PTR template

```yaml
id: CTX_PTR:<slug>
type: CTX_PTR
target:
  kind: [file|image|log|url|db_row|commit]
  locator: "<canonical path or URL>"
  hash: "<optional sha256>"
evidence_tier: 0|1|2|3|4
notes: "<optional>"
```

### ATOMIC_CTX template

```yaml
id: ATOMIC_CTX:<slug>
type: ATOMIC_CTX
grounded_by: [CTX_PTR:<slug>, ...]
claim: "<one falsifiable statement>"
scope: "<where it applies>"
time_tag: "<only if time is explicitly relevant>"
status: [PROVISIONAL|EVIDENCE-backed|RETRACTED]
test_plan: "<required if PROVISIONAL>"
```

### HINGE template

```yaml
id: HINGE:<slug>
type: HINGE
function: "<bridge/gate/translation rule>"
input: [ATOMIC_CTX:<slug> | ATOMIC_CONCEPT:<slug>]
output: [ATOMIC_CONCEPT:<slug> | ATOMIC_CTX:<slug>]
guardrails:
  evidence_required: true
  time_conditional: true
```

### ATOMIC_CONCEPT template

```yaml
id: ATOMIC_CONCEPT:<slug>
type: ATOMIC_CONCEPT
derived_from: [HINGE:<slug>, ...]
definition: "<small, testable abstraction>"
counterexample: "<what would falsify it>"
status: [PROVISIONAL|EVIDENCE-backed|RETRACTED]
```

---

## Promotion rule (ties to Evidence Policy)

- No **ATOMIC_CONCEPT** is governing until it is **EVIDENCE-backed** (Tier 0–2 pointers).
- Any contradiction by higher-tier evidence triggers **demotion** or **retraction** with a receipt.

---

## Example (real artifacts in your workspace)

```yaml
CTX_PTR:ai_orchestrator_flow_png:
  type: CTX_PTR
  target:
    kind: image
    locator: Downloads/_ByType/Images/ai_orchestrator_flow.png
  evidence_tier: 0
```

```yaml
ATOMIC_CTX:orchestrator_has_feedback_loop:
  type: ATOMIC_CTX
  grounded_by: [CTX_PTR:ai_orchestrator_flow_png]
  claim: "The orchestration system contains an explicit feedback loop that can amplify correction overhead."
  status: PROVISIONAL
  test_plan: "OCR the image and extract the labeled phases + feedback arrow; link to invariant graph."
```

```yaml
HINGE:feedback_gain_to_saturation_risk:
  type: HINGE
  function: "Map feedback-loop gain → correction-token amplification risk"
  input: [ATOMIC_CTX:orchestrator_has_feedback_loop]
  output: [ATOMIC_CONCEPT:feedback_gain_increases_saturation_risk]
  guardrails:
    evidence_required: true
    time_conditional: true
```

```yaml
ATOMIC_CONCEPT:feedback_gain_increases_saturation_risk:
  type: ATOMIC_CONCEPT
  derived_from: [HINGE:feedback_gain_to_saturation_risk]
  definition: "Higher feedback gain increases correction-token autocatalysis unless governed by evidence/policy."
  counterexample: "If a high-gain loop demonstrably reduces corrections while increasing reference density."
  status: PROVISIONAL
```

---

## Canon ledger files (append-only)

- **CTX pointers only**: `Downloads/_ByType/Docs/CTX_PTR_LEDGER.jsonl`
- **Hinge chain nodes** (`ATOMIC_CTX`, `HINGE`, `ATOMIC_CONCEPT`): `Downloads/_ByType/Docs/HINGE_CHAIN_LEDGER.jsonl`

Rule: The example chain in `Downloads/_ByType/Docs/INVARIANT_GRAPH.mermaid` is considered *traversable* only when the referenced IDs exist in these ledgers.
