# CHANGE.md

## 2026-06-14

### Homepage scaffold (tasks 1–5)

**What:** Restructured the Hugo skeleton to match the CLAUDE.md spec.

**Changes:**
- `hugo.toml` — fixed `locale` → `languageCode`, set title to `'Gloria Ma'`
- `static/css/style.css` → `static/css/main.css` (rename); updated `baseof.html` reference
- `layouts/_default/baseof.html` — stripped visible header/footer; now a minimal HTML shell
- `layouts/index.html` — rewrote with card structure: portrait slot, `{{ .Title }}`, `{{ .Description }}`, 6 nav buttons (research, garden, blog, cv, github, secret)
- `content/_index.md` — stripped placeholder body; set `title: "Gloria Ma"` and `description: "I work on machine learning, genomes, and small internet objects."`
- `CLAUDE.md` — updated `home.html` references to `index.html` throughout
