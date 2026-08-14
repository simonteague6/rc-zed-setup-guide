# Research Note: themissingmanual.dev — surface overview for beginner onboarding

**Date:** this session
**Purpose:** Surface-level assessment of https://themissingmanual.dev as a resource for complete beginners (zero to near-zero experience) setting up a dev environment, for the Rowdy Creators onboarding guide.

## 1. What the site is (from the homepage)

Fetched: `https://themissingmanual.dev/` (HTTP 200).

- **Title:** "The Missing Manual for Developers" / "The Missing Manual".
- **Tagline (H1):** "Understand how software works."
- **Description (meta):** "Clear, in-depth guides to how software works — from how a computer boots up to the internet, databases, and AI. Start from zero or go deep. Free, forever."
- **Purpose (from `/about`):** A free, **text-first library** that explains "the things most resources skip — from the absolute basics up to the deep details." Explicitly motivated as filling the gap between official docs (which "assume you already know") and tutorials (which "stop at hello world"). No account needed; free forever; brand-new-computer-friendly framing ("Start from zero").

**Structure:** Homepage is "Browse by topic" — the site's content is organized into **categories**, each containing **guides**. Guides are tagged by difficulty (**B = Basic, I = Intermediate, A = Advanced** — confirmed from the nav `title="Basic"/"Intermediate"/"Advanced"` attributes). Guides are split into numbered **parts** (e.g. `/guides/git-from-zero/1` … `/4`).

## 2. Root URL and main section / chapter URLs

**Root:** `https://themissingmanual.dev/`

### Top-level site pages (from homepage + about nav)
- `/paths` — Learning paths (client-rendered; content not in static HTML)
- `/train` — Brain games
- `/practice` — Practice (learn-by-doing)
- `/cheat-sheet` — Cheat sheets
- `/glossary` — Glossary
- `/about` — About
- `/changelog` — "What's new"
- `/request` — Request a guide
- `/backlog` — "What's next?"
- `/contribute` — Contribute
- `/rss.xml` — RSS feed

### Category (section) URLs — the main content structure (all fetched from homepage)
| Category URL | Guides | Category URL | Guides |
|---|---|---|---|
| `/categories/algorithms` | 10 | `/categories/apis` | 10 |
| `/categories/logic` | 10 | `/categories/architecture` | 9 |
| `/categories/mathematics` | 10 | `/categories/devops` | 9 |
| `/categories/physics` | 8 | `/categories/infrastructure` | 12 |
| `/categories/operating-systems` | 12 | `/categories/performance` | 11 |
| `/categories/hardware` | 7 | `/categories/security` | 12 |
| `/categories/networking` | 9 | `/categories/ai-ml` | 13 |
| `/categories/programming-concepts` | 13 | `/categories/working-with-ai` | 16 |
| `/categories/programming-languages` | 9 | `/categories/no-code` | 11 |
| `/categories/web-fundamentals` | 11 | `/categories/tooling` | 55 |
| `/categories/frontend` | 5 | `/categories/projects` | 16 |
| `/categories/frameworks` | 37 | `/categories/working-as-a-developer` | 5 |
| `/categories/version-control` | 5 | `/categories/data-analytics` | 13 |
| `/categories/debugging` | 8 | `/categories/databases` | 13 |
| `/categories/testing` | 9 | | |

### Beginner-relevant guide URLs within the recommended categories (fetched from category pages)
**Version Control (`/categories/version-control`):**
- `/guides/git-from-zero` — Git From Zero (Basic)
- `/guides/git-explained-like-a-human` (Basic)
- `/guides/git-with-other-people` (Intermediate)
- `/guides/git-disaster-recovery` (Advanced)
- `/guides/gitignore-lfs-submodules` (Intermediate)

**Operating Systems (`/categories/operating-systems`) — Basic level guides:**
- `/guides/what-an-operating-system-is`
- `/guides/the-filesystem-explained`
- `/guides/the-terminal-and-shell` — The Terminal & Shell, Explained (Basic)
- `/guides/linux-from-zero` (Basic)
- `/guides/editing-in-the-terminal` (Basic)
- `/guides/how-your-computer-boots` (Basic)

**Tools & Workflow (`/categories/tooling`) — the largest category (55 guides); Basic-level anchors:**
- `/guides/what-tooling-even-is` — What Tooling Even Is (Basic)
- `/guides/python-packaging-pip-poetry-uv` (Python packaging: pip, venv, Poetry, uv)
- `/guides/npm-pnpm-yarn`

