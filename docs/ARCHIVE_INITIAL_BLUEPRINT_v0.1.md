# TONG AI — Community Compute & Credits Blueprint (Draft v0.1)

**Date:** 2 November 2026  
**Project:** TONG AI — open-source, CPU-first, peer-to-peer collective intelligence research  
**Status:** Design proposal. No production network, trained foundation model, rewards or GitHub repository is claimed to exist.

## 1. Vision
TONG AI is an open-source research network where consenting participants can contribute bounded computational resources, quality-reviewed knowledge or code and receive internal **Tong Credits (TC)** for useful, verifiable work. Participants can spend TC on compute-intensive features. Every participant retains control over their devices and private information. This does not imply universal general intelligence, perpetual uptime or guaranteed self-improvement.

## 2. Three distinct contributions
- **Compute:** scheduled inference, reproducible evaluation, bounded training experiments, compatible memory services; reward only on independently validated results.
- **Human contributions:** reviewed code, documented benchmarks, reproducible research and licensed public datasets; grant via transparent reviewer-approved bounties rather than automatically tracking conversation volume.
- **Learning feedback:** explicit opt-in and consent to use selected examples; default is private. Never require sharing chats, photos, contacts or files to earn compute credits.

## 3. Participation and access
- **Free / non-contributor:** basic local/open features and a small, sustainable network allowance where capacity permits. No obligation to share private data.
- **Contributor:** earns TC for validated resources or community tasks. More contribution generally permits more *network service usage*, not intrinsically smarter answers or unrestricted permissions.
- **Heavy user:** can accumulate TC, contribute more, or use local execution. Advanced workloads are only accessible if suitable nodes/models exist and resource budgets allow.
- **Per-device controls:** opt in/out, CPU percentage, RAM limit, data transfer cap, battery threshold, charging-only, Wi-Fi only, time window, daily usage cap and instant stop. No penalty for stopping beyond not earning new compute credits.

## 4. Initial Tong Credit economics (provisional toy values)
**Earned TC = Task Base Points × Verified Quality (0–1) × Demand Multiplier (bounded 0.5–1.5).**

Example (illustrative; not a market quote): a reproducible task worth 10 base points, with 0.9 validated quality and 1.0 demand multiplier, earns **9 TC**. Two such validated tasks earn 18 TC. If one small network query costs an illustrative **2 TC**, this buys up to 9 such queries (subject to availability). There is **no payout for simply declaring CPU/RAM**, running fake tasks, sending spam interactions or failing validation.

A task's cost should be shown before execution. Reserve the quoted TC, charge only for completed measured work and release/refund unused credits. Prices track measured work, bandwidth, validation, availability and service demand, with transparent caps. Maintain a bounded community treasury to fund trial usage, validators and public-interest research; never promise free unlimited compute.

For v0.1, TC is a **non-transferable, non-cash, in-app service unit** — not a blockchain token, financial asset or guaranteed currency. Any future transfers, cash-outs or tokenization require a separate legal and security review.

## 5. Verification and anti-abuse
- Nodes register public keys and signed *capability declarations* (limits, not unverifiable absolute performance claims).
- Scheduler sends randomized, reproducible tasks where possible; validators verify outputs and can duplicate a sample on independent peers.
- Non-deterministic AI outputs use quality tests, private holdout evaluations, challenge tasks and sampled manual review; validation has cost and is never assumed infallible.
- Prevent spoofed identities, duplicate submissions, spam credits, self-validation, malicious model updates, stolen compute, ledger double-spends and poisoning. Reputation influences scheduling but must not replace evidence.
- Keep append-only signed receipts and periodic replicated checkpoints; for real decentralized balances and concurrent spending, introduce a separately reviewed consensus/quorum mechanism. A local SQLite prototype is not a fully trustless currency.

## 6. Data and privacy
- **Default:** user interactions remain private and local. Network peers do **not** receive everyone's raw prompts, conversations or private files.
- **Opt-in knowledge sharing:** user selects specific material under a clear license and can revoke future sharing; previously shared information may be difficult to retract from decentralized peers, which must be clearly disclosed.
- **Federated learning:** may send bounded local model updates, but these can leak information; test secure aggregation, clipping, differential privacy, poisoning defenses and privacy attacks before deployment.
- Training-quality gate: provenance, permissions, privacy review, duplication filters, benchmark checks and quarantine for untrusted updates. Knowledge storage is not equivalent to robust continual learning.

