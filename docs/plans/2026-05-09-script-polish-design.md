# Script Polish Design — ham-ai-script.html

## Problem

The script is strong but reviewer feedback identifies six areas to improve before the VK4WIP club night:
runtime is slightly long for a 60+ audience, a few claims overstate AI capabilities, the live
account sign-up moment creates unnecessary pressure, the safety section needs one more memorable
line, and three small wording issues reduce clarity.

## Approach

Surgical edits to `ham-ai-script.html` only (Pass 1). Presentation file edits follow as Pass 2.
No sections are rewritten wholesale — only the specific lines called out in feedback are changed.

## Changes

### 1. Runtime trim — 4 slides

| Slide | Change | Timing marker |
|-------|--------|---------------|
| 7 — dipole explanation | Trim 1–2 script sentences from the dipole calculation explanation | `~2 min` → `~1.5 min` |
| 9 — email / QSL | Remove one example or condense the second paragraph | `~2 min` → `~1.5 min` |
| 11 — study buddy | Shorten one talking-point block | `~2 min` → `~1.5 min` |
| 19 — discussion | Update timing cap in marker | `~12–15 min` → `~8–10 min` |

Target total saving: ~10–12 minutes, bringing the run to roughly 63–78 minutes.

### 2. Accuracy softening — 3 phrases

- "actually processed and understood millions of books"
  → "been trained on a huge amount of written material and generates answers from patterns in that material"
- "within about three seconds"
  → "usually within a few seconds"
- "The best version… is completely free"
  → "the free versions are good enough for tonight's examples"

### 3. Account sign-up pressure — 2 edits

- **Before first demo slide** — insert: _"You do not need to create an account tonight to benefit from this talk."_
- **Sign-up cue** — replace current instruction with: _"If you already have an account, follow along now; if not, just watch and we'll help you set it up after the meeting."_

### 4. Safety section — 1 addition

Append to safety talking points:
_"If in doubt, stop and ask someone before entering details."_

### 5. Small wording polish — 3 edits

- Move "beginner-friendly" reassurance earlier, before the "no code" line.
- Soften handwriting claim: "sometimes AI can read handwriting well enough"
- Add `[pause]` stage cue and repeat "verify before you act" in the troubleshooting section.

## Out of scope (Pass 1)

- `ham-ai-presentation.html` presenter notes — covered in Pass 2.
- Any structural or layout changes.
- New slides or removed slides.

## Success criteria

- All six feedback categories addressed with minimal diff.
- No unintended content removed.
- Timing markers on slides 7, 9, 11, 19 updated to match shorter content.
- File still valid HTML, opens correctly in browser.
