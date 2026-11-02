# TONG AI Research Roadmap

Milestones are **gated by evidence**, not dates or promises. Research results may invalidate parts of the plan.

| Milestone | Work | Completion gate |
|---|---|---|
| M0 | Public docs, 1000 FAQ, decision records, contributor policy, docs CI | 1000 unique FAQ entries, passing checks, privacy/credit/tiers defined |
| M1 | CPU local simulator and two-process signed job transport | Compare baseline vs two peers; verified job receipt; no double-spend |
| M2 | Small libp2p-compatible distributed coordinator | Peer churn, dropout, NAT fallback, signed capability declarations, latency metrics |
| M3 | Offline toy continual learner + opt-in feedback | Held-out quality improves on at least selected tasks, forgetting and leakage assessed |
| M4 | Compression + signed distributed knowledge snapshots | Lossless restore, query latency, bit/byte cost, tamper test, owner delete path |
| M5 | Android opt-in node with resource limits | OS-conformant scheduling, thermal/battery/stop and transparent data consent |
| M6 | Contributor credits ledger + anti-Sybil tests | Quorum validation and double-spend protection under fault injection |
| M7 | Paid dedicated inference **only after funding** | Independent 3s small-response SLO pilot, load/stability/fairness tests |
| M8 | Multimodal skills / CPU/GPU/NPU adapters | License audits, per-modality tests, graceful fallback |
| M9 | Foundation legal & finance readiness | Qualified legal/accounting review; public reports; reserve and procurement policy |
| M10 | Research-grade hardware/quantum abstractions | Portable adapter API; simulator and classical reference; honest quantum-specific benchmarks |

First public milestone is **docs and local simulation**, not a released frontier model.