## 7. Collective Brain and scheduling
1. Node advertises signed available capacity (CPU, memory, bandwidth, time, device consent limits).
2. Peer-to-peer network discovers eligible nodes.
3. Distributed scheduler matches tasks by suitability, latency, power, reliability, resource cost and data sensitivity.
4. Worker completes a bounded task locally; validator independently checks evidence.
5. Signed receipt awards TC; recipient's requested service spends TC on another task.
6. High-impact global updates require multi-party validation, safety tests, versioning and rollback; local scheduling need not trigger global consensus.

The 'collective consciousness' is an engineering metaphor for distributed coordination, shared knowledge and decision-making; it is not evidence of subjective sentience. Owners always retain permission and shutdown controls for their own devices.

## 8. Mobile / desktop / hardware
- **Android:** use WorkManager with charging/Wi-Fi/battery/storage constraints. Android does not promise uninterrupted 24/7 background execution. Provide pause/stop, battery and temperature safeguards.
- **Desktop/servers:** opt-in background jobs with resource caps, sandboxed tasks and robust signed updates.
- **Hardware portability:** CPU first; accelerator adapters for GPU/NPU; future quantum integration only for applicable algorithms as hardware becomes capable. No promise all AI workloads will run faster on quantum.

## 9. Repository skeleton (proposed, not yet created)
```text
tong-ai/
  README.md  LICENSE  CONTRIBUTING.md  CODE_OF_CONDUCT.md
  SECURITY.md  GOVERNANCE.md  ROADMAP.md
  docs/architecture.md  docs/credits.md  docs/privacy.md  docs/protocol.md
  core/                  # local model, reasoning, experiment APIs
  memory/                # compressed blocks, indexing, versioning
  network/               # libp2p discovery, signed peer messaging
  scheduler/             # bounded tasks, node capabilities
  credits/               # receipts, local ledger, settlement tests
  validator/             # reproducible challenges, quality checks
  node/                  # CPU worker
  android/               # opt-in worker prototype
  benchmarks/            # CPU/RAM/energy/privacy/quality tests
  examples/two_nodes/    # local demo without paid infrastructure
  .github/workflows/     # lint, unit tests, security checks
```

**Licensing:** choose Apache-2.0 for original code if desired; each third-party model, dataset, and weight file must be individually checked and attributed. Do not assume open weights imply unrestricted training permission. Public PRs welcome, but main branch merges require passing tests and review.

## 10. Phased zero-cash roadmap
- **M0 — Documentation and governance:** publish project charter, license, contribution policy, threat model, privacy consent, measurable success criteria; GitHub public repository.
- **M1 — Two CPU nodes on one machine:** P2P discovery, capability announcements, reproducible task, validation, signed receipt, earning/spending mock TC in SQLite, benchmark single-node baseline.
- **M2 — Five actual volunteer devices:** dropout recovery, rate limits, scheduler, fraud exercises, resource/battery logging, local encrypted data, user pause/stop.
- **M3 — Safe learning:** tiny open-licensed model or symbolic learner; opt-in training/evaluation, held-out tests, catastrophic-forgetting metrics, privacy attack tests; no automatic deployment.
- **M4 — Replicated credits and governance:** multi-validator quorum, account/receipt synchronization, anti-double-spend controls, recovery snapshots and public audit.
- **M5 — Wider network:** documented cross-platform integrations, constrained Android workers, optional model specialists, comprehensive safety/energy testing; upgrade only after results demonstrate benefit.

## 11. Measurable acceptance criteria for M1
- Two separate CPU processes discover one another and exchange mutually authenticated task metadata.
- One reproducible task is computed by node A, independently checked by node B, with an auditable receipt.
- A mock user starts at 0 TC, receives the expected verified TC, spends TC on a service, and cannot double-spend.
- A node can disconnect without data corruption; the remaining local demo can recover or clearly report incomplete work.
- Record baseline vs P2P latency, CPU time, maximum RAM, network bytes, energy estimate (if measurable) and quality accuracy; publish raw experimental method.
- All tests run locally on ordinary CPU and in public GitHub Actions without requiring a paid AI API.

## 12. Grounding / reference links
- GitHub pricing and public Actions: https://github.com/pricing
- Android WorkManager constraints: https://developer.android.com/develop/background-work/background-tasks/persistent/getting-started/define-work
- Flower secure aggregation (not a complete guarantee of privacy): https://flower.ai/docs/framework/main/en/explanation-ref-secure-aggregation-protocols.html
- Bittensor incentive design: https://guides.learnbittensor.org/learn/anatomy-of-incentive-mechanism
- Golem compute marketplace: https://docs.golem.network/docs/golem/payments
- libp2p: https://github.com/libp2p/rust-libp2p

**Bottom line:** Reward useful validated work, not nominal hardware specs or private user data. Make participation optional and transparent. Start with a small CPU-only experiment, then test whether the network learns, saves energy and improves reliability before claiming distributed intelligence.