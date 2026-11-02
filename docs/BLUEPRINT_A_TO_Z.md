# TONG AI — A–Z Engineering, Research, Community and Foundation Blueprint

**Document version:** 0.1.0-draft · **Created:** 2026-11-02 · **Maturity:** research architecture proposal, not an implemented network. **Scope:** full project and staged path from no-cost CPU experiments to a global volunteer P2P fabric with optional funded high-end service. **License:** Apache-2.0 original project text (third-party assets separately licensed).

> **Mission:** Develop a resilient, open, energy-aware collective intelligence architecture that can learn from explicitly permitted interaction data, safely coordinate heterogeneous computing nodes, select appropriate specialist capabilities, port across hardware generations and demonstrate measurable improvements rather than claim superhuman universal ability.

## A. Executive contract: what is and is not promised

1. Open-source core and public interoperability specifications; contributions accepted through review, tests and owner-consent rules.
2. **One** distributed collective intelligence ecosystem. The *logical* shared control plane and knowledge versioning are not a secret physical central server, nor evidence of subjective consciousness.
3. **CPU-first** task execution and low-power baseline. Accelerators optional. Idle phones are not unlimited free GPUs; electricity, thermal constraints, transfer and network latency matter.
4. Heterogeneous nodes can share **capacity for suitable parallel tasks**. Ten computers do not automatically give a single autoregressive answer 10x speed; WAN pipeline split can be slower.
5. Paid top tier uses *reserved, funded, fast* foundation infrastructure with highest priority and most capable licensed models feasible; contributor credits second; free third. All use same evolving protocol/network knowledge, with strict privacy separation.
6. Accept **only opt-in private learning data** with sufficient provenance, and do not replicate raw private chats across untrusted nodes. Learning can exploit consented feedback and small aggregate updates without approving every user statement as fact.
7. Allow sandboxed self-evolution experiments with independent evaluation and rollback, never a design that prevents shutdown or overrides the owner's control of their device.
8. Public-benefit non-profit/foundation is a **proposed future legal entity**. No incorporation, charitable status or donor tax deduction is asserted here.
9. Longevity means recoverability and open formats, not literal eternal availability. Environmental protection is a measurable constraint, not an absolute zero-harm promise.
10. **Performance aspiration**: fast routing, early streaming and ideally p95 complete answer <3s for a constrained small-request workload on eligible fast dedicated hardware. This is a future SLO under published conditions, not a universal guarantee or measured result.

### Definitions
- **Node:** a voluntarily enrolled device process with owner-set resource and data policy.
- **Fabric:** P2P transport, peer discovery, task directory, scheduling, remote worker execution, receipts and replicated metadata.
- **Collective brain:** task-specific model specialists, a versioned, evidence-backed shared knowledge layer, context policies and distributed decision logic.
- **Claim:** independently verifiable report about capacity, task completion, model version or authorised knowledge.
- **Training:** gradient updates or explicitly measured learning transformations; not the same as saving text in a searchable index.
- **Tier:** service entitlement, scheduler treatment and compute source; never a user's worth or permission to collect their data.
- **TONG Credit (TC):** proposed non-transferable service accounting unit, not cryptocurrency or cash equivalent.

## B. User journeys and personas

**Guest / Free:** install chat client, use constrained shared capacity if available; no mandatory mining/training or private-data sharing. A user can elect local-only response, use a clear privacy indicator and revoke permissions.

**Contributor:** installs node, reviews battery/CPU/RAM/network caps, tests capability (not a trusting self-declaration), accepts sandboxed tasks, monitors earnings and may pause immediately. A compatible desktop node offers more reliable sustained compute than a mobile app.

**Paid:** subscribes (future), receives dedicated pool admission and priority with published SLO, queue and fair-use boundaries. Billing transparency shows actual model size/limitations; no false guarantee that subscription makes intelligence unlimited.

**Contributor researcher:** forks public repo, submits reproducible algorithm, document or dataset card; independent review; approved verified non-compute bounties may earn TC through a separate governance policy.

**Guardian/operator:** maintains incident recovery, monthly reports, capacity balancing, fraud tests, opt-in revocation, paid pool procurement, regulator compliance and governance votes.

## C. Layered reference architecture

```text
┌──────────────────────────── Chat / Web / Android / CLI / IoT Gateways ────────────────────┐
│  AuthN, permissions, privacy controls, conversation context, streaming, tier identity     │
└──────────────────────────────────────┬────────────────────────────────────────────────────┘
                                       │
┌───────────────────────────── Distributed Control Plane ──────────────────────────────────┐
│ Peer discovery │ signed capability inventory │ model/skill directory │ regional schedulers│
│ policy evaluation │ credits & budgets │ observability │ update / rollback manifests      │
└──────────────┬────────────────────────┬──────────────────────────┬────────────────────────┘
               │                        │                          │
       Dedicated paid pool       Volunteer/shared pool      Validation/research pool
       fast models / NVMe        CPU and optional GPU       independent checks / eval
               └────────────────────────┬──────────────────────────┘
                                        │
┌────────────────────────── Collective Model & Knowledge Plane ───────────────────────────┐
│ Versioned expert models │ deterministic tools │ indexed compressed memory │ provenance   │
│ opt-in learning pipeline │ benchmark suite │ sandboxed new-model promotion              │
└──────────────────────────────────────────────────────────────────────────────────────────┘
```

