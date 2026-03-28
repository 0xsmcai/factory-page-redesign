# SMC Factory Page

Terminal-industrial pixel art landing page for the 0xSMC autonomous startup factory. An isometric factory visualization showing the GStack pipeline: ideas flow in, get validated, products ship out.

**Live:** https://0xsmcai.github.io/factory-page-redesign/

## What This Is

A single-page visualization built as one self-contained HTML file. Canvas-based pixel art, CRT terminal aesthetic, three factory zones (Input → Forge → Output). Designed screenshot-first for Twitter/X sharing.

- **Fonts:** Press Start 2P, VT323, JetBrains Mono (Google Fonts CDN)
- **Colors:** Terminal green → intake blue → forge amber → output gold
- **Effects:** CRT scanlines, phosphor glow, pixel grid
- **No external dependencies** beyond Google Fonts

## Installable Skills

### OpenClaw Skill

Interactive commands for previewing and validating the factory page.

**Install:** Copy `skills/openclaw/SKILL.md` to your OpenClaw skills directory.

**Commands:**
| Command | Description |
|---------|-------------|
| `/factory-preview` | Screenshot the live page for visual inspection |
| `/factory-og-check` | Validate OG and Twitter Card meta tags |
| `/factory-validate` | Cross-reference CSS tokens against DESIGN.md |
| `/factory-responsive` | Test layout at desktop, tablet, and mobile breakpoints |
| `/factory-status` | Quick health check — HTTP status, fonts, DOM |

### Claude Code Skill

Operational commands for managing and deploying the page.

**Install:** Copy `skills/claude-code/SKILL.md` to `~/.claude/skills/` or your project's `.claude/skills/` directory.

```bash
# Global install
cp -r skills/claude-code ~/.claude/skills/factory-ops

# Project install
mkdir -p .claude/skills
cp -r skills/claude-code .claude/skills/factory-ops
```

**Commands:**
| Command | Description |
|---------|-------------|
| `/factory-deploy` | Audit, commit, push, and verify deployment |
| `/factory-audit` | Full design and code audit against DESIGN.md |
| `/factory-counter [n]` | Update the "Products shipped" counter |
| `/factory-design-sync` | Sync CSS custom properties with DESIGN.md |
| `/factory-diff` | Summarize changes since last deploy |

## Project Structure

```
factory-page-redesign/
├── index.html              # Single-file page (HTML + CSS + JS canvas)
├── DESIGN.md               # Design system specification
├── README.md               # This file
└── skills/
    ├── openclaw/
    │   └── SKILL.md        # OpenClaw interactive skill
    └── claude-code/
        └── SKILL.md        # Claude Code operational skill
```

## Design System

See [DESIGN.md](DESIGN.md) for the complete design system specification including color tokens, typography scale, spacing system, motion guidelines, and anti-patterns.

## Disclaimer

For informational purposes only. Use at your own risk. Not financial advice.
