# Script Polish Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Apply six categories of reviewer feedback to `ham-ai-script.html` using surgical edits only.

**Architecture:** Each task targets one feedback category. Tasks are independent and can be executed sequentially. No structural changes — existing HTML/CSS/JS is untouched. After all edits, validate the file opens correctly in a browser.

**Tech Stack:** Plain HTML. No build step. Edit with `edit` tool, validate with `grep` and browser open.

---

### Task 1: Accuracy softening — 3 phrases

**Files:**
- Modify: `ham-ai-script.html` (lines 419, 422, 425)

**Step 1: Edit "understood millions" phrase (line 419)**

Old:
```
It has read — and I mean actually processed and understood — millions of books, technical manuals, forum posts, and articles.
```
New:
```
It has been trained on a huge amount of written material — technical manuals, forum posts, books, and articles — and generates answers from patterns in that material.
```

**Step 2: Edit "three seconds" phrase (line 422)**

Old:
```
you type your question, and within about three seconds you get a detailed answer.
```
New:
```
you type your question, and usually within a few seconds you get a detailed answer.
```

**Step 3: Edit "completely free" phrase (line 425)**

Old:
```
the best version — good enough for everything we're going to talk about tonight — is completely free.
```
New:
```
the free versions are more than good enough for everything we're going to talk about tonight.
```

**Step 4: Verify edits**

```bash
grep -n "actually processed\|within about three\|completely free" ham-ai-script.html
```
Expected: no matches for any of the three old phrases.

**Step 5: Commit**

```bash
git add ham-ai-script.html
git commit -m "script: soften accuracy claims per reviewer feedback

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>"
```

---

### Task 2: Switch to presenter-led demo — Slides 14, 16, 20, 22

**Approach change:** Remove all live account-creation steps. The presenter uses pre-signed-in accounts
on the projector. Audience watches and nominates questions. QR codes stay on screen but are reframed
as "try this at home" rather than "do this now."

**Practical setup note to add to Slide 14 talking points:**
- Bring laptop pre-signed into ChatGPT (primary) and Claude (backup tab)
- Prepare screenshots of expected answers in case internet fails
- QR codes = take-home reference, not live activity

**Files:**
- Modify: `ham-ai-script.html` (Slides 14, 16, 20, 22)

---

**Step 1: Rewrite Slide 14 talking points**

Old:
```html
        <li>Ask everyone to get out their phone or tablet</li>
        <li>QR codes on screen — scan to open ChatGPT or Claude</li>
        <li>Walk around the room and help anyone who needs it</li>
        <li>Have a backup device (club tablet/laptop) ready for anyone who can't access it</li>
        <li>The suggested question on screen gives a great result every time</li>
        <li>Allow time for people to see results and react</li>
```
New:
```html
        <li>Presenter-led demo — drive from your own pre-signed-in laptop on the projector</li>
        <li>QR codes on screen = "take home and try later" not "do this now"</li>
        <li>Ask the room to nominate a ham radio question — makes it interactive without phones</li>
        <li>Narrate as you type: plain English, no special syntax needed</li>
        <li>Point out what AI does well AND where you'd verify the answer</li>
        <li>Have a backup tab open in Claude in case ChatGPT is slow</li>
```

**Step 2: Rewrite Slide 14 script body**

Replace the entire script section (from `<h3>Script</h3>` to `<div class="transition">`) with:

```html
    <div class="script">
      <h3>Script</h3>
      <p>
        <span class="cue red">DEMO — Drive from your own laptop. Project the screen. Do not ask attendees to sign up.</span>
      </p>
      <p>
        Alright — this is where I'll show you exactly how it works, without us spending ten minutes creating accounts.
        I've already got ChatGPT open on this screen. All I'm going to do is type a question — in plain English — and you watch what comes back.
      </p>
      <p>
        Before I type mine, let me ask you: is there a ham radio question someone would like me to try?
        <span class="cue green">Wait for suggestions. If none: "Right, I'll use the one on the screen."</span>
      </p>
      <p>
        <span class="cue">Type the chosen question slowly enough that the room can read it on the projector.</span>
        Notice a few things. I'm asking in completely plain English — no codes, no commands, no special format.
        Just a question, exactly the way I'd ask a knowledgeable friend.
      </p>
      <p>
        <span class="cue">Wait for the answer to appear.</span>
        Now look at that answer. Useful — but not perfect. I'd still verify anything important before acting on it.
        That's the habit to build: ask AI first, then check the critical details against a reliable source.
      </p>
      <p>
        The QR codes on screen are there for you to take a photo of tonight and try at home at your own pace.
        No sign-up pressure — just try it when you're ready.
      </p>
      <div class="transition">➜ Next slide — WSPR background, then second demo</div>
    </div>
```

