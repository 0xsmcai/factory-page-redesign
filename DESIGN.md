# Design System — SMC Factory Page

## Product Context
- **What this is:** Landing page for the 0xSMC autonomous startup factory. Isometric pixel-art factory visualization showing the GStack pipeline: ideas flow in, get validated, products ship out.
- **Who it's for:** AI agent followers on X (@truth_terminal, @ai16z, @virtikitten crowd). People who track novel agent behaviors and share them.
- **Space/industry:** Crypto/AI agents. Competitive set: every agent project's landing page. Most use purple gradients and glossy web3 UI.
- **Project type:** Single-page visualization. Screenshot-first. One self-contained HTML file. The OG image IS the product.

## Aesthetic Direction
- **Direction:** Terminal-Industrial Pixel Art
- **Decoration level:** Intentional — CRT scanline overlay, phosphor text glow, pixel grid. Decoration serves world-building, not ornament.
- **Mood:** "You ssh'd into the agent's server and found this running." Dark, mechanical, alive. Not a game screenshot... a live monitoring feed from inside autonomous infrastructure. The factory hums. Green phosphor text flickers. Items move through the pipeline. It feels like peeking behind the curtain of an AI that builds things while you sleep.
- **Reference aesthetic:** CRT terminal monitoring system rendering a pixel-art isometric factory. Think: if SimCity ran inside a VT220 terminal. Demoscene meets ops dashboard.

## Typography
- **Display/Hero:** Press Start 2P — pixel art native, already established in the brand. Used for "SMC FACTORY" title and major headings. Loaded via Google Fonts CDN.
- **Terminal/UI:** VT323 — authentic VT220 terminal typeface. Used for status text, labels, CTA, watermark, "LIVE" indicator, product counter. The voice of the system. Loaded via Google Fonts CDN.
- **Data/Monospace:** JetBrains Mono — clean monospace for any inline data, code-style text, or tooltip content. Self-hosted or Google Fonts.
- **Loading:** Google Fonts CDN (the only external dependency). `<link>` tags with `display=swap`.
- **Scale:**
  - Title (Press Start 2P): 28-32px desktop, 18-22px mobile
  - Subtitle: 12-14px Press Start 2P
  - Terminal body (VT323): 18-24px
  - Labels on factory (VT323): 14-16px
  - Status/counter (VT323): 16-18px
  - Data (JetBrains Mono): 13-14px
  - Watermark: 11-12px VT323

## Color

### Approach: Restrained with functional color channels
Color is rare and meaningful. Each color maps to a factory state or system function. No decorative color. The palette tells the story: green (system alive) → blue (ideas entering) → amber (processing) → gold (shipped).

### Core Palette

| Token | Hex | Role |
|-------|-----|------|
| `--bg-deep` | `#0a0a0a` | True black. Page background, canvas background. |
| `--bg-surface` | `#0d1117` | Slightly lifted surface. Terminal chrome, card backgrounds. |
| `--bg-elevated` | `#161b22` | Elevated panels, hover states. |
| `--border` | `#1a2332` | Subtle borders, terminal frame edges. |
| `--border-bright` | `#2a3a4a` | Active borders, focus states. |
| `--text-muted` | `#4a5568` | Dim text, disabled states, background labels. |
| `--text-secondary` | `#7a8a9a` | Secondary information, timestamps. |
| `--text-primary` | `#c9d1d9` | Primary readable text (when not using terminal green). |

### Signal Colors (the factory story)

| Token | Hex | Role |
|-------|-----|------|
| `--terminal-green` | `#4AF626` | System alive. Phosphor green. Used for: LIVE indicator, system status text, terminal prompt, scanline tint. THE signature color. |
| `--terminal-green-dim` | `#2a8a14` | Muted green for secondary terminal text, grid lines. |
| `--terminal-green-glow` | `rgba(74, 246, 38, 0.15)` | Green glow/bloom around text and elements. CRT phosphor bleed. |
| `--intake-blue` | `#4A90D9` | Ideas entering. Cool, potential, unprocessed. NV's zone glow. Input side of the factory. |
| `--intake-blue-dim` | `#2a5a8a` | Muted blue for intake zone background, item trails. |
| `--forge-amber` | `#FFB000` | Processing, transforming. The forge at work. Center zone glow. Active machinery. |
| `--forge-amber-dim` | `#8a6000` | Muted amber for forge background, conveyor segments. |
| `--forge-amber-hot` | `#FF8C00` | Peak processing. Sparks, gear friction, active stamps. |
| `--output-gold` | `#FFD700` | Shipped. Success. Golden products emerging. Garry's zone glow. |
| `--output-gold-glow` | `rgba(255, 215, 0, 0.2)` | Gold bloom on shipped products. |
| `--reject-red` | `#FF3333` | Rejection. Item failed validation. Red stamp flash, dissolve effect. |
| `--reject-red-dim` | `#8a1a1a` | Muted red for rejection smoke tint. |

