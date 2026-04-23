---
name: Career-Ops Setup Plan
description: career-ops is cloned and ready but intentionally deferred to Session 61+ when active job hunting begins
type: project
---

Career-ops (cloned at `career/career-ops/`) is NOT to be set up or used until Session 61+.

**Why:** User is in learning phase (Sessions 1–60). Career-ops is for active job hunting — scanning portals, evaluating offers, generating tailored CVs. Setting it up now adds zero value and maintenance overhead.

Gap tracking also starts at Session 61 — not before. Before that, Flutter track already covers what jobs need; gap analysis just creates noise without real interview experience to calibrate against.

**How to apply:** At Session 61, FIRST run `git submodule update --remote career/career-ops` to pull latest career-ops changes before onboarding. Then set up `cv.md`, `config/profile.yml`, `portals.yml`, `modes/_profile.md`. Also create `career/gaps.md` at that point to feed real gaps from job posts into learning.

career-ops is tracked as a **git submodule** (not plain files) so upstream updates can be pulled cleanly at Session 61.

Do not suggest career-ops setup, gap tracking, or job scanning before Session 61.
