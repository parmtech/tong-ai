# Contributing to TONG AI

Any contributor may fork and propose changes. **Nobody gets automatic direct write access to the protected default branch**; openness means reviewable participation, not arbitrary remote control of users' devices.

1. Open an issue with use case, proposal, privacy implication, CPU/RAM/energy budget and measurable success criterion.
2. For architecture or rules changes, submit an ADR (`docs/adr/NNNN-topic.md`) with context, options, decision and tradeoffs.
3. Implement the smallest reviewable change with tests, documentation, benchmark environment and security analysis.
4. For learning updates, provide dataset/teacher license and provenance, explicit consent, contamination checks, held-out results, reproducible hashes, and rollback plan.
5. Open a pull request using the included template. Two independent reviewers are recommended for security/protocol/ledger/privacy changes; maintainers establish CODEOWNERS once identities exist.
6. **Every merged PR** must update `docs/handoff/CHANGELOG.md` and `docs/handoff/HANDOFF.md` (or explain explicitly why no handoff state changed). The PR itself is the authoritative line-by-line code diff. Changes impacting design update the blueprint/ADR too.

Non-negotiables: no personal-data dumps; no secrets; no undisclosed device resource consumption; no malicious code, obfuscated binaries or unsafe self-replication; no unverifiable "always fast" claims. Report vulnerabilities privately per `SECURITY.md`.