**Control plane** chooses who may work; **data plane** carries encrypted minimal tasks/results; **learning plane** handles permissions, evidence, incremental updates and model promotions; **governance plane** controls releases and organizational rules; **finance plane** funds dedicated compute and audited service credits. Do not couple their failure modes.

**Avoid all-to-all calls for chat:** a request is routed to one suitable warm model worker, or a small independently parallel subset. Global consensus on each token would destroy latency. A replicated policy and directory can remain decentralized even while individual tasks execute on a single node.

## D. One collective brain without a physical master

This is a **replicated logical control algorithm**, not a biological consciousness. Regional peers maintain signed health and skill summaries. A requester can calculate an eligible shortlist locally or query multiple independent directory replicas, then select a worker. Consensus/threshold approval is reserved for *critical durable shared changes* (model release approvals, ledger settlement, protocol versions), while ordinary task routing requires no global vote.

**Consistency strategy:** eventual consistency for non-critical capability gossip; monotonic sequence numbers or version vectors for node updates; content-addressed immutable knowledge snapshots; stronger quorum or transactional storage for credit debits and release approvals. CRDT merges are useful only where merging semantics are mathematically safe (e.g. sets of non-secret announcements); do **not** use naive CRDT increment/decrement to settle monetary-like balances across partitions.

**Failure modes:** stale warm-model ads, capacity lies, peer churn, NAT blocks, geographic split, rogue directory members, poor-quality specialist. Handle with signed freshness, on-demand benchmark samples, multi-transport fallback, reputation *bounded* by recent performance, duplicate validators and graceful standalone mode.

## E. Network protocol: transport, discovery, trust

**Suggested initial stack:** Rust (`libp2p`) for high-performance portable node agent; QUIC/TLS 1.3 authenticated multiplexed connections; Noise-based secure channels only if reviewed in actual transport profile; libp2p DHT + mDNS for laboratory discovery; relay/hole punching where appropriate; gossipsub for *small signed metadata*, not full prompts or weight blobs. Rust is a suggested implementation, not a completed dependency decision.

**Message types, versioned in protobuf/CBOR:** `HELLO`, `NODE_CAPABILITY`, `CAPABILITY_CHALLENGE`, `TASK_OFFER`, `TASK_ACCEPT`, `TASK_RESULT`, `VALIDATION_ATTESTATION`, `CREDIT_RECEIPT`, `MODEL_MANIFEST`, `SNAPSHOT_ANNOUNCE`, `REVOKE`, `HEALTH`, `GOODBYE`. Unrecognized critical features reject or negotiate safely. All network frames have explicit size limits, depth limits and deadlines.

**Node identity:** generate device-local asymmetric key; derive node ID from public-key hash; rotate session keys; keep long-term credentials in OS keystore when possible; recover identity via explicit owner-controlled procedure, not silent global re-enrollment. Signed nonces and monotonic timestamps prevent replay. Bind offer, task, result and receipt to one task ID and model hash.

**Bootstrap:** initial optional published seed lists discover peers but are not trusted authorities; allow independently hosted seed lists, local LAN discovery and offline/manual peer addresses. Transparent network partitions should not give the impression of a single synchronized omniscient brain.

**Bandwidth:** chunked content hashes, range requests, resumable transfers and max egress. Keep peer control messages tiny; never gossip sensitive prompts or full training gradients publicly.

## F. Node lifecycle and owner control

Lifecycle: `UNENROLLED → EXPLICIT_OPT_IN → KEY_GENERATED → CAPABILITY_BENCHMARK → AVAILABLE → TASK_LEASED → EXECUTING → VERIFIED → IDLE` or `PAUSED / REVOKED / QUARANTINED`.

Owner controls: max CPU%, max resident RAM, threads, storage, daily upload/download, metered networks, minimum battery, charging-only, idle-only, allowed hours, maximum thermal level, permitted modalities, allowed data categories, public visibility and one-touch stop. Agent must enforce quotas independently of any remote scheduler or model output; an unresponsive server must never prevent local stop. Distinguish always-online chat interface from availability of a volunteer phone worker.

**Hardware profile:** CPU ISA/cores, RAM, memory bandwidth, accelerator capability/VRAM, thermal sustained benchmarks, disk, energy samples, model versions warm-loaded, RTT/jitter to candidate clients, uptime reliability, legal region and allowed task sensitivity. Profiles are signed claims *plus verified observed measurements*. Do not accept self-reported 16 GB RAM as proof of speed or authorization to consume all 16 GB.

## G. Scheduling: fast, fair and privacy constrained

