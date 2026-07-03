# PRD: Rowdy Creators Setup Guide

## Problem Statement

New Rowdy Creators club members arrive with fresh laptops and no configured development environment. They need Zed editor, Zsh shell, Oh My Zsh, and the club project cloned and open on either macOS or Windows. Without a guide, onboarding is ad-hoc and each member hits the same blockers (WSL filesystem confusion, missing CLI tools, shell misconfiguration). The club lead repeatedly explains the same concepts (version control, commits) throughout the semester.

## Solution

A single-page static website (HTML + Tailwind CDN, no build step) that walks a new member through environment setup from zero. The page has two OS-specific sections for pre-Zed steps (macOS, Windows) and a shared end-of-guide section for everything inside Zed. The guide uses annotated screenshots, collapsible "why" sections, copyable code snippets, and visual severity cues to keep the reader oriented and moving forward. A Next Steps section links to curated external resources so members can deepen their skills independently.

## User Stories

1. As a new club member on macOS, I want to install Xcode CLI tools, Homebrew, Zed, and Oh My Zsh in the right order, so that I have a working terminal and editor without guessing what to install first.
2. As a new club member on Windows, I want to check my BIOS virtualization before starting, install WSL, and configure my shell inside Ubuntu, so that I'm not blocked by hardware settings or wrong filesystem paths.
3. As a Windows user, I want clear warnings about always using WSL Remote and never working from the Windows filesystem, so that my projects don't break due to cross-filesystem issues.
4. As a Windows user whose `chsh` command fails, I want a collapsible fallback with exact Nano keystrokes and a copyable AI chat prompt, so that I can fix my shell without needing to understand terminal editors.
5. As a new club member, I want "why" explanations available when I'm curious but hidden when I just want to move fast, so that I learn at my own pace without walls of text.
6. As a new club member, I want a copy button on every terminal command, so that I can paste into my terminal without selecting text or worrying about typos.
7. As a new club member, I want to see screenshots of what success looks like (Oh My Zsh, WSL Remote picker, verification), so that I know I'm on the right track.
8. As a club lead, I want a section that explains version control and commits at a high level, so that I don't have to explain these concepts five times a semester.
9. As a new club member, I want curated links to git basics, terminal usage, and branching strategy resources, so that I can continue learning after setup.
10. As a new club member, I want to clone an example project and tour Zed's file picker, git graph, terminal, and Agent Panel, so that I'm comfortable in the editor before working on the real club project.
11. As a new member who doesn't know what a terminal is, I want the command palette route for cloning (not the terminal), so that I'm not intimidated by a black window with a blinking cursor.
12. As a Windows user, I want a note explaining that I must type `wsl` every time I open Windows Terminal — otherwise I'm in PowerShell and commands from the guide won't work.
13. As a club member on either OS, I want to verify `echo $SHELL` and `git status` at the end, so that I'm confident my environment is ready.

## Content Outlines

### macOS Path (8 steps)

