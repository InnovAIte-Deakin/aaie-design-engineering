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

1. **Fork** the repo to your GitHub account.
2. **Clone** your fork and add upstream:
   ```bash
   git clone https://github.com/<you>/aaie-design-engineering.git
   cd <repo>
   git remote add upstream https://github.com/InnovAIte-Deakin/aaie-design-engineering.git
   ```
3. **Create/align your local `development` branch** from upstream and set it to push to your fork:
   ```bash
   git fetch upstream origin
   git checkout -B development upstream/development
   git push -u origin development
   ```
4. **Do your work on `development` in your fork** (commit early, commit often).
5. **Keep current** by rebasing on upstream `development` regularly:
   ```bash
   git fetch upstream
   git rebase upstream/development
   ```
6. **Push** your commits to your fork:
   ```bash
   git push origin development
   ```
7. **Open a PR** from **`<you>:development` → `AAIE/<repo>:development`**.
8. **Request reviewers:** add **2 peers** + **1 senior**. (See Senior list.)
9. **Address feedback**; push updates to the same branch; re‑request review if needed.
10. **Merge** once checks pass and approvals are in. Default strategy: **squash**.

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