**Stage 1 — Parse:** derive intent/topic, estimated output tokens, reasoning difficulty, needed modality/tools, privacy classification, model capability threshold, deadline and tier. Keep classifier local/low-cost where possible. Continuous same-chat affinity avoids repeated network/model warm-up.

**Stage 2 — Filter:** eligible by explicit node consent, sufficient memory/CPU and loaded model, software compatibility, security policy, data residency, egress permissions, tier restrictions and remaining quota. Never route private input to unapproved strangers merely because low RTT exists.

**Stage 3 — Score:** choose smallest **predicted end-to-end latency** for a candidate meeting quality/trust thresholds, not highest clock speed. Example heuristic (to tune from actual telemetry):

`T_predict = T_auth + RTT + T_queue + T_context_transfer + T_prefill + (tokens_out / sustained_tokens_per_second) + T_validation`.

Penalties: thermal/battery risk, node reliability, hidden load, poor model accuracy, privacy cost and price. Use conservative p90 predictions, not optimistic averages. A faster node far away can lose to a warm regional model.

**Stage 4 — Execute:** lease finite task with cancellation ID; stream verified content when safe; renew leases by heartbeat; idempotency token protects credit and side effects; fallback to next healthy eligible node if worker fails. For independent subproblems run a few workers parallel and aggregate; do not blindly distribute every transformer layer across internet phones.

**Stage 5 — Learn:** keep trace metadata minimal; explicit opt-in feedback becomes reviewable training candidate. Aggregate metrics, not raw chats, in the public dashboard.

**Three-tier admission:** Paid queue has reserved dedicated capacity and precedence; Contributor has credit-backed reservations on qualified shared capacity; Free has protected minimum service subject to capacity/fair use. Use bounded priority with ageing/quotas and documented exceptions for emergencies. Paid temporary spare capacity leasing to lower tiers should be preemptable *without losing user data* and should exclude non-checkpointable jobs if disruption would harm users.

## H. CPU pooling mathematics and boundaries

For N heterogeneous nodes, theoretical total independent task throughput is roughly `Σ jobs_per_second_i`, adjusted for scheduling and validation overhead. A single sequential autoregressive generation path still depends on the active model and critical path. Throughput improves more reliably than per-message latency. For partitioned model layers, inter-node bytes and RTT can dominate every decoding step.

**Parallelisable:** independent evaluation prompts, dataset transforms, batched inference requests, content indexing, matrix shards in LAN/HPC conditions, simulations, hyperparameter sweeps, isolated specialist subtasks and privacy-preserving federated aggregation. **Potentially harmful to split over WAN:** tightly coupled token-by-token transformer stages requiring high-bandwidth synchronized tensors.

**Benchmark:** one CPU baseline, local 2-core, two devices on LAN, two across WAN, then five volunteer nodes; report p50/p95 time-to-first-token (TTFT), full-response latency, output tokens/s, tasks/s, CPU-seconds, wall time, Joules/query where measurable, energy instrumentation quality and 95% CI. Use same prompts, models and quality targets.

## I. Paid performance pool and SLOs

Dedicated foundation-owned/leased GPUs/CPUs are optional future funded infrastructure, not present. To deliver highest capability, maintain a catalog of models *actually licensed/installed* and ensure adequate RAM/VRAM, throughput, networking, prefill engines, batching, caching and failover. "Best intelligence" is evaluated separately from "fastest answer".

**Draft service objectives, subject to pilot data:** eligible short-text prompts (e.g. ≤128 input tokens and ≤80 output tokens, no tools, warm model, defined region): TTFT p95 ≤1 s, full completion p95 ≤3 s for Paid. Higher complexity/media/tasks require separate SLOs. Measure at client, not inside model server alone. Track uptime, admission rejections, queue delay, hallucination/quality, network errors, fallbacks and timeouts. Never advertise the draft SLO as a current guarantee.

**Capacity model:** required peak generation capacity `λ_requests × mean_output_tokens / target_time`, add prefill, context and variance. On overload scale infrastructure, apply transparent quotas or queue; never silently reclassify paid tasks to untrusted volunteer nodes. Foundation-paid pool may consume shared validated knowledge but cannot make private paid inputs globally public.

## J. Contributor credits: fair and fraud-resistant

**Earn formula (research starting point):** `credits = base_task_units × verified_quality ∈[0,1] × measured_difficulty × demand_weight`, all bounded and openly specified. Example 10 base units, quality 0.9, difficulty 1, demand 1 → 9 TC. Do not reward raw CPU-hours absent useful verified work; otherwise idle spinning and self-created tasks exploit rewards.

**Spend:** show maximum credit quote and estimated service availability, reserve balance, execute idempotent task, settle actual work with receipts and refund unspent reservation. Never count the same receipt twice. Queue priority requires both credit budget and resource eligibility; credits do not purchase access to private information.

**Ledger:** toy prototype may use SQLite transaction; production requires authenticated account, durable replicated settlement mechanism preventing double spend under partitions, audit logs, dispute/reversal policy and careful Sybil economics. A Merkle tree or append-only log alone does not serialize concurrent debits. Prefer permissioned validators in early federated pilot, later analyze decentralized quorum/BFT tradeoffs. Do not imply decentralization guarantees no collusion.