1. **Install Xcode CLI tools** — `xcode-select --install`. Why collapsible (blue).
2. *(Homebrew moved into Step 3's Recommended Path)*
3. **Install Zed** — Recommended Path (collapsible, starts open): `brew install --cask zed` plus Homebrew install command and brew.sh link. Quick Path (collapsible, starts closed): zed.dev download. Zed installation docs link called out at top.
4. **Verify zsh** — `echo $SHELL` inline. Collapsible fallback if missing.
5. **Install Oh My Zsh** — `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`. Screenshot: success screen.
6. **Clone Example Project** — Zed command palette (Recommended Path). Terminal mentioned in passing. Screenshot: file tree of cloned project.
7. **Verify** — `echo $SHELL`, `git status` inline.
8. **→ Zed UI Tour** (shared section)

### Windows Path (12 steps + step 0)

0. **Before You Start** — BIOS virtualization check (Task Manager), Windows update, brand-specific BIOS keys. Calming language about virtualization.
1. **Install WSL** — `wsl --install` (PowerShell as Admin), reboot.
2. **Ubuntu first launch** — Create username/password. Screenshot: console window.
3. **Update Ubuntu** — `sudo apt update && sudo apt upgrade -y`.
4. **Install git + zsh** — `sudo apt install git zsh -y`.
5. **Change shell to zsh** — `chsh -s $(which zsh)`. Collapsible fallback (red, starts open): Nano `/etc/passwd` edit + AI chat fallback with copyable prompt.
6. **Install Oh My Zsh** — Same curl command. Brief explanation: clearer prompt, directory display. Screenshot: success screen.
7. **Install Zed on Windows** — zed.dev download. Explicit: this is for Windows, not inside WSL.
8. **Connect via WSL Remote** — Always visible critical warning (not collapsible). Screenshot: WSL Remote picker. Fresh WSL lands in `/mnt/c/Users/...` (Windows home); `cd` to Linux home (`~`).
9. **Terminal note** — Type `wsl` every time you open Windows Terminal. PowerShell is a different language.
10. **Clone Example Project** — `mkdir -p ~/projects` first, then Zed command palette.
11. **Verify** — `echo $SHELL`, `git status` inline.
12. **→ Zed UI Tour** (shared section)

### Zed UI Tour (shared, end-of-guide)

- Clone Example Project (`thurwitz/example-branches`) into `~/projects/`.
- Walkthrough: file picker, git graph + branches, terminal, Agent Panel (awareness only, no AI setup).
- For Windows: establishes where projects live on disk.

### Next Steps (end-of-guide)

1. Inline write-up: what version control is, what a commit is, why it matters (light, few paragraphs).
2. GitHub Hello World — `https://docs.github.com/en/get-started/start-your-journey/hello-world`
3. Learn Git Branching — `https://learngitbranching.js.org`
4. Ubuntu command line for beginners — `https://ubuntu.com/desktop/docs/en/latest/tutorial/the-linux-command-line-for-beginners/` (noted as lengthy)
5. Zed getting started docs — `https://zed.dev/docs/getting-started`

## Implementation Decisions

### Architecture
- Single-page HTML + Tailwind v3 via Play CDN (`3.4.17`).
- No build step. No framework. Deploy as static HTML.
- Linux is out of scope. macOS and Windows only.

### UI Patterns
- **Collapsible sections**: Minimal JS with subtle height animation. Independent toggles. Critical sections start **open** on load. Three visual severities: red (critical/blocking), orange (caution/decisions), blue (informational).
- **Code Snippets**: Copy button always visible on every block. `navigator.clipboard.writeText()`. ✓ checkmark feedback for 2 seconds. No `execCommand` fallback.
- **"Why" Content**: Always collapsible, never inline. Uses the same collapsible pattern.
- **Tip Banner**: Non-intrusive callout for optional-but-recommended steps (Homebrew).
- **Annotated Screenshots**: WebP format. Color-coded annotations matching severity colors. Stored in `assets/` or `images/`. Count not capped — user captures during fresh setup on both OSes.
- **Screenshot sizing**: Deferred to implementation — user decides while adding screenshots.
- **Responsive**: Functional on mobile, optimized for desktop.
- **Favicon**: Generic dev icon (terminal prompt) as inline SVG.

### macOS-specific
- Xcode CLI tools installed first via `xcode-select --install`.
- Homebrew: Tip Banner. Recommended but not required. Install command and brew.sh link live inside the Zed Recommended Path collapsible.
- Zed: `brew install --cask zed` (Recommended Path) or zed.dev download (Quick Path).
- zsh check: `echo $SHELL` inline. Collapsible section if missing.

### Windows-specific
- **BIOS Before You Start** section atop the Windows path. BIOS keys per brand:

| Brand | BIOS Setup Key | Boot Menu Key |
|-------|---------------|---------------|
| Dell | F2 | F12 |
| HP | Esc → F10 | Esc → F9 |
| Lenovo | F1 or F2 | F12 |
| ASUS | F2 (laptop) / Del (desktop) | Esc (laptop) / F8 (desktop) |
| Acer | F2 | F12 |
| Other | Del or F2 | F8, F11, or F12 |

- WSL: `wsl --install` (PowerShell as Admin). Windows 10 v2004+ or 11.
- WSL Remote: Always visible critical warning — never collapsible. Always open projects via WSL Remote, never from Windows filesystem.
- Shell Change Fallback: Nano `/etc/passwd` edit with exact keystrokes. AI chat fallback with copyable example prompt.
- Terminal note: type `wsl` to enter Linux; fresh WSL lands in `/mnt/c/` (Windows home).
- Oh My Zsh prerequisites: `sudo apt install git zsh -y` before running the installer.

### Zed Details
- Zed installation docs linked at the top of each OS path.
- Agent Panel: awareness only — no AI setup or configuration.
- Example Project: `thurwitz/example-branches` — public, 8 branches, 3 files, simple structure.

### Next Steps
- Inline version-control explanation: light, few paragraphs.
- Five curated external links (see Content section above).

## Testing Decisions

- Manual QA on both OSes. User will follow the guide on a fresh machine (likely a sibling's computer) to verify all commands work and no gaps exist.
- Screenshots captured during that fresh-setup session.
- What makes a good test: a new member with zero dev tools can follow the guide end to end without external help and arrive at a working Zed + zsh + cloned project.

## Out of Scope

- Linux setup path
- AI/agent configuration or setup
- Any build step (bundler, minifier, framework)
- Walkthroughs beyond the Zed UI Tour (no git tutorial, no terminal tutorial — those are external links)
- Any backend, database, or dynamic content

## Further Notes

- The user will capture screenshots during fresh setup on both macOS and Windows. Four screenshots are non-negotiable: WSL Remote picker, Zed annotated UI tour, Oh My Zsh success screen, terminal verification.
- Screenshot count is not capped. Mostly small, cropped shots of specific UI elements — not full-screen.
- The Example Project (`thurwitz/example-branches`) is distinct from the real club project. The club project is selected later.
- The guide content will be written by the agent; the user will then follow it step-by-step on a fresh machine and provide feedback.
- `CONTEXT.md` holds the domain glossary (23 terms). `docs/adr/0001-single-page-with-os-sections.md` holds the information architecture decision.
