---
name: reference-design-contract
description: >-
  Turn screenshots, URLs, product notes, or reference styles into a grounded
  9-section DESIGN.md contract, decision log, and CSS token handoff before
  building or redesigning UIs.
---

# Reference Design Contract

Freeze visual direction explicitly before generating or refactoring UI code so downstream edits stay consistent without copying reference brand marks.

## Deliverables

Create up to three concise files in the target project before UI implementation:

1. `DESIGN.md` — reusable visual direction using the exact nine headings below.
2. `design-contract.md` — evidence table (`observed` / `provided` / `inferred`), `Keep / Change / Do not copy` boundary matrix, risks, and quality gate.
3. `implementation-handoff.md` — concrete file targets, token/palette/type/layout constraints, asset rules (respecting local zero-CDN constraints if applicable), and responsive acceptance checks.

## Bundled References & Light-Mode Presets

| Purpose | File | Notes |
| :--- | :--- | :--- |
| P0 validation & handoff bar | [references/checklist.md](references/checklist.md) | Must pass all P0 gates before UI build |
| Minimal clean surface system | [references/design-systems/clean/DESIGN.md](references/design-systems/clean/DESIGN.md) | White canvas + neutral spacing baseline |
| Clean CSS variable tokens | [references/design-systems/clean/tokens.css](references/design-systems/clean/tokens.css) | Drop-in `:root` CSS variables (pure CSS) |
| Cal.com monochrome SaaS system | [references/design-systems/cal/DESIGN.md](references/design-systems/cal/DESIGN.md) | High-legibility neutral dashboard/SaaS elevation |

## Workflow

1. **Lock the job:** Identify target artifact, audience, framework/constraints (e.g., SSR + pure CSS vs Tailwind), and references. Ask at most two questions only if a missing decision alters visual direction.
2. **Separate reference semantics:** Split each reference into:
   - `Keep`: density, material, typography rhythm, color temperature, elevation strategy.
   - `Change`: domain copy, branding, proprietary layout structure, framework specifics.
   - `Do not copy`: literal screenshots, logos, pricing/claims, external CDN font URLs if project bans them.
3. **Freeze one stance & write `DESIGN.md`:** Use these nine exact headings:
   `## 1. Visual Theme & Atmosphere`, `## 2. Color`, `## 3. Typography`, `## 4. Spacing & Grid`, `## 5. Layout & Composition`, `## 6. Components`, `## 7. Motion & Interaction`, `## 8. Voice & Brand`, `## 9. Anti-patterns`.
4. **Handoff & Validate:** Write `design-contract.md` and `implementation-handoff.md`, then verify every item in [references/checklist.md](references/checklist.md). Prefer numeric constraints (`1px solid #EAEAEA`, `>= 4.5:1` contrast) over adjectives like "modern" or "premium".
