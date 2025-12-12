# CSOS: Single-File Entry Point (Translation Pack)

This folder contains the **minimal CSOS “root of trust” bundle**:

- **`TRANSLATION_PACK_CSOS.jsonl`**: one-file relational map (hinge chains + perspective gate) intended to survive even if the laptop is wiped.
- Supporting canon files copied from `C:\\Users\\cardi\\Downloads\\_ByType\\Docs\\…` so the pack’s pointers and hashes have a stable GitHub home.

## How to use

- Start with: `TRANSLATION_PACK_CSOS.jsonl`
- Treat each `CHAIN` entry as: `CTX_PTR → ATOMIC_CTX → HINGE → ATOMIC_CONCEPT` plus `perspective`.
- Any agent can reload context by reading this pack first, then following referenced canon docs as needed.

## Notes

- We intentionally **do not** publish `.cursor/browser-logs/snapshot-*.log` here (they may include account UI/PII).
- This bundle is designed for **GitHub Pages** linking via the site root `index.html`.