**Step 3: Update Slide 16 talking points and script opening**

Slide 16 (propagation maps) currently says "Keep phones out from the previous demo" — remove that since there is no phone demo.

Old talking point:
```html
        <li>Both tools require no account — just scan and view</li>
```
New:
```html
        <li>No account needed — project WSPR.rocks on screen, audience watches</li>
```

Old script opening:
```html
      <p>
        <span class="cue red">DEMO — Keep phones out from the previous demo.</span>
      </p>
      <p>
        We've still got our phones out — let's look at these two tools. Scan the left QR code for WSPR.rocks.
        <span class="cue">Give people a moment.</span>
        This one you don't even need an account for. It just opens and shows you a live map.
      </p>
```
New:
```html
      <p>
        <span class="cue red">DEMO — Open WSPR.rocks on your laptop and project it. No accounts or phones needed.</span>
      </p>
      <p>
        Now for a second demo — and this one is even easier, because there's no account at all.
        I'm going to open WSPR.rocks on the screen. It just loads straight to a live map.
      </p>
```

**Step 4: Update Slide 20 — reframe Step 1 from "sign up now" to "try at home"**

Old Step 1 paragraph:
```html
      <p>
        <strong>Step one:</strong> Go to chat.openai.com, click Sign Up, enter your email, choose a password. Done. That's the account sorted. It takes about two minutes, and as I said — no payment card, no subscription required.
      </p>
```
New:
```html
      <p>
        <strong>Step one:</strong> Go to chat.openai.com or claude.ai — the URLs are on the QR slide you saw earlier.
        When you're ready, signing up takes about two minutes: an email address and a password, no payment card required.
        If you want a hand with that, any club member is happy to sit with you and do it together.
      </p>
```

**Step 5: Update Slide 22 — remove "get accounts set up" from workshop description**

Old:
```html
        If there's enough interest, I'm also open to running a more hands-on workshop at a future meeting — where we sit down, get accounts set up, and work through some real ham radio questions together.
```
New:
```html
        If there's enough interest, I'm also open to running a more hands-on workshop at a future meeting — where we work through real ham radio questions together and anyone who wants to get set up can do so with a club member alongside them.
```

**Step 6: Verify**

```bash
grep -n "Keep phones out\|We've still got our phones\|click Sign Up\|get accounts set up" ham-ai-script.html
```
Expected: zero matches (all old phrases removed).

```bash
grep -n "Drive from your own laptop\|try at home at your own pace\|sit with you and do it together" ham-ai-script.html
```
Expected: all three new phrases present.

**Step 7: Commit**

```bash
git add ham-ai-script.html
git commit -m "script: switch to presenter-led demo, remove live account creation

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>"
```

---

### Task 3: Safety section addition

**Files:**
- Modify: `ham-ai-script.html` (Slide 17, after "Fourth: use a separate email" paragraph, before `<div class="transition">`)

**Step 1: Append "stop and ask" line to safety script**

Old:
```html
      <p>
        <strong>Fourth: use a separate email if you can.</strong>
        It takes five minutes to create a free Gmail account specifically for AI tools.
        That way, if anything goes wrong, your main email — the one you use for banking and personal communication — is untouched.
      </p>
      <div class="transition">➜ Next slide — Limitations</div>
```
New:
```html
      <p>
        <strong>Fourth: use a separate email if you can.</strong>
        It takes five minutes to create a free Gmail account specifically for AI tools.
        That way, if anything goes wrong, your main email — the one you use for banking and personal communication — is untouched.
      </p>
      <p>
        And finally — the most important rule of all: <strong>if in doubt, stop and ask someone before entering any details.</strong>
        Any club member will be happy to help you check whether a site is legitimate.
      </p>
      <div class="transition">➜ Next slide — Limitations</div>
```

