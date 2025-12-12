# Context Edge Remap (Module Separation + Hinge Chains)

**Purpose:** Re-map “all context so far” into a small number of modules so edges stop collapsing into a single blob.  
**Rule:** No floating concepts: every governing edge must trace through a hinge chain grounded in receipts.

---

## Module 0 — Canon Structure (what must remain stable)

**What it is:** the minimal set of artifacts that define “how we decide what’s true” (Structure > Wave).

**Primary CTX_PTRs (Tier 0):**
- `Downloads/_ByType/Docs/EDGE_MAP_Fortress_Collapse_Token_Saturation.md`
- `Downloads/_ByType/Docs/FAST_PLAN_INVARIANT_GRAPH_RIPPLES.md`
- `Downloads/_ByType/Docs/INVARIANT_GRAPH.mermaid`
- `Downloads/_ByType/Docs/HINGE_CHAIN_ATOMIC_CONTEXT_POINTERS.md`
- `Downloads/_ByType/Docs/CTX_PTR_LEDGER.jsonl`
- `Downloads/_ByType/Docs/CONTEXT_RELATIONAL_MATRIX.md`

**Hinge chain (structure stability):**
- `CTX_PTR: Downloads/_ByType/Docs/FAST_PLAN_INVARIANT_GRAPH_RIPPLES.md`
  → `ATOMIC_CTX:canon_requires_receipt_grounding`
  → `HINGE:enforces:no_governing_edge_without_evidence`
  → `ATOMIC_CONCEPT:evidence_policy_limits_correction_churn`

---

## Module 1 — Fortress → Collapse (Token Saturation dynamics)

**What it is:** the primary failure mode: correction tokens displace reference tokens until collapse.

**Grounding CTX_PTR (Tier 0):**
- `Downloads/_ByType/Docs/EDGE_MAP_Fortress_Collapse_Token_Saturation.md`

**Core hinge chain (mechanism):**
- `CTX_PTR: Downloads/_ByType/Docs/EDGE_MAP_Fortress_Collapse_Token_Saturation.md`
  → `ATOMIC_CTX:correction_tokens_can_displace_reference_tokens`
  → `HINGE:causes:context_window_saturation`
  → `ATOMIC_CONCEPT:fortress_controls_can_self_induce_collapse`

**Pipeline-induced sub-edge (proof/recursion as a factory):**
- `CTX_PTR: Downloads/_ByType/Docs/CONTEXT_RELATIONAL_MATRIX.md`
  → `ATOMIC_CTX:verification_loops_generate_additional_tokens`
  → `HINGE:risks:correction_token_factory`
  → `ATOMIC_CONCEPT:proof_cost_can_accelerate_token_saturation`

---

## Module 2 — Evidence Governance (anti-hallucination / anti-correction-churn)

**What it is:** the “receipts > debate” rule set and edge mutation rules that prevent drift and endless correction.

**Grounding CTX_PTR (Tier 0):**
- `Downloads/_ByType/Docs/FAST_PLAN_INVARIANT_GRAPH_RIPPLES.md` (Evidence Policy + Edge Mutation Rules)
- `Downloads/_ByType/Docs/INVARIANT_GRAPH.mermaid` (Invariant nodes I5/I6)

**Hinge chain (epistemic boundary):**
- `CTX_PTR: Downloads/_ByType/Docs/FAST_PLAN_INVARIANT_GRAPH_RIPPLES.md`
  → `ATOMIC_CTX:model_prior_is_bounded`
  → `HINGE:overridden_by:local_receipts`
  → `ATOMIC_CONCEPT:receipts_win_over_prior`

**Hinge chain (non-deletion stance):**
- `CTX_PTR: Downloads/.cursorrules`
  → `ATOMIC_CTX:do_not_delete_context_by_default`
  → `HINGE:prevents:evidence_loss`
  → `ATOMIC_CONCEPT:context_preservation_reduces_false_rewrites`

---

## Module 3 — Agent/Queue Surfaces (how systems “talk to each other”)

**What it is:** the actual pipes: JSONL queues, `.codex.yml`, browser actions, snapshots, logs. This is where coordination becomes real.

**Grounding CTX_PTRs (Tier 0/1):**
- `C:/Users/cardi/Git/DATA_INBOX/Other/.codex.yml` (agent instructions)
- `C:/Users/cardi/Git/DATA_INBOX/Databases/Ledgers/codex_prompt_queue.jsonl` (queue)
- `C:/Users/cardi/Git/DATA_INBOX/Data/JSONL/codex_prompt_queue.jsonl` (queue)
- `C:/Users/cardi/.cursor/browser-logs/*` (browser snapshot receipts)

