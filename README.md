# Custom AI Plugins

**[Türkçe](#türkçe-özet) | [English](#english-overview) | [Kurulum / Installation](#kurulum--installation) | [Lisanslar / Licenses](#lisanslar--licenses)**

Antigravity için hazırlanmış özel eklenti (plugin) koleksiyonudur. Çekirdek MIT yeteneklerinden (`custom-ai-skills`) ayrı olarak; uzman inceleme rolleri, doğal dil + `/denetle` tetikleyici katmanı ve farklı lisanslı 3. parti uyarlama paketlerini temiz lisans sınırlarıyla barındırır.

> Curated Antigravity plugins kept cleanly separate from MIT `custom-ai-skills` so multi-license third-party adaptations (`CC-BY-SA-4.0`, `Apache-2.0`) carry explicit attribution and untouched license terms.

---

## Türkçe Özet

| Eklenti (`dir`) | İçerik | Lisans | Kaynak / Not |
| :--- | :--- | :--- | :--- |
| [`expert-roles`](expert-roles/plugin.json) | **4 Uzman Rol:** `principal-architect`, `security-auditor`, `perf-simplifier` (salt-okunur) + `design-architect` (`DESIGN.md` & a11y/LCP)<br>**Tetik Katmanı:** `/denetle` komutu + `rules/AGENTS.md` Türkçe niyet yönlendiricisi<br>**4 Trail of Bits Skilli:** `modern-cpp`, `modern-python`, `sharp-edges`, `differential-review` | Roller ve tetikçiler özgün; paket `CC-BY-SA-4.0` uyumlu ([LICENSE.CC-BY-SA-4.0](expert-roles/LICENSE.CC-BY-SA-4.0)) | Trail of Bits (`trailofbits/skills`) Antigravity uyarlaması + özel rol tanımları |
| [`open-design-contracts`](open-design-contracts/plugin.json) | `reference-design-contract` yeteneği (`DESIGN.md` 9 bölümlü sözleşme, kontrol listesi, `cal` & `clean` token şablonları) | `Apache-2.0` ([LICENSE.Apache-2.0](open-design-contracts/LICENSE.Apache-2.0)) | `nexu-io/open-design` hafif yerel demeti |

---

## English Overview

| Plugin | Components | License | Attribution |
| :--- | :--- | :--- | :--- |
| [`expert-roles`](expert-roles/plugin.json) | **4 Subagent Roles:** `principal-architect`, `security-auditor`, `perf-simplifier`, `design-architect`<br>**Dispatch Layer:** `/denetle` skill + `rules/AGENTS.md` natural-language router<br>**4 Hardening Skills:** `modern-cpp`, `modern-python`, `sharp-edges`, `differential-review` | `CC-BY-SA-4.0` ([LICENSE.CC-BY-SA-4.0](expert-roles/LICENSE.CC-BY-SA-4.0)) | Roles authored for Antigravity; security/language skills adapted from `trailofbits/skills` |
| [`open-design-contracts`](open-design-contracts/plugin.json) | `reference-design-contract` skill (`DESIGN.md` contract workflow, `checklist.md`, `cal` / `clean` presets) | `Apache-2.0` ([LICENSE.Apache-2.0](open-design-contracts/LICENSE.Apache-2.0)) | Curated from `nexu-io/open-design` |

---

## Kurulum / Installation

1. Eklenti klasörlerini global eklenti dizininize (`~/.gemini/config/plugins/`) kopyalayın:
   ```bash
   cp -r expert-roles open-design-contracts ~/.gemini/config/plugins/
   ```
2. `expert-roles` içindeki roller (`~/.gemini/config/skills/...` altındaki) temel yeteneklere referans verir; tam verim için [`custom-ai-skills`](https://github.com/Recep-krblt/custom-ai-skills) deposunu da `~/.gemini/config/skills/` altına kurun.
3. Doğrulama için:
   ```bash
   python ~/.gemini/config/skills/skill-and-mcp-tools/scripts/validate_skills.py \
     --plugin ~/.gemini/config/plugins/expert-roles \
     --plugin ~/.gemini/config/plugins/open-design-contracts \
     --check-plugins-root ~/.gemini/config/plugins
   ```
4. Yeni bir sohbet açın veya uygulamayı yeniden başlatın; ardından **`/denetle`** komutu veya doğal Türkçe niyet ifadeleriyle (*"güvenliğe bak"*, *"mimariyi incele"*, *"sadeleştir/hızlandır"*, *"tasarımı kontrol et"*) rolleri çağırabilirsiniz.

---

## Lisanslar / Licenses

- [`expert-roles/`](expert-roles/) içindeki uyarlanmış güvenlik/dil yetenekleri Trail of Bits'ten **`CC-BY-SA-4.0`** altında uyarlanmıştır (orijinal `allowed-tools`, `issue-writer` ve `audit-context-building` çağrıları Antigravity araçlarına dönüştürülmüştür); tam lisans metni [expert-roles/LICENSE.CC-BY-SA-4.0](expert-roles/LICENSE.CC-BY-SA-4.0) dosyasındadır.
- [`open-design-contracts/`](open-design-contracts/) bileşenleri **`Apache-2.0`** lisanslıdır; tam lisans metni [open-design-contracts/LICENSE.Apache-2.0](open-design-contracts/LICENSE.Apache-2.0) dosyasındadır.
- Yerel kullanıcı adları ve makine yolları (`~/.gemini/config/` biçimine çevrilerek) tamamen temizlenmiştir.