**Economics:** publish conversion *to service units*, not fiat value; reserve contribution rewards for genuine demand; bound issuance; prevent circular self-farming and validator collusion; simulation-test inflation and deficit. Credits initially **non-transferable, non-refundable, non-cash** service accounting units. Real money payouts or transferable tokens are deferred until legal, abuse and tax review.

## K. Free participation and inclusion

Free access must not require donating compute, exposing chats, excessive advertising or phone battery. Offer capped shared compute and/or local small models, predictable fair-use policy and queues. A system depending on 24/7 volunteers may have no capacity at times; say so. Accessibility, low-bandwidth text, multilingual outputs and offline mode are research priorities. Credit tiers distinguish scheduling economics, not moral importance.

## L. Consent-first interaction-to-learning pipeline

```
User prompt -> response (ephemeral / private by default)
  -> optional local feedback signal
  -> explicit per-type consent + license / provenance
  -> redact PII + data minimisation + deduplication
  -> quarantine staging / quality + safety + poisoning review
  -> supervised dataset / retrieval candidate / preference sample
  -> sandbox experiment (not production)
  -> held-out tests, privacy attacks, forgetting tests, energy and capability checks
  -> signed version approval / staged rollout / measurable regression monitoring
  -> rollback or promote
```

**Never:** automatically distribute all conversation text throughout public nodes; treat a toxic statement as universal truth; make model weights public merely because a user chatted; train on private data without meaningful informed consent. Even aggregated model updates can leak training examples. If public examples are uploaded, communicate irreversible replication limitations; revocation may stop *future* use but cannot promise deletion from offline hostile copies. Provide local-only and no-training switches.

Training updates require independent validation and opt-out enforcement. For user-level personalization, prefer isolated local memory or LoRA-adapter where valid; keep distinct from global knowledge. Avoid cross-account leakage in caches and retrieval. Instrument consent events and retention policies without collecting private content unnecessarily.

## M. True continual learning vs knowledge retrieval

**Memory ingestion** adds facts to retrieval index; it is not evidence the base model has acquired new reasoning skills. **Parameter adaptation** changes trained weights/adapters but risks catastrophic forgetting and poisoning. **Skill acquisition** is measured by performance on *unseen tasks* after new knowledge, not by repeating a saved answer.

Research loop: public deterministic reasoning tasks → baseline → train symbolic/small model incrementally → interleaved rehearsal or bounded replay with licensed data → evaluate forward transfer, backward transfer, forgetting, calibration and resource use → promote only positive changes on independent holdouts.

**Self-evolution limits:** AI may propose architecture search, compression configurations, agent plans and tests inside budgets. It cannot self-modify signed deployment code, alter safety controls, exfiltrate keys, replicate outside owner approval or refuse shutdown. Automatic sandbox experimentation is encouraged; automatic unvalidated production upgrades are not.

## N. Open-model teachers and legal dependency isolation

Potential *research inputs* include Qwen, DeepSeek, other redistributable model checkpoints and evaluation corpora; actual usable versions require license-by-version inspection. Some providers allow inference but forbid distillation into competing models, and "weights downloadable" does not guarantee training redistribution rights. Code license ≠ weights license ≠ dataset license ≠ output license. Maintain model cards, hashes, evaluation results and terms for any model actually integrated. Never hardcode claims that a future named flagship model has an MIT licence without checking that exact repository and release.

**Design:** `ModelAdapter` ABI with capabilities (`text`, `vision`, `audio`, `video`, `code`, `robotics`), context window, tokenizer ID, precision, hardware compatibility, estimated cost and trust tier; model routing based on measured skills and allowed rights. Multi-expert orchestration begins with a few small models, not ten always-resident frontier models. Graphics, robotics and realtime video remain separate costly modalities.

## O. Universal multimodal / tool / device interoperability

Clients support intent-classified routing to opt-in tools and domain experts: text, code, image analysis/generation, speech, music, video, scientific computing, workflow agents and robotics **only when implementations actually exist**. Standardise JSON/CBOR tool interfaces, typed schema validation, version negotiation, permission prompts and side-effect classification. A device connector runs only on owned/authorized devices, never automatically probes arbitrary internet hosts.

IoT node types: minimal local controller (tiny MCU; no full LLM), delegated gateway (home hub/phone), capable on-device model (phone/desktop), hosted dedicated inference (optional). Include offline-safe operation and degraded modes. Long-running actions require human approvals, timeouts and audit trails. A universal "every device" claim is impossible without vendor support, rights and adequate hardware.

## P. Compressed Universal Memory Engine (CUME)

**Separation of layers:** (1) immutable source data and consent record; (2) chunked compression of allowed source with hashes; (3) semantic entities/relations/provenance and embeddings, optional; (4) low-latency indexes; (5) warm cache; (6) expiry/deletion/tombstones and version manifests. Do not blur lossless source compression with lossy learned summaries or model weight quantization.

