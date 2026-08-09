---
name: github-repo-beautifier
description: "Make GitHub repositories look premium: hero banner, shields, SVG assets, and landing-page rhythm. Based on hermes-optimizer format."
version: 2.0.0
author: Azamat Safarov
license: MIT
metadata:
  hermes:
    tags: [github, readme, branding, documentation, repo, presentation, premium]
    related_skills: [premium-github-readmes, public-hermes-skill-repos]
---

# GitHub Repo Beautifier

Transform any GitHub repository README into a premium product page with strong hierarchy, branded visuals, and fast scanability.

**IMPORTANT: After pushing, ALWAYS set GitHub topics via API.** They appear as blue label pills under the repo name and are critical for discoverability. Details in the "GitHub Topics" section below.

## When to use

- Creating a new public repo
- Updating an existing repo to look professional and premium
- Preparing portfolio, demo, or open-source projects
- Any repository that others will discover and evaluate

## Recommended Format: Hermes Optimizer Style

The [hermes-optimizer](https://github.com/AzamatSafarov/hermes-optimizer) repository is the reference implementation. Use this structure for maximum impact.

### 1. Centered hero block

```markdown
<div align="center">

<img src="assets/logo-mark.svg" alt="Project mark" width="92">

# ⚙️ Project Name

![Status](https://img.shields.io/badge/status-active-22c55e?style=for-the-badge)
![Type](https://img.shields.io/badge/type-Tool-2563eb?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-lightgrey?style=for-the-badge)

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)

**One-line pitch that explains value in under 15 words.**

[Quick Start](#quick-start) · [Features](#features) · [Architecture](#architecture) · [Tech Stack](#tech-stack) · [Roadmap](#roadmap)

<img src="assets/hero-banner.svg" alt="Hero banner" width="100%">

</div>
```

**Rules:**
- `for-the-badge` shields for product info (status, type, license)
- `for-the-badge` tech shields with logos (Python, TypeScript, etc.)
- Max 10 badges total
- Inline navigation anchors
- Hero banner: wide SVG/PNG, dark-mode friendly

### 2. Framing block

```markdown
> Project does **not** assume X. It inspects Y and only then recommends Z.

> [!NOTE]
> Public examples are intentionally generic.
```

### 3. Section structure (in order)

| # | Section | Emoji | Content |
|---|---------|-------|---------|
| 1 | Concept | 💡 | Why exists, what makes it different |
| 2 | Features | ✨ | Dense feature table |
| 3 | Quick Start | 🚀 | One-command install/run |
| 4 | Core Mechanism | varies | Architecture, lanes, or workflow |
| 5 | Package/Structure | varies | What files matter |
| 6 | At a Glance | 🧠 | Signal/value summary table |
| 7 | Tech Stack | 🏗️ | Layer/technology table |
| 8 | Workflow | 🧭 | ASCII flow or diagram |
| 9 | What It Improves | varies | Benefit table |
| 10 | Example Output | varies | Sample output shape |
| 11 | Quality Checks | 🛡️ | What's verified |
| 12 | Roadmap | 🗺️ | Checklist with ✅ 🟡 |
| 13 | Contributing | 🤝 | How to contribute |
| 14 | License | 📄 | License + author footer |

### Tables style
- Short dense cells
- Feature / Description pattern
- Max 2-3 columns
- No paragraph-length cells

### Code blocks
- Specify language
- Use for install, quick start, config examples

### Details blocks
- Hide secondary info: advanced install, environment notes, optional steps

### Visual assets
| Asset | Format | Size | Purpose |
|-------|--------|------|---------|
| Logo mark | SVG | 92×92 | Identity above H1 |
| Hero banner | SVG/PNG | Wide, responsive | Top visual |
| Architecture flow | SVG | Wide | System diagram |
| Social preview | PNG | 1280×640 | GitHub repo settings |

### Copy style
- Crisp, product-oriented, no corporate clichés
- Active voice: "It inspects..." not "It is designed to inspect..."
- Concrete numbers when possible

### Footer
```markdown
---

<div align="center">

**Built by [Your Name](https://github.com/YOURNAME)**

</div>
```

## Alternative: Fast ASCII Format

When full assets aren't available, use `flat-square` shields + ASCII art:
1. ASCII banner (≤3 lines)
2. `flat-square` shields row
3. Italic pitch
4. Emoji tree structure
5. Status table (✅ 🟡 ❌)
6. Author footer

See `references/complete-example.md` for this variant.

## Critical Rules

1. **Never expose private config** as defaults in public READMEs
2. **Never modify third-party originals directly** — create new repo/branch
3. **Preserve original CSS/JS** when adapting visualizations
4. **Deployed versions stay untouched** — create v2 for changes
5. **Verify `git remote -v`** before any modifications
6. **No emojis in H1/H2 headings**
7. **Dark mode friendly** colors
8. **All links must work**

## Anti-slop Rules

- Rotate opening phrases: «Готово», «Сделано», «Запушено», «В продакшене», «Финализировано»
- Avoid: «Как вы можете видеть», «Важно отметить», «Не забудьте»
- Concrete numbers: «16 файлов, 6936 строк» not «много изменений»
- Vary status emoji: ✅ 🟢 📦 🚀 🎯

## GitHub Topics (auto-generation)

After pushing the repository, generate and set topics via GitHub API:

### What topics do
- Blue label pills under repo name on GitHub → instant discoverability
- Power search filtering by topic
- Required for trending/explore visibility

### How to generate topics
Extract from: project purpose + tech stack + license + domain + audience.

**Template:**
- 1 primary tech: `python`, `typescript`, `javascript`, `go`, `rust`...
- 1 product type: `chatbot`, `dashboard`, `cli-tool`, `api`, `rag`...
- 1 audience domain: `philosophy`, `finops`, `mlops`, `devops`, `ai-agent`...
- `open-source` (always)
- Stack specifics: `fastapi`, `langchain`, `qdrant`, `nextjs`, `react`...
- Maximum 20 topics, each ≤35 chars, lowercase, hyphen

### API call (after `git push`)
```bash
export GHTOK=$(gh auth token)
curl -s -X PUT "https://api.github.com/repos/$OWNER/$REPO/topics" \
  -H "Accept: application/vnd.github.mercy-preview+json" \
  -H "Authorization: token ${GHTOK}" \
  -H "Content-Type: application/json" \
  -d '{"names":["python","chatbot","rag","azure-openai","qdrant","langchain","open-source","shchedrovitsky","philosophy","hermes-agent"]}'
```

### Verify
Go to `https://github.com/$OWNER?tab=repositories` — topics appear as blue pills under repo name.

**Rule: Never skip topics.** They are part of the premium presentation.

## References

- `references/hermes-optimizer-example.md` — reference structure
- `references/complete-example.md` — ASCII variant (creative-system)
- `references/html-footer-snippet.md` — HTML footer for visualizations

## Process

1. Read existing README
2. Determine project type and audience
3. Choose format: Full Hermes Optimizer style or Fast ASCII style
4. Create/restructure README with proper sections
5. Generate/update visual assets if needed
6. Verify GitHub rendering
7. Commit and push
