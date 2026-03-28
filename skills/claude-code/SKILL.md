---
name: factory-ops
version: 1.0.0
description: |
  Manage and operate the SMC Factory landing page from Claude Code. Deploy updates,
  run design audits, manage the GitHub Pages deployment, update the product counter,
  and sync design tokens. Use when asked to "deploy the factory page", "update shipped count",
  "audit the design", or "sync design tokens".
slash-commands:
  - factory-deploy
  - factory-audit
  - factory-counter
  - factory-design-sync
  - factory-diff
allowed-tools:
  - Bash
  - Read
  - Edit
  - Write
  - Glob
  - Grep

---

# SMC Factory Ops — Claude Code Skill

## Overview

Operational commands for managing the SMC Factory landing page from Claude Code. Handles deployment, design audits, content updates, and design system synchronization.

**Repo:** `~/projects/factory-page-redesign/`
**Live:** https://0xsmcai.github.io/factory-page-redesign/
**Deploy:** GitHub Pages (auto-deploys from `main` branch)

## Slash Commands

### `/factory-deploy`
Deploy the factory page to GitHub Pages.

**Steps:**
1. Run `/factory-audit` to catch issues before deploy
2. Stage changes: `git add index.html DESIGN.md`
3. Commit with descriptive message
4. Push to `main` — GitHub Pages auto-deploys
5. Wait 30s, then verify the live URL returns 200
6. Report deploy status

**Usage:** `/factory-deploy`

### `/factory-audit`
Full design and code audit against DESIGN.md.

**Steps:**
1. Read DESIGN.md for canonical design spec
2. Extract all CSS custom properties from index.html
3. Cross-reference design tokens — flag mismatches
4. Check font loading (Google Fonts CDN links)
5. Validate OG meta tags (og:title, og:image, twitter:card)
6. Check accessibility: aria labels, color contrast, reduced-motion support
7. Verify anti-patterns from DESIGN.md are not present (no rounded corners, no light mode, etc.)
8. Report findings with severity (critical/warning/info)

**Usage:** `/factory-audit`

### `/factory-counter`
Update the "Products shipped" counter on the page.

**Steps:**
1. Read current counter value from index.html
2. Accept new count as argument (or increment by 1 if no arg)
3. Update the counter in the HTML
4. Optionally commit and push

**Usage:** `/factory-counter [number]`
- `/factory-counter 48` — set to 48
- `/factory-counter` — increment by 1

### `/factory-design-sync`
Sync CSS custom properties with DESIGN.md after a design system update.

**Steps:**
1. Parse DESIGN.md for all design tokens (colors, spacing, typography, motion)
2. Parse index.html `:root` block for current CSS custom properties
3. Generate a diff: tokens added in DESIGN.md but missing in CSS, tokens in CSS not in DESIGN.md
4. Offer to apply changes automatically
5. Validate the result

**Usage:** `/factory-design-sync`

### `/factory-diff`
Show what changed since last deploy.

**Steps:**
1. Run `git diff HEAD~1..HEAD -- index.html DESIGN.md`
2. Summarize changes in plain English
3. Flag any changes that might affect OG image rendering or responsive layout

**Usage:** `/factory-diff`

## File Structure

```
factory-page-redesign/
├── index.html          # Single-file page (HTML + CSS + JS canvas)
├── DESIGN.md           # Design system specification
├── skills/
│   ├── openclaw/       # OpenClaw skill (slash commands for interacting)
│   │   └── SKILL.md
│   └── claude-code/    # Claude Code skill (operational commands)
│       └── SKILL.md
└── README.md           # Project overview + installation
```

## Notes

- The page is a single `index.html` file — all CSS and JS inline
- Canvas-based pixel art is programmatic (no external sprites)
- The only external dependency is Google Fonts CDN
- OG image is rendered from the canvas itself via `?export=og` URL param
- Design system is the source of truth — always reference DESIGN.md