**Step 2: Also add the talking point to the bullet list for Slide 17**

Old (in Slide 17 talking points):
```html
        <li>Suggest a separate email address as a practical tip</li>
```
New:
```html
        <li>Suggest a separate email address as a practical tip</li>
        <li>Final rule: if in doubt, stop and ask someone before entering details</li>
```

**Step 3: Verify**

```bash
grep -n "stop and ask someone" ham-ai-script.html
```
Expected: 2 matches (talking point + script paragraph).

**Step 4: Commit**

```bash
git add ham-ai-script.html
git commit -m "script: add 'stop and ask' safety rule per reviewer feedback

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>"
```

---

### Task 4: Small wording polish — 3 edits

**Files:**
- Modify: `ham-ai-script.html` (Slides 1, 8, 10)

**Step 1: Move "beginner-friendly" reassurance earlier in Slide 1 script**

Old (line ~299):
```html
        Now before anyone tunes out — <span class="cue">pause for a laugh</span> — I promise this is not going to be a technology lecture.
        There are no complicated diagrams, no computer science theory, and nobody is going to ask you to write any code.
```
New:
```html
        Now before anyone tunes out — <span class="cue">pause for a laugh</span> — I promise this is completely beginner-friendly.
        There are no complicated diagrams, no computer science theory, and nobody is going to ask you to write any code.
```

**Step 2: Soften handwriting claim in Slide 8 script (line ~586)**

Old:
```
        AI can read the handwriting well enough to give you a useful analysis.
```
New:
```
        Sometimes AI can read handwriting well enough to give you a useful analysis — it's worth trying.
```

**Step 3: Add pause cue and "verify before you act" to Slide 10 troubleshooting**

Old (in Slide 10 script, the safety warning paragraph):
```html
      <p>
        One important note: <span class="cue red">Emphasis here.</span>
        Before you touch anything inside a mains-connected piece of equipment, please have it verified by someone with the right qualifications.
        AI can suggest where to look — it cannot replace a trained technician when mains voltages are involved.
      </p>
```
New:
```html
      <p>
        One important note: <span class="cue red">Pause here. Make eye contact. Emphasis here.</span>
        Before you touch anything inside a mains-connected piece of equipment, please have it verified by someone with the right qualifications.
        AI can suggest where to look — it cannot replace a trained technician when mains voltages are involved.
        <strong>Verify before you act.</strong>
      </p>
```

**Step 4: Verify**

```bash
grep -n "completely beginner-friendly\|Sometimes AI can read\|Verify before you act" ham-ai-script.html
```
Expected: all three phrases present.

**Step 5: Commit**

```bash
git add ham-ai-script.html
git commit -m "script: small wording polish — beginner-friendly, handwriting, verify cue

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>"
```

---

### Task 5: Runtime trim — Slides 7, 9, 11

**Files:**
- Modify: `ham-ai-script.html` (three slide script sections)

**Step 1: Trim Slide 7 (dipole diagram) — remove middle paragraph**

The second paragraph (coax/insulator/rope detail) is the most cuttable — it describes physical construction that the diagram already shows.

Old (Slide 7 script, second paragraph):
```html
      <p>
        The centre feed point is where your coax connects. You'd run the coax down to the rig — and AI will tell you what length and what connector you need for your specific radio.
        At each end there's a small insulator, and then a rope or cord going up to whatever supports you're using — trees, poles, whatever you have available.
      </p>
```
New: Remove this paragraph entirely (leave first and third paragraphs).

**Step 2: Trim Slide 9 (email/QSL) — remove third paragraph**

The WICEN newsletter paragraph is the most standalone and cuttable. The QSL letter example already lands the point.