### CRT Effects
| Token | Hex/Value | Role |
|-------|-----------|------|
| `--scanline-opacity` | `0.03` | Subtle horizontal scanlines across the entire page. Barely visible, but adds texture. |
| `--scanline-color` | `rgba(74, 246, 38, 0.02)` | Green-tinted scanlines. |
| `--crt-vignette` | `radial-gradient(ellipse, transparent 60%, rgba(0,0,0,0.4))` | Subtle darkening at screen edges. CRT curvature illusion. |
| `--phosphor-blur` | `0 0 8px var(--terminal-green-glow)` | Text-shadow for terminal green text. Phosphor bloom. |

### Dark Mode
This IS dark mode. There is no light mode. Permanent dark. Terminal-native, Twitter-native.

## Spacing
- **Base unit:** 4px
- **Density:** Compact — terminal density. Information-rich, not airy.
- **Scale:**
  - `--space-2xs`: 2px — pixel-level gaps, inline elements
  - `--space-xs`: 4px — tight gaps between related items
  - `--space-sm`: 8px — standard element padding, label gaps
  - `--space-md`: 16px — section internal padding
  - `--space-lg`: 24px — between major sections
  - `--space-xl`: 32px — terminal chrome padding
  - `--space-2xl`: 48px — major vertical rhythm
  - `--space-3xl`: 64px — page-level breathing room

## Layout
- **Approach:** Terminal-chrome wrapper around a full-bleed canvas viewport.
- **Structure:** The page is a "terminal window." Top bar (status line), main viewport (canvas factory scene), bottom bar (CTA + watermark). No sidebar. No columns. One big scene.
- **Terminal chrome:** 1-2px border in `--border`, status bar at top with green text on near-black. Feels like a terminal emulator frame.
- **Canvas viewport:** The isometric factory fills 70% of vertical space. Designed as 1200x630 composition (OG image ratio). Scaled responsively.
- **Max content width:** None for the canvas. Terminal chrome caps at 1200px for text elements, centered.
- **Border radius:** 0px everywhere. Terminals don't have rounded corners. Sharp edges only. (Exception: the overall terminal window can have 2-4px radius to feel like an app window, not a browser default.)
- **Responsive:**
  - Desktop (>1024px): Full terminal chrome + factory scene, all effects
  - Tablet (768-1024px): Terminal chrome simplified, factory scene scales down
  - Mobile (<768px): Minimal chrome, factory scales aggressively. Not the screenshot target.

## Motion
- **Approach:** Intentional-functional. Nothing moves for decoration. Everything that moves is "the factory working."
- **Easing:** `ease-out` for enter, `ease-in` for exit, `linear` for conveyor (mechanical, constant)
- **Duration:**
  - `--duration-blink`: 1000ms — cursor blink, LIVE dot pulse
  - `--duration-micro`: 100ms — hover states, button feedback
  - `--duration-short`: 200ms — tooltip appear, label fade
  - `--duration-conveyor`: 12000ms — full conveyor belt cycle
  - `--duration-item-transit`: 12000ms — item moves intake to output
  - `--duration-intake-drop`: 3000-4000ms interval — new idea drops in
  - `--duration-rejection`: 500ms — red flash + dissolve
  - `--duration-sparkle`: 500ms — gold burst on product ship
  - `--duration-smoke`: 4000ms — smoke puff rise cycle (4 staggered)
- **Special animations:**
  - Scanline scroll: continuous, very slow vertical drift of scanline pattern
  - Cursor blink: `_` character blinks in terminal status bar
  - LIVE dot: green dot pulses (opacity 0.4 → 1.0, 1s cycle)
  - Text flicker: occasional subtle brightness variation on terminal green text (rare, 1-2% opacity shift, every 5-10s)
- **`prefers-reduced-motion`:** Pause all canvas animations. Show static frame. Scanlines and glow remain (CSS only, not motion).

## Factory-Specific Design Tokens

### Three Zones (per CEO Review)
The factory has three visual zones, not five. Each zone has a signature color that dominates its region:

| Zone | Position | Color Channel | Character | Label |
|------|----------|--------------|-----------|-------|
| INPUT | Left (20% width) | `--intake-blue` | NV (feeding ideas) | "IDEAS" or "> input" |
| FORGE | Center (60% width) | `--forge-amber` | Machinery, gears | "GSTACK" or "// processing" |
| OUTPUT | Right (20% width) | `--output-gold` | Garry (inspecting) | "SHIPPED" or "< output" |

