# Docker Desktop: Context Map (Receipts + Edges)

## Receipts (Tier 0: local files)

- `Downloads/_ByType/Docs/Receipts/docker_version.txt`
- `Downloads/_ByType/Docs/Receipts/docker_info.txt`
- `Downloads/_ByType/Docs/Receipts/docker_context_ls.txt`
- `Downloads/_ByType/Docs/Receipts/docker_ps_a.txt`
- `Downloads/_ByType/Docs/Receipts/docker_images.txt`
- `Downloads/_ByType/Docs/Receipts/docker_volume_ls.txt`
- `Downloads/_ByType/Docs/Receipts/docker_network_ls.txt`
- `Downloads/_ByType/Docs/Receipts/docker_system_df.txt`

## Atomic contexts extracted (ATOMIC_CTX)

- `ATOMIC_CTX:docker_desktop_available`:
  - Receipt: `docker_version.txt` shows **Server: Docker Desktop**.
- `ATOMIC_CTX:docker_context_desktop_linux_active`:
  - Receipt: `docker_version.txt` / `docker_context_ls.txt` shows **Context: desktop-linux** selected.
- `ATOMIC_CTX:kubernetes_on_docker_desktop_running`:
  - Receipt: `docker_ps_a.txt` shows `k8s_*` containers (apiserver, etcd, controller-manager, scheduler, coredns).
- `ATOMIC_CTX:local_llm_stack_present`:
  - Receipt: `docker_volume_ls.txt` includes `ollama`; images include `ollama/ollama`, `ghcr.io/open-webui/open-webui`.
- `ATOMIC_CTX:mcp_images_present_in_docker`:
  - Receipt: `docker_images.txt` includes `mcp/playwright`, `mcp/git`, `mcp/fetch`, `mcp/dockerhub`, plus `ghcr.io/github/github-mcp-server`.

## Hinge chain edges (CTX_PTR → ATOMIC_CTX → HINGE → ATOMIC_CONCEPT)

### Chain A: Docker as execution substrate

- `CTX_PTR:docker_info_receipt` → `ATOMIC_CTX:docker_desktop_available`
- `ATOMIC_CTX:docker_desktop_available` → `HINGE:enables:local_execution_substrate`
- `HINGE:enables:local_execution_substrate` → `ATOMIC_CONCEPT:execution_can_be_receipt_backed_locally`

### Chain B: K8s on Docker Desktop as orchestration substrate

- `CTX_PTR:docker_ps_a_receipt` → `ATOMIC_CTX:kubernetes_on_docker_desktop_running`
- `ATOMIC_CTX:kubernetes_on_docker_desktop_running` → `HINGE:enables:multi_agent_orchestration`
- `HINGE:enables:multi_agent_orchestration` → `ATOMIC_CONCEPT:orchestration_increases_observable_edges`

### Chain C: Local LLM tooling increases “capability surface” (and log surface)

- `CTX_PTR:docker_volume_ls_receipt` → `ATOMIC_CTX:local_llm_stack_present`
- `ATOMIC_CTX:local_llm_stack_present` → `HINGE:risks:log_and_state_proliferation`
- `HINGE:risks:log_and_state_proliferation` → `ATOMIC_CONCEPT:more_execution_surface_can_increase_context_saturation_risk`

### Chain D: MCP images in Docker imply “tool execution pathways”

- `CTX_PTR:docker_images_receipt` → `ATOMIC_CTX:mcp_images_present_in_docker`
- `ATOMIC_CTX:mcp_images_present_in_docker` → `HINGE:supports:tooling_routing`
- `HINGE:supports:tooling_routing` → `ATOMIC_CONCEPT:tools_can_be_containerized_for_reproducible_receipts`

## Notes (non-governing)

- This file is a **map**, not an instruction to delete/cleanup anything.
- Any “cleanup” (image pruning, volume deletion) must be **explicitly approved** (per `.cursorrules`).
