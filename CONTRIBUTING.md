# Contribution Workflow

> **Scope:** This document defines how we contribute via GitHub, how reviews work, who reviews, timelines (SLA), and what “good peer review” means. It also records current Senior Reviewers and the current mentor for the trimester.

---

## 1) Branching & Source of Truth

- **Default branches:**
  - `main` — stable, release-ready, synced by the mentor only.
  - `development` — integration branch; **all PRs target this branch**.
- **Fork workflow:**
  - Everyone works from a **personal fork**. No direct pushes to `AAIE/*` repos.
- **Protected branches:**
  - `main` and `development` are protected (no force-push, no direct push, merge via PR only).

---

## 2) Roles

- **Author** (PR creator): responsible for getting their change merged end‑to‑end.
- **Peer reviewers (2)**: any team members with relevant context.
- **Senior reviewer (1)**: a Domain Lead or Project Lead (see list below).
- **Mentor (current trimester)**: syncs `main` with `development`, unblocks and coordinates releases.
- **Leaders**: provide direction, do not assign reviewers.



---

## 3) Contribution Flow (Step‑by‑Step)

> **Update:** Feature branches are optional. Default is to work on your **fork's `development`** branch and open a PR to the upstream `development` branch.

**One-time Setup (per machine)**

1. **Fork** the repo on GitHub to your account.

2. **Clone your fork** and add the official repo as `upstream`:
    ```bash
    git clone https://github.com/<you>/aaie-design-engineering.git
    cd aaie-design-engineering
    git remote add upstream https://github.com/InnovAIte-Deakin/aaie-design-engineering.git
    git remote -v  # sanity check
    ```



**For Each New Feature**

3. **Sync** with the latest official `development`:
    ```bash
    git fetch upstream
    ```

4. **Create a feature branch from `upstream/development`** and switch to it:
    ```bash
    git checkout -B feat/<short-description> upstream/development
    ```

5. **Do your work** and commit:
    ```bash
    # edit files
    git add .
    git commit -m "feat: <short description of change>"
    ```

6. **Push the feature branch to your fork** (and set upstream tracking):
    ```bash
    git push -u origin feat/<short-description>
    ```

7. **Open the PR** (UI path):
    - Go to your fork on GitHub → you’ll see **"Compare & pull request"**.
    - Set:
        - **base repository:** `InnovAIte-Deakin/aaie-design-engineering`
        - **base branch:** `development`
        - **head repository:** `<you>/aaie-design-engineering`
        - **compare branch:** `feat/<short-description>`
    - Fill in the PR template, add **2 peers + 1 senior**, create PR.

    **Direct compare URL format:**
    ```
    https://github.com/InnovAIte-Deakin/aaie-design-engineering/compare/development...<you>:feat/<short-description>?expand=1
    ```

**Keeping Your PR Up to Date**

8. **Rebase your feature branch on latest `upstream/development`** (recommended):
    ```bash
    git fetch upstream
    git rebase upstream/development
    git push -f origin feat/<short-description>   # force-push ok after a rebase
    ```

    > If you hit conflicts: fix files → `git add <file>` → `git rebase --continue`.

    **If merging instead of rebasing:**
    ```bash
    git fetch upstream
    git merge upstream/development
    git push origin feat/<short-description>
    ```

**Finish**

9. Once checks pass and you have **2 peers + 1 senior** approvals, **Squash & merge** the PR into **`development`**.

10. **Clean up branches** (optional):
    ```bash
    git branch -d feat/<short-description>
    git push origin --delete feat/<short-description>
    ```


## Quick Cheats

- **Verify remotes:**
    ```bash
    git remote -v
    ```

- **Reset your feature branch to latest `upstream/development`:**
    ```bash
    git fetch upstream
    git checkout feat/<short-description>
    git reset --hard upstream/development
    ```
11. **Request reviewers:** add **2 peers** + **1 senior**. (See Senior list.)
12. **Address feedback**; push updates to the same branch; re‑request review if needed.
13. **Merge** once checks pass and approvals are in. Default strategy: **squash**.

**Guardrails for this approach:**
- Keep PRs small and focused; if you need multiple concurrent PRs.
- Never push to upstream directly; `main` and `development` remain **protected**.

---

## 4) Pull Request Requirements

**Every PR must include:**
- Clear title and description (what/why), linked issue.
- Evidence Screenshots/logs if relevant.
- **Reviewers:** minimum **3 approvals** → **2 peers + 1 senior**.
- **Turnaround SLA:** reviewers should respond **within 2 calendar days (48h)** of request.

**Size & scope:**
- Keep PRs small and focused. Split large changes.

---

## 5) Responsibilities

### Author
- Drive the PR to completion: request reviews, follow up, and **merge** when ready.
- Pick **2 peers** with context and **1 senior** from your pillar (or closest).
- Be responsive: answer comments, push fixes, summarize changes after big updates.


### Reviewer (peer or senior)
- Acknowledge within 24h (even if full review comes later).
- Deliver review within **48h**. If busy, propose an ETA or suggest an alternate reviewer.
- Be specific, kind, and constructive; prefer suggestions over “drive‑by” nits.

### Mentor
- Keeps `main` in sync with `development` per release cadence.
- Unblocks overdue reviews and negotiates trade‑offs when needed.

---

## 6) What Counts as a **Good Peer Review** 

A good review increases correctness, clarity, and maintainability. Minimum bar:

- **Context & intent** — restate what the PR does and why (1–2 sentences) to show understanding.
- **Correctness** — find logical bugs, edge cases, race conditions, error handling gaps.

**Quality signal:** Avoid “LGTM” alone. Provide a brief summary and at least 2–3 concrete comments or explicit checks performed.

**When to “Request changes”:** correctness risk, missing tests, failing checks, or docs gap for user‑facing change.

**Re‑review:** significant updates after approval require a fresh approval from at least one prior approver.

---

## 7) PR Template 

```md
## Summary
- (What & why)

## Issue Reference
- 

## Type
- [ ] feat
- [ ] fix
- [ ] refactor
- [ ] docs
- [ ] test
- [ ] chore

## Changes
- Bullet the key changes

## Screenshots/Logs
- (If UI/logs are relevant)

## How to Test (If Relevant)
- Steps or commands

## Risk & Rollback (If Relevant)
- Risk level: Low/Med/High
- Rollback plan:


## Reviewers
- Peers: @<name>, @<name>
- Senior: @<name>
```




## 8) Review SLA & Escalation

- **SLA:** First substantive response within **48h** of review request.
- **Reminder cadence:**
  - T+36h: author pings reviewers on the PR.
  - T+48h: author pings pillar channel and tags a backup senior.
  - Persistent delays: escalate to the mentor.

(Optional automation examples live in `.github/workflows/` — see Appendix B.)


**Hotfixes:**
- Fix on a branch from `development`, merge to `development`, then cherry‑pick into `main` if urgent.

---

## 9) Current Trimester Contacts

**Senior Reviewers – Quick Reference**

- **Product Engineering**
  - Yugam Aggarwal
  - Negin Pakroohjahromi
- **Model Development**
  - Arnav Ahuja
  - Van Hieu Nguyen
  - Edson Rasguido
  - Khushi Choubey
- **Data Curation**
  - Aryan Arora
  - Yashica Bassi

**Mentor:** Nebula Alam

> Keep this section updated each trimester.

---

## 10) Contribution Expectations

- Contributions to AAIE **must** come in through PRs to be considered “lasting impact”.
- Everyone is expected to contribute **meaningful PRs** and complete **at least 2 thorough reviews** of others’ PRs.
- GitHub is the **source of truth** for work artifacts (not circulating documents).

---
