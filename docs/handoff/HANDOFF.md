# TONG AI — Live Handoff / Single Starting Point

> **GitHub status update (2026-11-02):** Public repository `parmtech/tong-ai` is active. The README, A–Z blueprint, 1,000 technical FAQ, governance and core handoff documents have been committed. GitHub Issues and Discussions are enabled, with kickoff [Issue #1](https://github.com/parmtech/tong-ai/issues/1). **This is a partial docs import:** the full 40-file starter ZIP (including LICENSE, CPU simulator, test suite and CI workflow) has **not** yet been fully committed. GitHub repository topics are not configured. Next action: import remaining files from the prepared ZIP, verify 1,000 FAQ and 10 tests locally/CI, add topics and branch protection. Do not claim the executable demo is in the repository until verified.

**Document status:** baseline handoff created 2026-11-02; version `0.1.0-docs`; publication awaiting first source commit. **Verified public repository:** https://github.com/parmtech/tong-ai (empty at last check). **Kickoff issue:** https://github.com/parmtech/tong-ai/issues/1. **Owner/maintainer:** GitHub account `parmtech`; community maintainer roles not yet assigned. **Last confirmed activity:** public repository and Issue #1 created; starter files assembled and tested locally, not pushed.

## Absolute project identity
TONG AI (T-O-N-G AI). No Aakaash AI naming going forward; historical mention only in archival notes. Separate from TongNet unless a later approved ADR says otherwise. Research concept, not an active artificial consciousness or deployed AGI.

## Mission, immutable user constraints unless changed through ADR
- Open-source/public contribution workflow and independent code review.
- CPU-first ultra-low-energy/low-RAM experiments; optional GPUs, NPUs and future quantum accelerators.
- Collective network where nodes can safely share bounded compute, validated knowledge and consented learning contributions; no forced raw-private-chat disclosure.
- Logical collective coordinator lives as a distributed protocol, not a master server; smart node placement measured by actual speed, latency, RAM, model load, trust, power and owner limits.
- Aim for early streaming and sub-3-second *small* answer p95 on suitable paid dedicated hardware; **not yet demonstrated** and never a guarantee for long responses.
- Three tiers: **Paid (highest priority, reserved foundation high-end hardware)**; **Contributor Credits (second priority on eligible shared nodes)**; **Free (third priority with caps)**, all sharing one collective research ecosystem.
- Volunteer credits earned only for independently validated computation/contributions; non-transferable non-cash service units, double-spend resistant ledger required before production.
- Proposed Australian public-benefit non-profit foundation and public reports on subscriptions, donations, server maintenance, power, salaries, bandwidth and reserves; none currently established.
- Continual improvement through opt-in feedback, sandboxed experiments, evaluation and versioned rollback; absolute zero harm/zero compute/immortality/self-awareness are not scientifically or operationally guaranteed.

## What exists today (file paths)
- `README.md`: launch overview and honest status.
- `docs/BLUEPRINT_A_TO_Z.md`: full plan, protocols, RFCs, security, implementation and research gates.
- `docs/faq/FAQ_1000.md`: exactly 1,000 numbered FAQ entries / 25 domains; `tools/validate_docs.py` checks numbering and count.
- `docs/GITHUB_PUBLIC_SETUP.md`: steps for creating the public GitHub repository and pushing extracted scaffold.
- `docs/MEASUREMENT_PROTOCOL.md`, `docs/PRIVACY_CONSENT_DESIGN.md`, `docs/OPEN_SOURCE_RESEARCH_MATRIX.md`: testing, consent and third-party research policy.
- `foundation/FINANCIAL_TRANSPARENCY_SPEC.md`: proposed nonprofit finance dashboard.
- `tools/build_faq.py`: curated 250-mechanism source and deterministic FAQ generator.
- `ROADMAP.md`, `GOVERNANCE.md`, `SECURITY.md`, `CONTRIBUTING.md`, `legal/THIRD_PARTY_POLICY.md`, ADRs.
- `prototype/`: CPU-only offline routing/credit simulation; **NOT live distributed inference**.
- `tests/`: ten passing standard-library unit tests; `.github/workflows/docs-and-tests.yml`: FAQ/test checks on PR/push and a PR check requiring both handoff and changelog edits.
- `docs/ARCHIVE_INITIAL_BLUEPRINT_v0.1.md`: historical concept draft.
- `docs/handoff/CHANGELOG.md`: dated changes.

## What does NOT exist
No source files committed to the now-created GitHub repository, deployed network, Android APK, node transport, trained foundation model, community compute pool, production credit ledger, payments, foundation legal registration, proof of 3-second results, secure aggregation implementation or independent safety audit. All examples and targets are proposals.

## Immediate next action for the *next* agent or human
1. Inspect `git status`, recent commits, open Issues/PRs, workflow runs, CODEOWNERS and this handoff; compare actual repo state to this document.
2. Confirm `parmtech/tong-ai` and kickoff Issue #1; as of 2026-11-02 it is public but has no source commit. Do not claim the source is published until verified.
3. Import scaffold, run `python3 -m unittest discover -s tests -v` and `python3 tools/validate_docs.py`; record exact output and commit ID.
4. Configure main branch protections, security reporting, Discussions, code owners and least-privileged Actions.
5. Start M1: implement real signed two-process authenticated CPU task exchange; measure single CPU baseline, peer latency, network bytes, verified receipts, resource use, retry and stop.
6. Capture blockers, rejected experiments, costs, benchmark device specifications and security decisions in the sections below; create ADRs for changed assumptions.

## Progress status table
| Item | Status | Evidence / next gate |
|---|---|---|
| A–Z blueprint | Draft written | Community and technical review required |
| 1,000 FAQs | Draft written | Count validator; answers require topic owner audit as research changes |
| Tier policy | Recorded in ADR-0002 | Load test only after actual infrastructure |
| GitHub repo | **Created, empty** (verified 2026-11-02) | https://github.com/parmtech/tong-ai ; Issue #1 ; first source commit pending |
| CPU routing simulation | Included | Local tests; not networked |
| P2P CPU prototype | Not implemented | M1 signed job/receipt test |
| Android volunteer client | Not implemented | M5 OS/battery tests |
| Real privacy-preserving learning | Not implemented | M3 research safety gate |
| Foundation legal entity | Not incorporated | Independent AU legal review |
| Paid service / dedicated server | Not operating | Funded deployment and load tests |

## Update-this-on-every-change contract (required)
- Record exact file paths and feature/bug/research issue, date/time UTC, branch, PR and commit SHA.
- Capture **before → after** behaviour, environment, dependencies, configuration and any data migrations.
- Record unit/integration/security/benchmark results including failures, logs or links, plus what was *not* tested.
- Explain privacy/legal/safety/CPU-energy impact and whether new external data/model licenses were checked.
- Add rollback/recovery instructions, owner, outstanding blocker and next explicit step.
- Update this file and CHANGELOG **in same PR**; write ADR for architectural changes. Git is the source of exact smallest edits; this handoff provides the navigable state.
- Never overwrite a failed experiment with an invented success or silently erase historic blockers.

## Open design decisions / blockers
- Choose reproducible P2P library and remote task sandbox after M1 threat model.
- Define cryptographic node ID lifecycle and delegated validators.
- Choose conflict-resolution semantics for decentralized credit ledger (signed receipts alone do not prevent double spend).
- Formalize *measured* price points, quotas, earnings, reserve and anti-fraud economics.
- Decide opt-in learning formats and retention/deletion semantics with privacy counsel.
- Obtain legal advice about organization structure, subscription obligations, Australian privacy law and global users.
- Choose reference small, appropriately licensed model and quantify costs on diverse CPUs.
- Validate that any neural-weight sharing beats local training on WAN; expect many workloads will not benefit.

## Handoff template for every PR
```text
Date (UTC):
Issue / PR / commit:
What changed (paths):
Why / assumptions:
Before -> after:
Exact test and benchmark commands + outputs:
Security / privacy / licensing review:
Energy / latency / cost impact:
Open regressions / blockers:
Rollback instructions:
Next smallest action + owner:
```

**Next agent:** do not repeat speculative claims as finished work. Start here, verify GitHub against this document, read the FAQ and the relevant blueprint chapter, then work in the smallest tested PR.