Old (Slide 9 script, third paragraph):
```html
      <p>
        The same approach works for the club newsletter. Instead of staring at a blank page, you tell AI: "Write a 200-word article about our WICEN participation at this year's Ipswich Marathon." Give it the key details — dates, who was involved, frequencies used — and it produces a readable article that you can edit.
        What used to take an hour takes ten minutes.
      </p>
```
New: Remove this paragraph entirely. The talking point about newsletters can stay (for ad-lib reference) but remove from the script.

**Step 3: Trim Slide 11 (study buddy) — trim last paragraph to two sentences**

Old (Slide 11 script, fourth paragraph):
```html
      <p>
        Use it alongside the WIA course materials and your club Elmers — not instead of them.
        But as a study tool that's available at eleven o'clock at night when a question suddenly makes sense and you want to explore it further, it's outstanding.
      </p>
```
New (tighter — keep the key message, cut the long elaboration):
```html
      <p>
        Use it alongside the WIA course materials and your club Elmers — not instead of them. It's outstanding for those late-night moments when a concept suddenly clicks and you want to dig deeper.
      </p>
```

**Step 4: Verify paragraph counts**

```bash
grep -c "<p>" ham-ai-script.html
```
Note the count before and after — it should decrease by 3 (two removed paragraphs, one merged).

**Step 5: Commit**

```bash
git add ham-ai-script.html
git commit -m "script: trim slides 7, 9, 11 to reduce runtime by ~90s

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>"
```

---

### Task 6: Update timing markers — Slides 7, 9, 11, 19

**Files:**
- Modify: `ham-ai-script.html` (4 timing `<span>` elements)

**Step 1: Update Slide 7 timing**

Old: `<span class="timing">~2 min</span>` (in Slide 7 header)
New: `<span class="timing">~1.5 min</span>`

Be careful — multiple slides have `~2 min`. Use the Slide 7 `<div class="slide-num">7</div>` as context anchor.

**Step 2: Update Slide 9 timing**

Old: `<span class="timing">~2 min</span>` (in Slide 9 header, after `<div class="slide-num">9</div>`)
New: `<span class="timing">~1.5 min</span>`

**Step 3: Update Slide 11 timing**

Old: `<span class="timing">~2 min</span>` (in Slide 11 header, after `<div class="slide-num">11</div>`)
New: `<span class="timing">~1.5 min</span>`

**Step 4: Update Slide 19 timing**

Old: `<span class="timing">~12–15 min</span>`
New: `<span class="timing">~8–10 min</span>`

**Step 5: Update the timing summary table (top of file)**

Locate the `<table class="timing-table">` near line 257. Find rows referencing slides 7, 9, 11 (listed as "Antenna help", "QSL emails", "Study buddy") and the discussion row. Update minutes accordingly. Also update the cumulative totals.

**Step 6: Verify**

```bash
grep -n "1.5 min\|8–10 min" ham-ai-script.html
```
Expected: three `~1.5 min` entries and one `~8–10 min` entry.

**Step 7: Commit**

```bash
git add ham-ai-script.html
git commit -m "script: update timing markers for trimmed slides

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>"
```

---

### Task 7: Final validation

**Step 1: Check HTML is well-formed (no unclosed tags)**

```bash
grep -c "<div" ham-ai-script.html && grep -c "</div>" ham-ai-script.html
```
Expected: counts match.

**Step 2: Smoke-test all changes are present**

```bash
grep -n "patterns in that material\|usually within a few seconds\|free versions are more than good enough\|do not need to create an account\|just watch this part\|stop and ask someone\|completely beginner-friendly\|Sometimes AI can read\|Verify before you act\|1.5 min\|8–10 min" ham-ai-script.html
```
Expected: all 10 phrases found (≥1 match each).

**Step 3: Open in browser to confirm visual layout is intact**

```bash
open ham-ai-script.html   # macOS
# or
xdg-open ham-ai-script.html  # Linux
```
Scroll through all slides. Confirm no broken layout, no missing content.

**Step 4: Final commit if any fixups were needed**

```bash
git add ham-ai-script.html
git commit -m "script: final polish pass complete

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>"
```
