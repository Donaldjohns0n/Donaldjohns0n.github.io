## Context Relational Matrix (What Changes What)

This is the “talk to each other” map: **which artifacts mutate context**, where they write receipts, and what hinges connect them into the invariant graph.

### Canon nodes

- **Invariant graph**: `Downloads/_ByType/Docs/INVARIANT_GRAPH.mermaid`
- **Fast plan**: `Downloads/_ByType/Docs/FAST_PLAN_INVARIANT_GRAPH_RIPPLES.md`
- **Edge map**: `Downloads/_ByType/Docs/EDGE_MAP_Fortress_Collapse_Token_Saturation.md`
- **Hinge chain spec**: `Downloads/_ByType/Docs/HINGE_CHAIN_ATOMIC_CONTEXT_POINTERS.md`
- **Pointer ledger (append-only)**: `Downloads/_ByType/Docs/CTX_PTR_LEDGER.jsonl`

### Context mutators (high-impact)

- **`Downloads/scripts/codex_browser_agent.py`**
  - **Mutates**: creates/append-writes `codex_mcp_actions.jsonl`, `codex_prompt_queue.jsonl`, `codex_agent_actions.jsonl`
  - **Hinge**: “Prompt → MCP tool-call queue → browser action → snapshot/network proof”
  - **Risk**: if verification remains stubbed (it is), edges may be promoted without real proof.

- **`Downloads/scripts/oracle_action_executor.py`**
  - **Mutates**: `oracle_actions_executed.jsonl`; may execute subprocess; may enqueue MCP actions.
  - **Critical risk**: `_cleanup_temp_files()` deletes `*.tmp`, `*.log`, `*.bak` in `~/Downloads` (local evidence loss).
  - **Hinge**: “Issue → action → proof receipt.”

- **`Downloads/scripts/self_heal_system.py`**
  - **Mutates**: `self_heal_log.jsonl` + triggers action executor.
  - **Time**: uses time windows for detection internally (this is OK as *operational monitoring*, but not a decision axis for governance edges unless explicitly tagged).
  - **Hinge**: “System fake detection → execute claimed action → log proof.”

- **`Downloads/scripts/oracle_config.json`**
  - **Mutates**: behavior thresholds, auto-execute policy, verification requirements, retention days.
  - **Hinge**: “Policy knobs → what becomes ‘auto’ vs ‘manual’.”

- **`Downloads/scripts/meta/README_ATOMIC_PIPELINE.md`**
  - **Mutates**: defines canonical pipeline steps (extract→hash→context→commit).
  - **Hinge**: “File → atomic contexts → commit receipts.”

- **`Downloads/scripts/migration/README.md`**
  - **Mutates**: defines what lives on laptop vs Drive vs GitHub pointers.
  - **Hinge**: “Large artifacts → Drive + pointer → GitHub.”

- **`Downloads/service_account_ghost_audit_protocol.md`**
  - **Mutates**: governance / alert schema; introduces `AnomalySignal` JSON schema for queue-based monitoring.
  - **Hinge**: “Cloud logs → anomaly signal → monitor queue → action.”

### Evidence surfaces (where “truth” lives)

- **Local evidence**: `Downloads/_ByType/Images/*`, `Downloads/files/*.mermaid`, `Downloads/_ByType/Docs/*`
- **Agent receipts/logs** (local): `Downloads/scripts/*.jsonl` outputs (queues + action logs)
- **Backups**: `C:/Users/cardi/Brain/Snapshots/brain_snapshot_*.zip`

### Immediate integrity note (non-deletion stance)

If your rule is “all context is useful,” then `oracle_action_executor.py` cleanup must be treated as **dangerous by default** because it can delete evidence-like `*.log` files.
Until we add an allowlist, do not run cleanup actions automatically.


