# Rowdy Creators Setup Guide

A static website that gets new Rowdy Creators team members from a fresh laptop to a working development environment — Zed editor, Zsh shell, and the club project cloned and open — on either macOS or Windows.

## Language

**Setup Guide**:
The deliverable: a single-page site that walks a new member through environment setup, organized into OS-specific pre-Zed steps and OS-agnostic in-Zed steps.
_Avoid_: Tutorial, onboarding playbook, installation guide

**OS Path**:
One of two environment-specific setup tracks — macOS or Windows. Pre-Zed steps differ per path; everything from "Zed is open" onward is shared.
_Avoid_: Platform, operating system branch

**Pre-Zed Setup**:
All steps required before opening the Zed editor — OS-level installs, shell configuration, and for Windows, WSL setup.
_Avoid_: Prerequisites, system prep

**In-Zed Setup**:
All steps performed inside Zed after it's open — cloning the club project (not the Example Project), verifying the environment works. Identical across OS paths. The Zed UI Tour is a separate end-of-guide section, not part of In-Zed Setup.
_Avoid_: Editor configuration

**Next Steps**:
A curated set of external resources (git basics, terminal usage, branching) linked at the end of the guide. Not original content; deferred to later.
_Avoid_: Further reading, additional resources

**Project**:
The Rowdy Creators club project that team members clone and work on. The guide assumes a single shared repository.

**Recommended Path**:
A setup step marked as the preferred approach (e.g. installing Zed via Homebrew on macOS). Presented alongside a Quick Path alternative; the reader chooses.
_Avoid_: Best practice, suggested approach

**Quick Path**:
The simpler but less opinionated alternative to a Recommended Path (e.g. downloading Zed directly). Skips optional tooling to get the reader to a working state faster.
_Avoid_: Fast track, alternative route

**Collapsible Section**:
A UI element that expands and collapses content. Used to keep the page scannable — details hidden behind a click without leaving the page.
_Avoid_: Accordion, dropdown, expandable panel

**Code Snippet**:
A short block of terminal commands or config text the reader copies and pastes. Rendered with a copy button.
_Avoid_: Code block, command block

**Annotated Screenshot**:
A screenshot with visual callouts (arrows, highlights, boxes) directing the reader's attention to a specific UI element.
_Avoid_: Marked-up image, labeled screenshot

**Xcode Command Line Tools**:
A lightweight macOS package providing `git`, compilers, and other developer utilities. A pre-Zed prerequisite on macOS, installed via `xcode-select --install`.
_Avoid_: Xcode, developer tools

**Static Asset**:
A pre-built file served as-is — annotated screenshots (WebP), favicons. Lives in an `assets/` or `images/` directory alongside the HTML.
_Avoid_: Media, resource, binary

**WSL Remote**:
Zed's built-in connection to a WSL distribution. Appears as an option in Zed's file picker and command palette. The guide must warn Windows users to always open their project via this remote, never from the Windows filesystem.
_Avoid_: WSL connection, remote host

**Tip Banner**:
A non-intrusive UI element (icon + short text) recommending an optional but beneficial step — e.g. installing Homebrew. Distinct from a warning or required step.
_Avoid_: Info box, callout, note

**Shell Change Fallback**:
On WSL, `chsh` often fails with "operation not permitted." The fallback is manually editing `/etc/passwd` to replace the shell path, using Nano (not Vim). Presented as a collapsible section that opens when `chsh` fails — includes exact Nano keystrokes and a verification step. If the edit also fails, the reader is directed to paste error logs into an AI chat with an example prompt.
_Avoid_: Shell workaround, chsh fix

**Oh My Zsh Prerequisites**:
Requires zsh, git, and curl or wget. On macOS these are covered by the default shell and Xcode CLI tools. On Windows/WSL Ubuntu, git must be verified or installed (`sudo apt install git`) before running the Oh My Zsh installer.

**"Why" Content**:
Collapsible explanations of why a step matters. Always presented in a collapsible section — never inline. Visual differentiation (red border/icon, bold label) makes critical warnings noticeable even when collapsed, while nice-to-know context uses a subtler treatment.
_Avoid_: Info box, callout, inline explanation

**BIOS Prerequisite**:
A dedicated "Before You Start" section atop the Windows OS Path. Covers Windows update check, BIOS virtualization enablement (VT-x/AMD-V), and brand-specific BIOS keys (5–6 common brands + generic fallback). Includes calming language (1–2 sentences) explaining what virtualization is and why it's needed — reassurance that enabling it won't void a warranty.
_Avoid_: System requirements, hardware check

**Zed UI Tour**:
An end-of-guide section (not a setup step) demonstrating Zed's capabilities. The reader clones an Example Project to a known location, then walks through the file picker, git graph/branches, terminal, and Agent Panel. For Windows/WSL users, this establishes where projects live on disk so the real club project lands in the right place later. No AI setup instructions — awareness only.
_Avoid_: Editor walkthrough, feature overview

**Example Project**:
A public GitHub repository cloned during the Zed UI Tour to demonstrate Zed's git and file-tree features. Not the Rowdy Creators club project. Chosen for visible branching and a simple structure a newcomer can visually parse.
_Avoid_: Demo repo, sample project

**Nano Editor**:
A simple terminal text editor used in the Shell Change Fallback to edit `/etc/passwd`. Chosen over Vim for its lower learning curve — the guide includes exact keystrokes for editing, saving, and exiting.
_Avoid_: Terminal editor, text editor

**Agent Panel**:
Zed's built-in sidebar showing agent conversation threads, each tied to a project directory. Mentioned in the Zed UI Tour for awareness — the reader sees it exists, understands threads map to projects, but receives no agent setup or configuration instructions.
_Avoid_: AI panel, assistant sidebar
