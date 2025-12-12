# Credentials + Drive Metadata: Context Map (Safe Handling)

## Core rule
We treat “passwords / cookies / auth tokens” as **context surfaces** (they explain *why* access works), but we do **not** extract or expose secrets.

What we store as receipts:
- file paths
- sizes
- timestamps
- browser snapshot logs (page-level proof)

What we do NOT store:
- decrypted passwords
- cookie values
- access tokens

---

## Evidence (Tier 0): local browser profile stores (metadata-only receipts)

- `Downloads/_ByType/Docs/Receipts/browser_user_data_dirs_receipt.txt`
  - proves Chrome/Edge profile roots exist and enumerates top-level entries (names only)
- `Downloads/_ByType/Docs/Receipts/browser_credential_surfaces.txt`
  - proves presence of high-signal stores like:
    - Chrome `Local State`, `Login Data`, `History`, `HistoryEmbeddings`
    - Edge `Local State`, `Login Data`, `History`

### Hinge chains (safe)

- `CTX_PTR:browser_credential_surfaces_receipt`
  → `ATOMIC_CTX:browser_session_state_exists_locally`
  → `HINGE:enables:authenticated_browser_access`
  → `ATOMIC_CONCEPT:browser_state_is_an_execution_enabler_not_a_shareable_secret`

---

## Evidence (Tier 1): Google Drive browser search receipts

Snapshots (local artifacts captured by the browser tool):
- `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T01-03-14-476Z.log` (Drive search: `mcp-central-orchestrato`)
- `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T01-03-16-459Z.log` (Drive search: `brain_snapshot`)
- `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T01-06-20-079Z.log` (Drive search: `mcp-central-orchestrato.zip`)
- `C:/Users/cardi/.cursor/browser-logs/snapshot-2025-12-12T01-06-29-548Z.log` (Drive search: `Master-Quest`)

### Hinge chain (Drive as metadata evidence store)

- `CTX_PTR:drive_search_mcp_central_snapshot_2025_12_12`
  → `ATOMIC_CTX:drive_search_results_viewable_in_session`
  → `HINGE:enables:remote_pointer_discovery`
  → `ATOMIC_CONCEPT:drive_metadata_can_supply_recheckable_ctx_ptrs`

---

## Practical “containment” pattern
When you say “my Drive is logged in so are lots of my passwords and metadata”, the safe operational translation is:

- Use the logged-in session to **enumerate file/folder identifiers** and capture snapshot receipts.
- Use local receipts to show **which stores exist**, without reading secrets.
- Convert any useful discovery into `CTX_PTR` entries + (optionally) hinge-chain nodes with **PROVISIONAL** status until Tier 0–2 evidence is attached.