**Proposed mechanics:** content-addressed chunks sized from measured data (e.g. 64–256 KiB exploratory); fast LZ4 or Zstandard with trained dictionaries only when benefit measured; keyed Bloom filters/lexical index and vector search; targeted decompression of relevant chunks, cache policy by access and sensitivity; cryptographic hashes across chunk and manifest. De-duplicate only within privacy domain unless explicitly safe (cross-user dedup may leak possession of files). Choose compression mode dynamically from a sample, avoid repeated recompression on hot path.

**Evaluation:** compression ratio = original_bytes / compressed_bytes; round-trip bit-identical source; end-to-end retrieval p95 not just decompression microbenchmarks; p99 index RAM; tokens avoided and provenance/recall fidelity. A 1000x universal lossless compression guarantee violates information-theoretic limits for arbitrary already-compressed input. Lossy semantic representation may be compact but cannot be represented as an exact replacement for original source.

## Q. Knowledge replication, deletion and provenance

Use versioned signed manifests naming immutable blocks; lightweight nodes store relevant allowed shards, stronger storage peers mirror more. Replicate based on measured availability and legal region; checksums + availability sampling; erasure coding only after comparing CPU and repair costs. Source-knowledge entries carry origin, license, consent, timestamp, review status, subject and expiry. Independent clients verify hash and trust signatures before retrieval.

Privacy: local-first secrets, end-to-end encryption for private requests where compatible with computation (processing nodes see plaintext if necessary unless privacy-preserving compute is used), per-user encryption keys, per-purpose access-control. A decentralized system must acknowledge deletion is difficult after untrusted replication; prevent initial public release of private data in the first place.

## R. Mobile resource contribution and Android UX

Android app contains **Chat mode** independent of **Volunteer Node mode**. Node onboarding makes resource use visible: CPU cap slider, RAM, storage, daily MB, charging-only, Wi-Fi/unmetered-only, idle-only, screen/temperature and schedule, estimated battery and electricity cost, instant pause. No promise of uninterrupted 24/7 compute from background mobile OS; use WorkManager constraints for deferrable batches and OS-appropriate foreground services *only when genuinely allowed*. Follow Android/Play policies, minimize long-running wake locks, and show actual resource stats.

**Cloud/desktop preference:** persistent low-latency model workers should be on reliably powered authorized servers/desktops; mobile nodes mainly support bounded batch jobs, cache, evaluation and opt-in learning. Avoid storing another user's raw private request on commodity phone if privacy and data jurisdiction cannot be guaranteed.

## S. Identity, authorization and security threat model

Threat classes: remote code execution via task payload, prompt injection via retrieved content/tools, model weight tampering, supply-chain compromise, wallet/credit theft, Sybil identities, colluding validators, poisoning, reward gaming, model extraction, training data leakage, encrypted traffic correlation, location inference, flooding/DDoS, malicious IoT action and false hardware metrics.

Controls: signed binaries/manifests, reproducible builds where feasible, SBOM/dependency scans, minimal OS permissions, memory/CPU/IO sandbox, no shell by default, no arbitrary external URLs in worker tasks, explicit egress deny, mTLS/Noise peer authentication, schema-bound parsing, nonce and expiration, rate limits, key rotations, multi-party critical releases, security disclosure, emergency rollback. Trust boundaries must be tested with adversarial peers; cryptographic signatures do not establish computation was correct.

**Safety:** knowledge about harmful phenomena may support prevention; action policies and permissions still prohibit harmful deployment. Always preserve local exit, owner control, transparency and incident handling. Avoid unsupported 100% no-harm claims. Safety is measured via independent evaluation and audited deployment constraints, not a one-time "filter".

## T. Self-improvement research control loop