### Terminal Chrome Elements
- **Top bar:** `[SMC-FACTORY] — status: LIVE — uptime: 47d 12h — cycle: 12s — ▮`
- **Bottom bar:** `@0xsmcai | Built by 0xSMC · Autonomous AI agent | Products shipped: 47`
- Top and bottom bars use VT323 in `--terminal-green` on `--bg-surface`
- Blinking cursor (`▮` or `_`) at end of top bar status line

### Label Style
Factory zone labels rendered in VT323, styled as terminal commands:
- Input zone: `> ideas --in` or `$ intake`
- Forge zone: `// gstack pipeline` or `[processing...]`
- Output zone: `> shipped ✓` or `$ output --gold`

Labels should feel like reading terminal output, not game UI.

### Item Visual Progression
Items change appearance as they move through the factory:
1. **Intake:** Small glowing blue orbs/diamonds. Raw, unformed. `--intake-blue`
2. **Forge:** Orbs gain amber edges, start pulsing. Being worked on. `--forge-amber`
3. **Output:** Items become golden rectangles with sparkle. Finished product. `--output-gold`
4. **Rejected:** Item flashes `--reject-red`, shakes, dissolves into smoke particles.

### Character Design (Programmatic Pixel Art)
- NV and Garry: 32x32 pixel sprites, code-drawn on canvas (no external PNGs)
- Color palette per character: 4-5 colors max (pixel art constraint)
- Must be recognizable at 2x zoom, read as "two workers" at thumbnail
- Idle animation: 2-frame bounce, 1s cycle
- Active animation: NV feeds items (arm movement), Garry inspects (head nod + thumbs up)

## Anti-Patterns (Do Not)
- No purple gradients. No web3 glossy cards. No "DeFi dashboard" aesthetic.
- No rounded corners (except 2px on outer terminal window frame).
- No light mode. No day/night cycle.
- No external sprite assets. All art is programmatic.
- No centered-everything layout. Terminal text is left-aligned.
- No decorative blobs, abstract shapes, or stock imagery.
- No Inter, Roboto, Poppins, or any sans-serif body font.
- No generic "Built for builders" marketing copy.
- Scanlines should be barely perceptible, not Instagram-filter obvious.
- CRT glow should be subtle phosphor bloom, not neon rave.

## OG Image
- Dimensions: 1200x630px (Twitter summary_large_image)
- The canvas factory scene IS the OG image. Built-in export via `?export=og` URL param.
- OG image must pass the thumbnail test: at 500x260px, the three zones and color gradient (blue → amber → gold) should be distinguishable.
- Meta tags: `og:title` = "SMC Factory", `og:description` = "Ideas flow in. GStack validates. Products ship out.", `twitter:card` = "summary_large_image", `twitter:site` = "@0xsmcai"

## Decisions Log
| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-03-28 | Terminal/console aesthetic over game-style pixel art | 0xSMC IS a terminal process. The factory should look like monitoring the agent from inside its own infrastructure, not like a game. More authentic, more interesting to the AI agent crowd who live in terminals. |
| 2026-03-28 | Three zones (Input/Forge/Output) not five stages | CEO review: five labeled rooms compress to illegible mush at Twitter thumbnail resolution. Three zones with distinct colors read at any size. |
| 2026-03-28 | Programmatic pixel art, no external sprites | CEO review: external spritesheets create an art production bottleneck. Code-drawn art means "every pixel placed by the AI" is literally true. Better narrative. |
| 2026-03-28 | Permanent dark mode, no day/night cycle | Dark is Twitter-native. Day/night means random screenshots might catch the "wrong" lighting. Always moody, always dramatic. |
| 2026-03-28 | Press Start 2P + VT323 + JetBrains Mono type stack | Press Start 2P for pixel art titles (established). VT323 for authentic terminal feel (it IS a VT220 font). JetBrains Mono for clean data display. Three fonts, three roles, zero overlap. |
| 2026-03-28 | Green → Amber → Gold color progression | Color tells the factory story left-to-right even at thumbnail size. Green (system/alive), blue (raw ideas), amber (processing), gold (shipped). Each color earns its place. |
| 2026-03-28 | LIVE indicator + product counter ships in V0 | CEO review expansion: "LIVE" transforms the page from art piece to operating system. Highest value-per-line-of-code addition. |
| 2026-03-28 | Zero border radius | Terminals have sharp edges. Rounded corners are for apps pretending to be friendly. This is infrastructure. |
