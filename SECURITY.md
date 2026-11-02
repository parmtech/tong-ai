# Security Policy (pre-release)

**Status:** no production service is deployed. Do not post vulnerabilities, passwords, credentials, user datasets or exploit instructions in public issues. Contact maintainers privately via GitHub private vulnerability reporting when enabled. Proposed response targets (not service guarantees): acknowledge within 5 business days; triage severity; patch and rotate credentials as needed; disclose after mitigation.

Every device opts in and can stop locally. No remote `execute arbitrary code` endpoint; run allowlisted, sandboxed tasks with CPU/memory/network/time quotas; signed artifacts and protocol-version checks; per-task data minimization; strict egress restrictions for untrusted jobs. Never trust node-declared performance, public IPs, model outputs or validator attestations unconditionally. Credits are not money; if this ever changes, redesign security and legal controls first.

Threat-model at minimum: Sybil nodes, poisoning, prompt injection, exfiltration, traffic correlation, replay, double spend, malicious updates, validator collusion, coordinator capture, dependency supply chain, privacy inference from model gradients and Android abuse.