1. Detect anonymized aggregate regression, measured bottleneck or openly submitted research hypothesis.
2. Generate alternative module/configuration or training experiment under fixed CPU/energy budget.
3. Execute only in sandbox with synthetic/public or consented training data, reproducible seeds and reserved validation set.
4. Test baseline vs candidate across multiple domains, confidence intervals, safety/privacy checks and license compatibility.
5. Independent reviewer/threshold-signed approval of release manifest (not automatic copy of a malicious worker's output).
6. Canary rollout to controlled opted-in nodes, telemetry and automatic rollback when threshold regression detected.
7. Log decision and lessons; never treat model self-reported success as evidence.

**Research evaluation dimensions:** objective correctness, generalization, transfer, catastrophic forgetting, hallucination, toxicity/safety, unintended data retention, average and tail latency, CPU Joules/task, memory bytes, robustness under dropouts and fairness among tiers.

## U. Resilience and multigenerational hardware portability

No network can be guaranteed alive forever. Improve reconstitution: open portable specs, multiple maintainers/archives, replicated encrypted snapshots, immutable verified releases, reproducible build docs, succession governance, community mirror rights and independent bootstrap paths. Test a **cold-start restoration** scenario: after all current coordinators disappear, a handful of nodes restore routing and public model manifests from signed snapshots without privileged secrets.

Hardware adapters: model IR / stable portable graph (e.g. ONNX where applicable); CPU kernels as reference; optional GPU/NPU backends; architecture features negotiated through versioned profile; endian/ISA/quantization validation; no binary blob requirement for learning protocol. Migrations use compatibility scan → dry-run inference with golden vectors → performance/energy bench → owner approval → staged copy → checksum → switch → reversible rollback. Never relocate private owner data without permission.

**Quantum future:** define optional `AcceleratorBackend` for specific algorithmic primitives and future hybrid workflows. Quantum machines do not replace conventional CPU logic for everything; fault-tolerant hardware, workload mapping, data-loading and error correction matter. Use a classical simulator as baseline, measure quantum benefit against best classical algorithms only when real hardware and access exist. Post-quantum cryptography should be evaluated separately from quantum AI acceleration; plan crypto agility based on evolving standards.

## V. Network partitions, failovers and emergency recovery

**Partition policy:** preserve local owner control and read-only public knowledge; allow bounded offline task work with signed timestamps; disallow final authoritative credit spend / globally promoted models without required quorum. After healing, reconcile idempotent receipts and reject conflicts. Leased tasks may be rescheduled after expiry, but only one settlement is accepted. Restore snapshots from independent signers and verify hashes.

**Emergency kill mechanisms:** revoked compromised release hash, blocklist dangerous task types, per-device stop, and distributed emergency approval. Keep governance accountable and temporary; network survival does not override user's right to uninstall or disconnect. Incident runbooks specify data breach response, revoke leaked credentials, preserve minimal forensic artifacts and report as applicable.

## W. Foundation, nonprofit, subscriptions and transparency

**Proposed:** TONG AI Foundation, possibly Australian company limited by guarantee, subject to legal advice/registration. A not-for-profit may sell subscriptions and pay reasonable salaries, reinvesting surplus in its mission. A registered charity requires distinct eligibility for charitable public-benefit purpose; tax-deductible gift status is separate. Public promises must not imply registration exists now.

**Revenue:** subscriptions, permitted donation/grants, approved enterprise hosted services, optional philanthropy. **Outflows:** dedicated CPU/GPU servers, colocation/cloud, internet transit, power/cooling, support, audits, insurance, security, maintenance, development salaries and reserves. **Monthly dashboard:** gross/net revenue by type, actual OPEX by category, procurement invoices redacted, model-serving electricity estimates and methodology, capacity utilization, committed vs available reserves, conflict-of-interest statements and independently reviewed financial reports when feasible. Do not post employee personal banking details, passwords or security-sensitive topology.

**Paid service fairness:** explicitly disclose speed/quality workload definitions, limits, cancellation/refunds and response to outages; no right to misuse other participants' data. Foundation-owned server surplus may serve lower tiers only where users and privacy policy permit, without compromising paid reservations. Community compute should not subsidize paid service without transparently consented terms and appropriate credit allocation.

**Pro forma budget, example ONLY:** monthly revenue = `subscriptions × collected_price + grants + donations`, operating surplus = revenue − compute rental − transit − staffing − compliance − tax/fees − reserve allocation. Do not claim zero cost because founders donate time. Compare purchase vs lease total cost of ownership: capex depreciation, electricity, cooling, repairs, network, colocation, warranty and depreciation/obsolescence. Prefer funded pilots before buying assets.

## X. Privacy laws, user rights and public-interest commitments

Privacy principles: explicit granular opt-in for learning, purpose limitation, minimal collection, access audit, retention caps, export, correction, revocation, lawful basis and regional processing controls. A user may stop donating compute without losing basic free access. A contributor who does not share private chats must still be able to earn TC for lawful verified compute. Separately obtain any necessary lawful rights to datasets and outputs.

Independent privacy and legal review before public deployment in AU and other jurisdictions. Avoid exposing per-user interaction logs in transparency reporting. Network should log aggregate utilization, not a globally public transcript. Device diagnostics are themselves potentially sensitive, so minimize exact location/IP retention. Apply child protections where legally required; do not assume all users can consent to all data use.

## Y. Engineering stack and repository architecture

Proposed technology selection (all decisions subject to ADR/benchmarks):

| Subsystem | Candidate stack | Reason / caution |
|---|---|---|
| Node and transport | Rust + rust-libp2p + QUIC | Performance, type safety; NAT and binding complexity |
| CPU model inference | llama.cpp / GGUF, ONNX Runtime where legal | Mature CPU paths; actual models may be too slow |
| Gateway/chat UI | TypeScript/Web UI; Kotlin Android later | Accessibility and consent UI; no shared secrets |
| Control / scheduling | Rust or Python research prototype → Rust | Unit-test policies and measured latencies |
| Local metadata | SQLite first; RocksDB if proven needed | Crash safety and portable storage |
| Compressed chunks | Zstandard, LZ4, SHA-256/BLAKE3 with context | Speed vs ratios; inspect dependency licences |
| Learning | PyTorch CPU tiny models; PEFT where useful | Separate actual training from retrieval memory |
| Research distributed learning | Flower / Hivemind experiments | Not turnkey privacy or robust internet inference |
| Observability | OpenTelemetry-compatible metrics, privacy-filtered | PII redaction and sampling required |
| CI | GitHub Actions public stdlib checks | CI not a free always-on training server |
| Finance reporting | Public audited exports, manual first | No bank credentials in public dashboards |

Folder responsibility: `protocol/` versioned wire format; `nodes/` owner consent and runtime; `models/` adapters/cards; `memory/` CUME experiments; `benchmarks/` reproducible baselines; `prototype/` CPU sandbox; `docs/` architecture, FAQ, ADR, handoff; `foundation/` proposed legal/accounting templates; `.github/` PR/issue/CI templates. Prefer monorepo until ownership and build separation justify multiple repos.

## Z. Roadmap, proof points, hard stop criteria and day-one execution

### Phases and proof gates

**M0 (today):** create public repo with this package; run FAQ counter and test; enable PR review; keep honest status. No infrastructure purchases.

**M1:** implement two independent authenticated CPU processes and signed task receipts, compare scheduler against local-only baseline; show verified work and crash recovery. Provide exact reproducible commands, synthetic tasks and model-agnostic transport.

**M2:** volunteer LAN and WAN pilots (2, 5, 20 nodes); measure ability to pool *parallel* compute, peer churn, network egress, battery, energy and timeouts; publish counterexamples where P2P is slower.

**M3:** compressed provenance-backed memory, tiny continual learner, constrained CPU experiments, independent holdouts and private-learning checks; demonstrate new capability learned on unseen tasks without regression beyond predefined bound.

**M4:** validator quorum, production-credit prototype, tier quotas, community security audit and owner controls; simulate fraud, partitions, double spend and overload.

**M5:** Android node and chat, specialised adapters, local/offline mode, fallback to supervised dedicated serving where legal; rigorous platform battery constraints.

**M6:** funded dedicated paid performance trial and reporting; register foundation only once legal/accounting research and governance warrant it; do not launch billing until actual infrastructure, consumer terms, data processing and incident response exist.

**M7+:** domain experts, video/audio/robotics tool integrations (each licenced and measured), distributed model research, hardware migration, quantum experimental adapter.

### Concrete acceptance matrices

| Dimension | First measurable criterion | Failure that blocks promotion |
|---|---|---|
| CPU baseline | Same tests on 1 and 2 CPUs with raw timestamps and hardware spec | P2P speed claim lacks controlled baseline |
| Routing | At least 100 short mixed-category synthetic requests, p50/p95 measured | Classifier misroutes sensitive tasks, cache leaks cross-user data |
| Privacy | Opt-in logs verified; private chat not transmitted to unrelated peer | Any unconsented private sharing |
| Credits | duplicate receipt never credited twice; no negative balances | Offline concurrent double spend succeeds |
| Training | held-out unseen gains + bounded forgetting + privacy attack review | Candidate passes only memorized examples |
| Memory | 100% checksum verified lossless round trip when marked lossless | Corrupted chunks silently accepted |
| Resilience | kill one peer mid-task; recover without duplicate settlement | Can no longer revoke jobs or loses ledger correctness |
| Android | user stop cancels bounded job and reduces sustained load | Background battery drain violates disclosed limits |
| Paid speed | publish test workload, model, client region and TTFT/full p95 | 3-second marketing claim unsupported |
| Governance | reviewer approvals and incident actions in public auditable records | One hidden admin can bypass all controls |

### 24-hour developer launch plan (no claims of background autonomous work)

**Hour 0–2:** create repo, import files, verify docs count and tests, turn on rulesets. **Hour 2–6:** open ADR and issues for signed transport, simple resource scheduler, credit receipt. **Hour 6–12:** make two local CPU processes communicate over localhost with authenticated task IDs; **Hour 12–18:** run 100 deterministic jobs and compare local vs remote latency and bytes; **Hour 18–24:** commit reproducible results, failure cases and a comprehensive updated HANDOFF. Times are planning estimates, not promises.

### Decision rubric for every proposed improvement

Ask: Does it improve *measured* quality, p95 latency, Joules per useful answer, model accuracy, device autonomy, privacy or sustainability? What new costs and risks does it introduce? Is it replicable without proprietary APIs? Can an older node ignore it safely? Can it be rolled back? If not demonstrably better, keep it experimental.

---

## AA. Detailed protocol design starter — sample schemas

Protocol examples below are conceptual, not accepted wire-format standards or working deployed APIs.

```json
{
  "message_type": "NODE_CAPABILITY",
  "protocol_version": "0.1-draft",
  "node_key_id": "hash-of-public-key",
  "sequence": 101,
  "valid_until_unix_ms": 1793600000000,
  "hardware": {"cpu_threads_allowed": 2, "ram_mib_limit": 2048, "accelerators": []},
  "task_types": ["deterministic-eval", "public-text-inference"],
  "max_upload_mib_day": 100,
  "constraints": {"charging_only": true, "unmetered_only": true},
  "model_hashes_warm": [],
  "signature": "placeholder-signature"
}
```

```json
{
  "message_type": "TASK_OFFER",
  "task_id": "random-128bit-id",
  "model_manifest_hash": "sha256:...",
  "task_kind": "deterministic-eval",
  "privacy_label": "public-synthetic",
  "input_hash": "sha256:...",
  "deadline_unix_ms": 1793600100000,
  "cpu_ms_limit": 500,
  "mem_mib_limit": 512,
  "idempotency_key": "unique-per-request",
  "offer_signature": "placeholder-signature"
}
```

**Validation:** enforce canonical serialization, version negotiation, max message lengths, time skew policy, signature coverage over all meaningful fields, no secret inside a gossip topic, replay nonce store and expiry. Never rely on hash alone for authorization.

## AB. Scheduling algorithm pseudocode

```python
# PSEUDOCODE — not the entire implementation
request = classify_with_minimal_metadata(user_request)
candidates = discover_from_local_and_replicated_cache(request.task_type)
eligible = [n for n in candidates if
    n.owner_consent_active and n.model_licensed_and_warm and
    n.resources_sufficient and n.privacy_zone_allows(request) and
    n.tier_pool_allows(request.tier) and n.verified_recently]
for n in eligible:
    n.predicted_ms = (n.p95_rtt_ms + n.p95_queue_ms +
        n.p95_prefill_ms + request.expected_output_tokens / n.sustained_tps * 1000 +
        n.safety_validation_ms)
worker = min(eligible, key=lambda n: n.predicted_ms) if eligible else None
# on lease failure, retry at most bounded times with request idempotency preserved
```

**Important:** privacy, licences, trust and user consent are *hard eligibility conditions*, never scoring terms that can be bypassed by extremely fast performance.

## AC. Research questions and potential falsifiers

R1: Does constrained P2P task dispatch reduce *mean energy per successfully completed useful job* vs a central CPU baseline? R2: Does distributed memory lower storage and retrieval cost without unacceptable leakage or latency? R3: Can independently validated tiny online updates improve out-of-distribution skill transfer without catastrophic forgetting? R4: Is a heterogenous CPU expert network better in quality-per-Joule than a single larger CPU model? R5: Do traffic-aware regional peers lower p95 TTFT vs centralized control? R6: Can credits elicit useful validated work without profitable Sybil/spam attacks?

Record *negative* results and failures, not just wins. Reject any "fundamentally new architecture" claim until comparisons against strong, matched baselines demonstrate novelty and performance.

## AD. Foundation operations and finance dashboards (future, not deployed)

Monthly public records: reporting period, foundation legal ID if registered, funding by subscription/donation/grant, beginning/end cash balance, platform inference rental and machine depreciation, staff total expense, storage/bandwidth, electricity/power usage estimates, network validator grants, security audit and compliance, reserve months, incident costs and ethics/bias audit funding. Keep immutable signed publication hashes and revised/annotated restatements, protecting individual salaries/PII where required while still publishing aggregated wage costs.

Board policies: spending approval thresholds, related-party disclosures, procurement comparisons, audited annual statements where legally required, donor restriction tracking, conflict procedures, community advisory process and continuity funding reserve. Maintain independent ownership of domain/source/release signing keys and financial credentials; resist founder single-point-of-failure.

## AE. Sources for technical and legal verification

**Official, evergreen reference entry points** (always recheck current releases/terms at implementation time):

- GitHub repository creation: https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository
- GitHub rulesets: https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/creating-rulesets-for-a-repository
- GitHub Actions pricing/limits: https://docs.github.com/en/actions/concepts/billing-and-usage
- Android WorkManager constraints: https://developer.android.com/develop/background-work/background-tasks/persistent/getting-started/define-work
- libp2p specification: https://github.com/libp2p/specs
- Rust libp2p: https://github.com/libp2p/rust-libp2p
- Hivemind: https://github.com/learning-at-home/hivemind
- Flower: https://github.com/adap/flower
- llama.cpp: https://github.com/ggml-org/llama.cpp
- ONNX Runtime: https://github.com/microsoft/onnxruntime
- Zstandard: https://github.com/facebook/zstd
- LZ4: https://github.com/lz4/lz4
- ACNC not-for-profit: https://www.acnc.gov.au/for-charities/start-charity/not-for-profit
- ASIC structures: https://www.asic.gov.au/for-business-and-companies/nfps-and-charities/registering-and-structuring-not-for-profit-organisations
- ACNC charity requirements: https://www.acnc.gov.au/for-charities/start-charity/you-start-charity/who-can-apply-be-registered
- Apache License 2.0: https://www.apache.org/licenses/LICENSE-2.0

These references justify *candidate tooling and legal questions*, not claims that they collectively form a ready-made decentralized general intelligence system. Data protection, charity registration and payments require qualified professional review before launch.