**Hinge chain (queue → action → proof):**
- `CTX_PTR:FILE:C:/Users/cardi/Git/DATA_INBOX/Databases/Ledgers/codex_prompt_queue.jsonl`
  → `ATOMIC_CTX:prompts_are_enqueued_as_jsonl`
  → `HINGE:drives:browser_and_tool_actions`
  → `ATOMIC_CONCEPT:agent_coordination_is_a_loggable_pipeline`

**Hinge chain (queue corruption as a drift source):**
- `CTX_PTR:FILE:C:/Users/cardi/Git/DATA_INBOX/Databases/Ledgers/codex_prompt_queue.jsonl`
  → `ATOMIC_CTX:invalid_json_lines_can_exist_in_queue`
  → `HINGE:risks:processing_failure_or_hesitation`
  → `ATOMIC_CONCEPT:queue_integrity_is_a_governance_dependency`

---

## Module 4 — Execution Substrate (Docker / local runtime as receipt engine)

**What it is:** where actions are executed and where proofs can be reproduced (containers, volumes, logs).

**Grounding CTX_PTRs (Tier 0):**
- `Downloads/_ByType/Docs/Receipts/docker_info.txt`
- `Downloads/_ByType/Docs/Receipts/docker_ps_a.txt`
- `Downloads/_ByType/Docs/Receipts/docker_images.txt`
- `Downloads/_ByType/Docs/Receipts/docker_volume_ls.txt`
- `Downloads/_ByType/Docs/DOCKER_DESKTOP_CONTEXT_MAP.md`

**Hinge chain (execution → receipts):**
- `CTX_PTR: Downloads/_ByType/Docs/Receipts/docker_info.txt`
  → `ATOMIC_CTX:docker_desktop_is_available`
  → `HINGE:enables:instrumented_execution`
  → `ATOMIC_CONCEPT:local_execution_can_generate_tier0_receipts`

**Hinge chain (execution surface ↔ saturation risk):**
- `CTX_PTR: Downloads/_ByType/Docs/Receipts/docker_system_df.txt`
  → `ATOMIC_CTX:execution_artifacts_consume_local_disk`
  → `HINGE:risks:storage_pressure_and_logging_failure`
  → `ATOMIC_CONCEPT:infrastructure_limits_can_trigger_collapse_modes`

---

## Module 5 — Provenance Layer (.git as atomic context nodes)

**What it is:** `.git/*` is a verifiable causality graph (refs→commits→trees), plus logs for post-hoc audit.

**Grounding CTX_PTRs (Tier 0):**
- `Downloads/_ByType/Docs/GIT_ATOMIC_CONTEXT_NODES.md` (spec)
- `Downloads/_ByType/Docs/Receipts/git_repos_with_dotgit.txt` (inventory)

**Hinge chain (provenance is machine-mappable):**
- `CTX_PTR: Downloads/_ByType/Docs/Receipts/git_repos_with_dotgit.txt`
  → `ATOMIC_CTX:multiple_git_repos_exist_locally`
  → `HINGE:enables:receipt_backed_provenance_queries`
  → `ATOMIC_CONCEPT:git_history_is_a_first_class_evidence_surface`

---

## Module 6 — Translation Fast-Track (MAP → PACK → TRANSLATE)

**What it is:** reduce correction churn by freezing a minimal IR (Translation Pack) and rendering outputs mechanically.

**Grounding CTX_PTR (Tier 1):**
- `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T00-03-03-936Z.log` (message submission receipt)

**Hinge chain (translation speedup):**
- `CTX_PTR: C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T00-03-03-936Z.log`
  → `ATOMIC_CTX:map_pack_translate_protocol_shared_in_chat`
  → `HINGE:reduces:second_pass_reasoning`
  → `ATOMIC_CONCEPT:translation_should_be_a_render_step_not_a_rethink`

---

## Module 7 — Recursive Verification (proof requirement mechanics)

**What it is:** instrumented verification framework that logs actions and proof state; useful but can become a recursion factory.

**Grounding CTX_PTRs (Tier 0/1):**
- `Downloads/scripts/recursive_verification_framework.py`
- `Downloads/_ByType/Docs/Receipts/recursive_verification_framework_sha256.txt`
- `https://drive.google.com/file/d/1YVW_l-_aGsKljJmHmClLRCw5orD_HkXv/view`

**Hinge chain (proof enforcement):**
- `CTX_PTR: Downloads/scripts/recursive_verification_framework.py`
  → `ATOMIC_CTX:verifier_marks_actions_unverified_without_execution_proof`
  → `HINGE:enforces:proof_before_promotion`
  → `ATOMIC_CONCEPT:instrumentation_prevents_false_success_claims`

**Hinge chain (recursion risk):**
- `CTX_PTR: Downloads/scripts/recursive_verification_framework.py`
  → `ATOMIC_CTX:recursive_checks_can_self_recur`
  → `HINGE:risks:token_saturation_via_audit`
  → `ATOMIC_CONCEPT:verification_must_be_proportional_to_proof_budget`


