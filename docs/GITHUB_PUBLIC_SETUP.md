# Publish the TONG AI starter files to GitHub (start-to-finish)

**Current verified project repository:** https://github.com/parmtech/tong-ai (public, empty at last check on 2026-11-02). **Kickoff issue:** https://github.com/parmtech/tong-ai/issues/1. Skip initial repo creation steps if using this existing repo; do not recreate it.

**Before beginning:** Decide whether the repository should live under an existing organization or personal account. A proposed "TONG AI Foundation" is *not* a currently registered legal entity; do not describe it as one.

## Browser / Android-friendly route
1. Sign in and open **https://github.com/new**.
2. Select the GitHub owner/account that should host the project. Choose repository name **`tong-ai`** (use `tong-ai-research` if already taken on that account).
3. Add description: `Open-source, CPU-first decentralized collective-intelligence research network`.
4. Select **Public**. Leave initial README, `.gitignore` and license *unchecked* if you will push this complete scaffold, avoiding conflicting histories.
5. Click **Create repository**. A blank repository is now ready to receive files.
6. On a computer with Git installed, extract `TONG_AI_GitHub_Starter.zip`, then from its `tong-ai` folder run (replace YOUR_OWNER):

```bash
git init -b main
git add .
git commit -m "docs: establish TONG AI public research blueprint and 1000 FAQs"
git remote add origin https://github.com/YOUR_OWNER/tong-ai.git
git push -u origin main
```

7. Without a computer: GitHub's web **Add file → Upload files** lets you upload extracted files, but nested directories and large file sets may be cumbersome on mobile. GitHub does not automatically expand a ZIP uploaded as a single file into a repository tree; use a Git client or desktop for the full scaffold.
8. In **Settings → Rules → Rulesets** add a ruleset for `main`: require pull request, status checks and review; restrict force pushes and deletion. Be aware of ruleset feature availability/administrative bypass rules.
9. **Settings → Actions → General**: keep actions permissions minimal, no write token on untrusted fork PRs, approve third-party workflows before relying on them. The included CI runs local standard-library tests and documentation QA.
10. Enable **Discussions** for architecture debate, **Issues** for tasks, a `good first issue` label and **Security → Private vulnerability reporting** if available.
11. Commit a change to `docs/handoff/HANDOFF.md`, `docs/handoff/CHANGELOG.md` and a PR describing every substantive update. Record decisions as ADRs.

## Verify
```bash
python3 -m unittest discover -s tests -v
python3 tools/validate_docs.py
```

Expected: simulator tests pass and **exactly 1000 unique FAQ IDs** are found. The file-count and size may change as the community develops. No GitHub repo is created by the starter package alone.

## Useful official documentation
- https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository
- https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/creating-rulesets-for-a-repository
- https://docs.github.com/en/actions/concepts/billing-and-usage

## Release gate
The first public release is a research-design milestone. Do not advertise production AI inference, community-credit value, a foundation or decentralized training until demonstrated and documented.