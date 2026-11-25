---
name: denetle
description: Route architecture, security, performance/simplification, or UI design audits ("denetle", "uzman", "mimari", "güvenlik", "hız", "tasarım", "hepsi") to expert-roles subagents without memorizing role names.
---

# Expert Roles Dispatcher (`/denetle`)

Route the user's request to the matching `expert-roles` subagent(s) via `invoke_subagent`:

| User Intent / Keywords | Subagent (`TypeName`) | When to Run |
| :--- | :--- | :--- |
| Architecture, modules, DB schema (`mimari`, `şema`, `yapı`, `refactor`) | `principal-architect` | Multi-file design, seams, PostgreSQL, Go/Java/C++/Python structure |
| Security, auth, diff risk (`güvenlik`, `açık`, `siber`, `diff`) | `security-auditor` | Auth/IDOR, secrets, C/C++ memory safety, sharp edges, git diffs |
| Speed, N+1, cleanup, leaks (`hız`, `performans`, `sadeleştir`, `temizle`) | `perf-simplifier` | Post-working simplification, SQL indexes, blocking locks, leaks, ML leakage |
| UI/UX, `DESIGN.md`, a11y, LCP (`tasarım`, `arayüz`, `UI`, `renk`) | `design-architect` | New views, visual direction contracts, WCAG/contrast/LCP audits |
| Branch merge / PR readiness (`dal kapanış`, `PR öncesi`, `merge öncesi`) | `devops-git-cicd` gate + relevant roles | Verify full test suite passes first (`git-workflows-and-recovery.md`), then dispatch diff/security/architecture roles |

## Execution Rules
1. **Explicit scope in prompt:** Dispatch only the matching role(s) in parallel via `invoke_subagent` (give each role the target paths, diff range, or question).
2. **`/denetle` with no specific domain (or "uzman kontrolü" / "hepsi"):**
   - Inspect changed files first (`git diff --name-only` / workspace files).
   - Run `principal-architect`, `security-auditor`, and `perf-simplifier` in parallel by default; include `design-architect` whenever frontend/UI files (`.tsx`, `.jsx`, `.html`, `.css`, `.astro`, `.xaml`, `DESIGN.md`) are present or requested.
3. **Interactive menu fallback:** If no workspace change or target is clear, present numbered choices via `ask_question`: `1. Mimari & Şema`, `2. Güvenlik`, `3. Performans & Sadeleştirme`, `4. UI/UX Tasarım`, `5. Uygun olan hepsi (Paralel)`.
4. **Never leak local/internal bloat:** Aggregate findings concisely by severity (`P0`–`P3`) without editing source files unless asked.