**Programming Concepts (`/categories/programming-concepts`):**
- `/guides/programming-from-zero` (Basic)
- `/guides/what-happens-when-code-runs` (Basic)
- `/guides/languages-explained-like-a-human` (Basic)

## 3. Recommended TOP 3 for a complete beginner setting up a dev environment

1. **Git From Zero — Version Control for People Who've Never Used It**
   `https://themissingmanual.dev/guides/git-from-zero`
   Why: Git is unavoidable in a coding club — members must clone the shared club project, work on branches, and open pull requests. This is a true zero-knowledge, Basic-level intro, so it's the single most useful prerequisite for club onboarding.

2. **The Terminal & Shell, Explained**
   `https://themissingmanual.dev/guides/the-terminal-and-shell`
   Why: Setting up a dev environment is terminal-driven (and Rowdy Creators' own guide is built around Zsh and the shell). This Basic-level explainer gives total beginners the mental model for the shell they're about to spend all their time in.

3. **What Tooling Even Is**
   `https://themissingmanual.dev/guides/what-tooling-even-is`
   Why: It's the exact topic of an environment-setup guide — it explains what developer tooling is and why it exists. A Basic-level, framing-first piece that quietly removes the "I don't even know what these things are" anxiety for near-zero-experience members.

## 4. Length / depth of the top 3

Verified via the numbered sub-page structure embedded in each guide page:
- **Git From Zero:** sub-parts `/1` through `/4` → a long 4-page chapter.
- **The Terminal & Shell, Explained:** sub-parts `/1` through `/3` → a 3-page chapter.
- **What Tooling Even Is:** sub-parts `/1` through `/4` → a 4-page chapter.

So each is a sizeable multi-part tutorial (not a one-page quick read), but split into digestible numbered parts labeled Basic.

## Sources fetched (all HTTP 200)
- `https://themissingmanual.dev/` (homepage)
- `https://themissingmanual.dev/about`
- `https://themissingmanual.dev/paths`
- `https://themissingmanual.dev/categories/version-control`
- `https://themissingmanual.dev/categories/operating-systems`
- `https://themissingmanual.dev/categories/tooling`
- `https://themissingmanual.dev/categories/web-fundamentals`
- `https://themissingmanual.dev/categories/programming-concepts`
- `https://themissingmanual.dev/guides/git-from-zero`, `/guides/git-from-zero/1`
- `https://themissingmanual.dev/guides/the-terminal-and-shell`, `/1`
- `https://themissingmanual.dev/guides/what-tooling-even-is`, `/1`

## Caveats / limits
- Guide bodies are **client-rendered** (Svelte SPA); the static HTML includes titles, nav, difficulty tags, and part URLs but not the full article text, so content quality here is inferred from titles/level tags rather than read in full.
- `/paths` and `/train`/`/practice` load content via JS and were not enumerable at surface level.
- Difficulty tags (B/I/A) come from the site's own nav `title` attributes (Basic/Intermediate/Advanced); no separate prose legend was found.

---
## Report

**What the site is:** The Missing Manual for Developers — a free, text-first, in-depth library explaining how software works "from the absolute basics," designed for people starting from zero. Organized into ~26 topic categories, each containing multi-part guides tagged by difficulty (Basic/Intermediate/Advanced).

**Root:** `https://themissingmanual.dev/`

**Main section (category) URLs found:**
`/categories/algorithms, logic, mathematics, physics, operating-systems, hardware, networking, programming-concepts, programming-languages, web-fundamentals, frontend, frameworks, version-control, debugging, testing, databases, data-analytics, apis, architecture, devops, infrastructure, performance, security, ai-ml, working-with-ai, no-code, tooling, projects, working-as-a-developer`, plus top-level `/paths`, `/train`, `/practice`, `/cheat-sheet`, `/glossary`, `/about`, `/changelog`, `/request`, `/backlog`, `/contribute`, `/rss.xml`.

**Top 3 for complete beginners (dev-environment focus):**
1. Git From Zero — `/guides/git-from-zero` (Basic, 4 parts) — core club workflow: clone, branch, PR.
2. The Terminal & Shell, Explained — `/guides/the-terminal-and-shell` (Basic, 3 parts) — terminal/Shell is the heart of env setup.
3. What Tooling Even Is — `/guides/what-tooling-even-is` (Basic, 4 parts) — frames exactly what developer tooling is.

All three are multi-part Basic-level chapters.
