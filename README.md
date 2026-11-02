# TONG AI — Open Collective Intelligence Research

**Stage:** public-repository starter kit / architecture design; **not** a deployed AI network or production-trained foundation model. **Version:** `0.1.0-docs` · **Date:** 2026-11-02.

> **Punjabi:** TONG AI ਇੱਕ ਖੁੱਲ੍ਹਾ, CPU-first, peer-to-peer AI research project ਹੈ। ਇਸਦਾ ਮਕਸਦ ਦੁਨੀਆ ਭਰ ਦੇ ਸਹਿਮਤੀ ਦੇਣ ਵਾਲੇ devices ਦੀ compute ਅਤੇ knowledge ਨੂੰ ਸੁਰੱਖਿਅਤ ਤਰੀਕੇ ਨਾਲ ਜੋੜ ਕੇ ਘੱਟ energy ਵਿੱਚ ਵਧੀਆ intelligence ਵਿਕਸਿਤ ਕਰਨਾ ਹੈ। ਇਹ ਹਾਲੇ research ਅਤੇ design stage ਵਿੱਚ ਹੈ; ਕਿਸੇ commercial model ਨੂੰ ਪਿੱਛੇ ਛੱਡਣ ਜਾਂ ਹਰ ਜਵਾਬ 3 ਸਕਿੰਟ ਵਿੱਚ ਦੇਣ ਦਾ ਦਾਅਵਾ ਨਹੀਂ ਹੈ।

## Vision
Build a permissioned-by-device-owner but decentralized *collective intelligence fabric*: heterogeneous CPU-first nodes offer bounded compute, specialised model services and validated learning contributions. A distributed control plane routes requests to the best available *eligible* node(s) rather than treating internet-connected CPUs as a magical shared processor. Improve inference latency, accessibility, resource efficiency, and measured learning over time while respecting user agency and public-benefit governance.

**Collective consciousness** is a metaphor for collective coordination, memory and intelligence, **not** a claim of subjective consciousness. TONG AI is distinct from TongNet unless future contributors formally decide otherwise.

## Fixed service-tier policy
| Priority | Plan | Workload placement | Access |
|---|---|---|---|
| 1 | **Paid** | Foundation-owned/leased dedicated high-performance hardware and fast network, with top scheduling priority | Most capable model *actually available*; speed/reliability targets and transparent subscription terms |
| 2 | **Contributor Credits** | Eligible community/shared nodes, credit-aware fair scheduling | Earn non-transferable service credits for *verified* work; credits fund greater usage |
| 3 | **Free** | Lower-priority shared capacity | Limited fair access; local/offline features wherever supported |

All tiers use **the same evolving collective network and protocols**. Separate compute pools and resource priorities do **not** mean separate collective minds. No paid deployment or service exists yet; the foundation is proposed, not incorporated.

## Start here
1. [A–Z Blueprint](docs/BLUEPRINT_A_TO_Z.md) — full architecture, roadmap, business, privacy, research, hardware, acceptance gates.
2. [1,000 Technical FAQs](docs/faq/FAQ_1000.md) — exactly 1,000 technically focused questions and detailed answers in 25 domains.
3. [Handoff / Current State](docs/handoff/HANDOFF.md) — what exists, what's planned, decisions, blockers, precise continuation instructions.
4. [Project Roadmap](ROADMAP.md), [Public Repo Setup](docs/GITHUB_PUBLIC_SETUP.md) and [Decision Log](docs/adr/README.md).
5. [Minimal CPU routing simulator](prototype/README.md) — local *simulation only*, not P2P training or LLM inference.

## Zero-cost principle
The starter repository needs no paid API or server; CI uses public-repository standard hosted runners subject to GitHub policies. Free/public GitHub does not provide an unlimited 24/7 AI training cluster. Hardware, electricity, hosting, mobile data, legal formation and uptime all have real costs even if volunteers absorb some.

## Responsible community participation
- Public contributions through forks and pull requests; no unreviewed merge to `main`.
- Node owners choose CPU, RAM, network, charging, time and privacy limits, and can stop.
- Private conversations are **never automatically published to all peers or fed into training**; learning feedback is explicit opt-in, minimised, secured and independently checked.
- Automatic experiments in isolated environments can propose changes; production promotion requires independently verified tests, approvals and rollback.
- Devices must never be enrolled, scanned or controlled without owner authorization.

## Contribute
Read [CONTRIBUTING.md](CONTRIBUTING.md), [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md), [SECURITY.md](SECURITY.md), and [GOVERNANCE.md](GOVERNANCE.md). Please attach reproducible benchmarks to claims of speed, quality, compression or energy savings.

## License
Original repository code and documentation are offered under **Apache License 2.0** (see `LICENSE`) unless marked otherwise. Third-party code, model weights and datasets **retain their own terms**; see [Legal and Attribution](legal/THIRD_PARTY_POLICY.md). The project name and marks are not automatically licensed as trademarks.

## Accurate public status
- ✅ Documentation scaffold, initial detailed plan, governance templates, and 1,000-FAQ knowledge base assembled.
- 📦 CPU-only **offline simulator** and tests exist in the downloadable 40-file starter ZIP, but their source files are not yet committed to GitHub.
- ❌ No live decentralized deployment, trained frontier model, nonprofit registration, paid subscription or 3-second production SLO achieved.

**Next maintainer action:** import the remaining starter ZIP files (including `LICENSE`, simulator, tests and CI); configure branch rules, publish topics, run CI, and update this handoff. See [Issue #1](https://github.com/parmtech/tong-ai/issues/1).