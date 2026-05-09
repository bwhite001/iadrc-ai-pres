# Copilot Instructions — IADRC AI Presentation

## What this repo is

Two self-contained, dependency-free HTML files for a VK4WIP (Ipswich & District Amateur Radio Club) club-night presentation on AI tools for amateur radio operators. No build step, no package manager, no framework. Open either file directly in a browser.

| File | Purpose |
|---|---|
| `ham-ai-presentation.html` | 22-slide browser-based slideshow (projected on screen) |
| `ham-ai-script.html` | Full speaker script with talking points and stage cues (printed by presenter) |

## Architecture

Both files are **single-file, fully self-contained HTML**. All CSS, JS, SVG diagrams, and content live inline. There are no external dependencies except:
- `quickchart.io/qr?text=<url>` — QR code images loaded at runtime (require internet at venue)
- No CDNs, no npm, no frameworks

### Presentation file structure (`ham-ai-presentation.html`)

```
<style>          CSS custom properties + all component styles
  :root          Brand tokens: --navy, --blue, --gold, --red, --green, --light, --white
  .slide         Base slide (position:absolute, opacity:0)
  .slide.active  Visible slide
  .sh / .sb      Slide header / slide body
  .hn .sh        Header colour variants: hn=navy, hb=blue, hg=green, hr=red, hy=gold
  special slides title-slide, demo-slide, disc-slide, ty-slide

<div#ss>         Slide container (1200×675px, scaled via JS)
  .slide[data-notes="..."]   Each slide — presenter notes stored in data attribute

<script>         Navigation (go/show), notes panel toggle, fullscreen, responsive scale()
```

Slide types by class:
- `.hn` / `.hb` / `.hr` / `.hy` — coloured header variants (navy/blue/red/gold)
- `.demo-slide` — red live-demo slides with animated LIVE dot
- `.disc-slide` — navy/blue gradient discussion slides
- `.title-slide` / `.ty-slide` — full-bleed centred slides

### Script file structure (`ham-ai-script.html`)

Each slide is a `.slide-block` containing:
- `.slide-header` — slide number, title, timing
- `.points` — bullet talking points
- `.script` — verbatim script paragraphs
- `.cue` spans — stage directions (yellow=action, `.red`=demo, `.green`=discussion)

## Key conventions

### Adding a new slide (presentation)
1. Add a `<div class="slide [type]" data-notes="presenter note text">` block inside `#ss`
2. Update the `total` variable — it is auto-derived from `querySelectorAll('.slide')`, so no manual count needed
3. Use `.sh` + `.sb` structure; pick a header colour class (`.hn`, `.hb`, etc.)
4. Match the existing layout helpers: `.two` (50/50 grid), `.t65` (65/35 grid), `.center`
5. Content components available: `.card`, `.prompt`, `.hl`, `.hl.gold`, `.qrc`, `.qgrid`, `.step`, `.warn`, `.disc`, `.agenda-item`

### Adding a new slide (script)
Mirror the presentation slide order exactly. Each `.slide-block` must have a matching `.slide-num` and the same title as the presentation slide header.

### QR codes
Generated via `quickchart.io/qr?text=<url>&size=170&margin=1`. Always include `onerror="this.style.display='none'"` on the `<img>` tag so offline use degrades gracefully.

### SVG diagrams
Inline SVG only — no external image files. Use the VK4WIP brand colours (`#0B2D53` navy, `#F4C542` gold, `#1E5CB3` blue). Keep `viewBox` fixed and let CSS control display size.

### Brand tokens (CSS custom properties)
```css
--navy:  #0B2D53
--blue:  #1E5CB3
--gold:  #F4C542
--red:   #E53935
--green: #2E7D32
--light: #f0f6ff
```
Always use these tokens — never hard-code hex values for brand colours.

### Accessibility / audience considerations
- Minimum body font size: `26px` for slide content, `20px` for supplementary text
- All lists use `font-size: 26px` minimum
- High contrast: light text on dark headers, dark text on white/light bodies
- No animations except the `.dot` pulse on LIVE demo slides and the slide `opacity` transition

## Deployment

No build step. Share by:
- Emailing the `.html` files directly
- USB stick
- Hosting as static files (any web server or GitHub Pages)

The presentation works fully offline except for QR code images.
