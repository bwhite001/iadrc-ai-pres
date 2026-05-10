# Design: Demo Slide Improvements

## Problem

Slide 14's suggested AI prompt ("Explain WSPR to me…") is a generic chatbot question. It doesn't connect to real ham habits that every operator has — reading manuals or studying for licences. Two stronger demo ideas were identified through brainstorming.

## Approach

Update Slide 14 and add one new demo slide, keeping all other slides unchanged.

---

## Changes

### Slide 14 — Updated: "Read a Radio Manual with AI 📄"

**Format:** Same `demo-slide` red layout. QR codes for ChatGPT and Claude remain.

**New suggested prompt (shown on screen):**
> "Here is a page from a radio manual. Summarise the key points in plain English as a short dot-point checklist for someone returning to HF after 20 years."

**Presenter intro line:**
> "Most of us have opened a radio manual, found the answer somewhere on page 83, and still not felt much wiser. Let's see what AI does with the same page."

**Presenter notes:** Before/after framing; demonstrate summarise → checklist → plain-English rewrite as three follow-up prompts showing progressive capability.

---

### New Slide — "AI as Your Exam Tutor 🎓" (inserted after Slide 14, before Slide 15)

**Format:** `demo-slide` red layout. No QR codes (phones already out). Three step cards showing the demo sequence.

**Sample theory question shown:**
> "Q: What does an SWR of 3:1 indicate, and what is the likely effect on your transmitter?"

**Three demo steps:**
1. "Explain why the correct answer is right, in plain English."
2. "Explain it at three levels: beginner, Standard licence, and Advanced licence."
3. "Give me two more practice questions on the same topic."

**Ethical framing note (shown on slide):**
> "Not to cheat — to understand *why* the answer is right."

**Presenter notes:** Frame as useful for anyone upgrading, mentoring a new member, or brushing up on theory. Ethical/educational tone is important.

---

### Slides 15 + 16 — Unchanged

WSPR intro and propagation demo slides remain as-is.

---

### Script file

Mirror the above in `ham-ai-script.html`:
- Update the Slide 14 `.slide-block` with new title, talking points, verbatim script, and cues
- Insert a new `.slide-block` for the exam-tutor slide with matching content
- Renumber subsequent slide blocks if needed

---

## Success criteria

- Both demo slides feel like natural demonstrations a presenter can run without prep
- Manual demo has a clear "before AI / after AI" moment
- Exam demo has the ethical framing visible on screen (not just in notes)
- Script file matches presentation slide order exactly
