# Design: Ham Shack Watermark Background

**Source:** Extracted from `SC 3.ppt` (IADRC Standard Licence Preparation Course, Section 3)

## Goal

Apply the club's existing ham radio sketch watermark (from SC 3.ppt) as a very subtle slide background, giving the AI presentation visual continuity with the club's other training materials — while keeping the modern layout, dark headers, and card-based design unchanged.

## Approach

Approach A — watermark behind the whole slide canvas. The solid dark header bands naturally cover it. Only the white body area shows the watermark through a semi-transparent white layer.

## Changes

### 1. New file: `ham-shack-watermark.jpg` (369KB)
Pencil-sketch of a ham radio shack (transceiver, logbook, radio gear). Extracted from `SC 3.ppt`. Saved to repo root.

### 2. CSS in `ham-ai-presentation.html` — two rules

**`.slide`** — add background image:
```css
background-image: url('ham-shack-watermark.jpg');
background-size: cover;
background-position: center;
```

**`.sb`** — change from solid white to semi-transparent white:
```css
background: rgba(255,255,255,0.88);  /* was: #fff */
```

The 0.88 opacity (88% white) lets the very-faint sketch show through at ~8–10% — barely visible, just a texture, matching the PPT's effect.

## How it looks per slide type

| Slide type | Effect |
|---|---|
| Regular (`.hn`, `.hb`, `.hr`, `.hy`) | Watermark visible through white `.sb` body. Header band covers it. |
| Demo (`.demo-slide`) | Full dark navy — watermark completely hidden. Clean red/navy. |
| Discussion (`.disc-slide`) | Navy/blue gradient — watermark hidden. |
| Title / Thank You (`.title-slide`, `.ty-slide`) | Full-bleed navy — watermark hidden. |

## Files changed

- `ham-shack-watermark.jpg` — new
- `ham-ai-presentation.html` — 2 CSS property changes
- `ham-ai-script.html` — no changes (print format)

## Success criteria

- Watermark visible but not distracting on white body slides
- All dark/coloured slides unchanged
- Counter, notes panel, navigation all unaffected
- File still distributable (image in same directory)
