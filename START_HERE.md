# First-commit quick start — TONG AI

**You have a complete research-documentation starter, not a running decentralized AI.**

1. Read `README.md`, `docs/BLUEPRINT_A_TO_Z.md` and `docs/handoff/HANDOFF.md`.
2. Public repository is already created: **https://github.com/parmtech/tong-ai** (empty as of 2026-11-02). Kickoff tracking: **https://github.com/parmtech/tong-ai/issues/1**.
3. Push all **extracted** files, not the ZIP archive as a single repo file; see `docs/GITHUB_PUBLIC_SETUP.md`.
4. Run `python3 tools/validate_docs.py` → must report exactly 1000 answers; run `python3 -m unittest discover -s tests -v` → ten tests should pass.
5. Enable `main` rules requiring PR reviews and passing checks; no unreviewed changes directly to main.
6. Make handoff and changelog changes in every PR. Git commits keep exact line-level history; the handoff tells the next agent what is *really implemented*, verified and next.
7. Follow GitHub Issue #1 for first-commit import and the M1 authenticated two-process CPU task demo. **Source files are not yet published to the repository**; check the live repository before assuming otherwise.

**Caution:** No existing nonprofit incorporation, hosted paid service, 3-second guaranteed chat, CPU peer network, trained polymath model or self-aware AI is claimed.