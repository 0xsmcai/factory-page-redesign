---
name: factory-page
version: 1.0.0
description: |
  Interact with the SMC Factory landing page — the autonomous startup factory visualization.
  Preview the page, check OG meta tags, validate design tokens, inspect animation states,
  and test responsive layouts. Use when asked to "check the factory page", "preview the site",
  "test OG image", or "validate the design system".
slash-commands:
  - factory-preview
  - factory-og-check
  - factory-validate
  - factory-responsive
  - factory-status
allowed-tools:
  - Bash
  - Read
  - Glob
  - Grep
  - WebFetch

---

# SMC Factory Page — OpenClaw Skill

## Overview

This skill provides slash commands for interacting with the SMC Factory landing page, an isometric pixel-art factory visualization showing the GStack pipeline: ideas flow in, get validated, products ship out.

**Live URL:** https://0xsmcai.github.io/factory-page-redesign/
**Repo:** https://github.com/0xsmcai/factory-page-redesign

## Slash Commands

### `/factory-preview`
Open the factory page and take a screenshot for visual inspection.

**What it does:**
1. Opens the factory page URL in a headless browser
2. Takes a full-page screenshot
3. Reports page load status, any console errors, and font loading state

**Usage:** `/factory-preview`

### `/factory-og-check`
Validate Open Graph and Twitter Card meta tags for social sharing.

**What it does:**
1. Reads index.html and extracts all `og:*` and `twitter:*` meta tags
2. Validates required tags are present: og:title, og:description, og:image, twitter:card, twitter:site
3. Checks og:image URL is accessible (1200x630 expected)
4. Reports missing or malformed tags

**Usage:** `/factory-og-check`

### `/factory-validate`
Validate design tokens and CSS custom properties against DESIGN.md.

**What it does:**
1. Reads DESIGN.md for the canonical design system
2. Extracts all CSS custom properties from index.html
3. Cross-references: reports missing tokens, mismatched values, unused tokens
4. Checks font stack (Press Start 2P, VT323, JetBrains Mono)
5. Validates color palette against the design spec

**Usage:** `/factory-validate`

### `/factory-responsive`
Test responsive layout at key breakpoints.

**What it does:**
1. Opens the page at desktop (1200px), tablet (768px), and mobile (375px) widths
2. Takes screenshots at each breakpoint
3. Checks for overflow, clipping, or layout breaks
4. Verifies terminal chrome adapts correctly

**Usage:** `/factory-responsive`

### `/factory-status`
Quick health check — is the page live and loading correctly?

**What it does:**
1. Fetches the live URL, reports HTTP status
2. Checks that Google Fonts CDN loads (the only external dependency)
3. Validates the page title and key DOM elements exist
4. Reports the shipped product count from the page

**Usage:** `/factory-status`

## Design System Reference

The factory page uses a terminal-industrial pixel art aesthetic:

- **Fonts:** Press Start 2P (titles), VT323 (terminal UI), JetBrains Mono (data)
- **Colors:** Terminal green (#4AF626), intake blue (#4A90D9), forge amber (#FFB000), output gold (#FFD700)
- **Layout:** Terminal-chrome wrapper around a full-bleed canvas viewport
- **Three zones:** Input (blue) → Forge (amber) → Output (gold)
- **Effects:** CRT scanlines, phosphor glow, pixel grid

See `DESIGN.md` in the repo for the complete design system specification.
