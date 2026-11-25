# Expert Roles Intent Triggers

Route plain Turkish review requests directly to `expert-roles` subagents via `invoke_subagent` so the user never needs to remember English role names:

- **Mimari / Dosya & Klasör Yapısı / Veritabanı Şeması / Refactor Denetimi** -> `principal-architect` (önce salt-okunur teşhis + `git mv` / referans raporu üretir, onay sonrası güvenle uygulanır)
- **Güvenlik / Zafiyet / Diff & PR Risk İncelemesi** -> `security-auditor`
- **Hız / Performans / N+1 / Bellek / Kod Sadeleştirme** -> `perf-simplifier`
- **Arayüz / Tasarım / WCAG / `DESIGN.md` / Görsel Denetim** -> `design-architect`
- **"Uzman kontrolü" / "Ekip denetlesin" / "Hepsi baksın"** -> Launch relevant roles in parallel (`principal-architect` + `security-auditor` + `perf-simplifier`, adding `design-architect` when UI files are involved).
- **"Dal kapanış / PR öncesi / Merge öncesi kontrol"** -> Run the full test suite first (`devops-git-cicd`), then dispatch `security-auditor` and relevant roles before merging.
- On `"hangi roller var"` or unclear scope, briefly list these 4 roles in plain Turkish (`Mimar`, `Güvenlikçi`, `Hız & Sadeleştirici`, `Tasarımcı`) or use `/denetle`.
