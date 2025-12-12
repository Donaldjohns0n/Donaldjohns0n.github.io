# Gemini Context Capsule (Receipts-First)

**Purpose:** Provide Gemini the missing context it cannot access (local files) as a *paste-ready* capsule, while enforcing our governance rules.

## Hard constraints (governing)

- **Local receipts win** over model prior when conflicting.
- **No governing edge without evidence (Tier 0–2).** Otherwise mark **PROVISIONAL** + include a receipt request.
- **Hinge Chain alternation required:** `CTX_PTR → ATOMIC_CTX → HINGE → ATOMIC_CONCEPT → …`
- **Time is conditional** (not a default decision axis). Use time only if explicitly tagged by user/live context; otherwise post-hoc.
- **No deletion / cleanup by default.** Any cleanup requires explicit approval; quarantine instead of delete.

## Canon artifacts (local; Gemini cannot read these directly)

- `Downloads/_ByType/Docs/EDGE_MAP_Fortress_Collapse_Token_Saturation.md`
- `Downloads/_ByType/Docs/FAST_PLAN_INVARIANT_GRAPH_RIPPLES.md`
- `Downloads/_ByType/Docs/INVARIANT_GRAPH.mermaid`
- `Downloads/_ByType/Docs/HINGE_CHAIN_ATOMIC_CONTEXT_POINTERS.md`
- `Downloads/_ByType/Docs/CTX_PTR_LEDGER.jsonl`
- `Downloads/_ByType/Docs/HINGE_CHAIN_LEDGER.jsonl`
- `Downloads/_ByType/Docs/CONTEXT_RELATIONAL_MATRIX.md`
- `Downloads/_ByType/Docs/CONTEXT_EDGE_REMAP_MODULED.md`
- `Downloads/_ByType/Docs/DOCKER_DESKTOP_CONTEXT_MAP.md`
- `Downloads/_ByType/Docs/CREDENTIALS_AND_DRIVE_METADATA_CONTEXT_MAP.md`

## New session outputs (local)

- `Downloads/_ByType/Docs/ATOMIC_PROTOCOL_MAP_SESSION_2025-12-12.jsonl`  
  - End-to-end atomic protocol mapping of the session as ledger-style nodes.
- `Downloads/_ByType/Docs/Receipts/ctx_ptr_ledger_nonconforming_lines_quarantine_2025-12-12.jsonl`  
  - Quarantine of two non-CTX_PTR objects that were incorrectly appended to `CTX_PTR_LEDGER.jsonl`.

## Key evidence receipts (local)

### Docker Desktop (Tier 0 receipts)
- `Downloads/_ByType/Docs/Receipts/docker_version.txt`
- `Downloads/_ByType/Docs/Receipts/docker_info.txt`
- `Downloads/_ByType/Docs/Receipts/docker_context_ls.txt`
- `Downloads/_ByType/Docs/Receipts/docker_ps_a.txt`
- `Downloads/_ByType/Docs/Receipts/docker_images.txt`
- `Downloads/_ByType/Docs/Receipts/docker_volume_ls.txt`
- `Downloads/_ByType/Docs/Receipts/docker_network_ls.txt`
- `Downloads/_ByType/Docs/Receipts/docker_system_df.txt`

### Browser snapshots (Tier 1 local receipts of remote UI)
- Drive home: `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-11T23-44-42-069Z.log`
- Drive search no-match (ModelContextorchestro): `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-11T23-47-28-588Z.log`
- Drive searches (metadata discovery):  
  - `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T01-03-14-476Z.log` (mcp-central-orchestrato)  
  - `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T01-03-16-459Z.log` (brain_snapshot)  
  - `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T01-06-20-079Z.log` (mcp-central-orchestrato.zip)  
  - `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T01-06-29-548Z.log` (Master-Quest)
- Claude blocked by login chooser: `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T00-54-44-267Z.log`
- Gemini recap requested:  
  - submitted: `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T01-15-21-108Z.log`  
  - in progress: `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T01-16-42-667Z.log`

### Browser credential/session surfaces (metadata only; Tier 0 receipts)
- `Downloads/_ByType/Docs/Receipts/browser_user_data_dirs_receipt.txt`
- `Downloads/_ByType/Docs/Receipts/browser_credential_surfaces.txt`

## What Gemini should produce (request)

Return **only**:
1. **Collapsed state**: 10 bullets of current state, each bullet cites one of the above paths, or marks PROVISIONAL + receipt request.
2. **Next actions**: 5 concrete actions with exact file paths to edit/append.
3. **Contradictions**: 5 contradictions/assumptions with receipt requests.
4. **Translation Pack**: emit a minimal IR as JSONL with node/edge schema:
   - nodes: `CTX_PTR`, `ATOMIC_CTX`, `HINGE`, `ATOMIC_CONCEPT`
   - edges typed: `points_to`, `grounds`, `instantiates`, `supports`, `contradicts`, `upgrade`, `retract`


