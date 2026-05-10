# Demo Slide Improvements Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Replace Slide 14's generic WSPR prompt with a radio-manual demo, insert a new WIA exam-tutor demo slide after it, and keep all other slides unchanged.

**Architecture:** Two self-contained HTML files (`ham-ai-presentation.html` and `ham-ai-script.html`). Changes are in-place HTML edits. A new slide is inserted after Slide 14 in the presentation; all slides from old Slide 15 onwards shift up by one number in the script. JS auto-counts `.slide` elements so no `total` variable needs updating.

**Tech Stack:** Vanilla HTML/CSS/JS, no build step. Open in browser to verify visually.

---

## Task 1: Update Slide 14 in the presentation file

**Files:**
- Modify: `ham-ai-presentation.html` lines ~710–745

**Step 1: Replace the Slide 14 comment header**

Find:
```html
<!-- ══════════════════════════════════════════════════════
     SLIDE 14 — DEMO: TRY AI NOW
══════════════════════════════════════════════════════ -->
```
Replace with:
```html
<!-- ══════════════════════════════════════════════════════
     SLIDE 14 — DEMO: READ A RADIO MANUAL WITH AI
══════════════════════════════════════════════════════ -->
```

**Step 2: Replace the presenter notes (`data-notes`) on the Slide 14 `<div>`**

Find (the full `data-notes` attribute):
```
data-notes="• DEMO — pause slides, get everyone hands-on (8–10 minutes).
• Ask everyone to get out their phone or tablet.
• Walk room and help with QR scanning and sign-up — have a backup device ready.
• Suggested question on screen gives a reliable, interesting result every time.
• After 30–60 seconds: ask 2–3 people to share what their screen said — react naturally."
```
Replace with:
```
data-notes="• DEMO — pause slides, get everyone hands-on (8–10 minutes).
• Ask everyone to get out their phone or tablet.
• Walk room and help with QR scanning and sign-up — have a backup device ready.
• Intro line: 'Most of us have opened a radio manual, found the answer on page 83, and still not felt much wiser. Let's see what AI does with the same page.'
• Show the prompt on screen; invite them to paste in any manual page they have handy, or use the example prompt as-is.
• After 30–60 seconds: ask 2–3 people to share — what did it summarise? How did it rewrite it?
• Follow-up prompts to suggest: 'Turn this into a 5-step checklist' / 'Explain this for someone returning to HF after 20 years.'"
```

**Step 3: Replace the slide heading**

Find:
```html
    <h2 style="margin-left:18px;margin-bottom:0;">Try ChatGPT Right Now! 📱</h2>
```
Replace with:
```html
    <h2 style="margin-left:18px;margin-bottom:0;">Read a Radio Manual with AI 📄</h2>
```

**Step 4: Replace the gold highlight line**

Find:
```html
      📱 Get out your phone — let's try it together!
```
Replace with:
```html
      📱 Get out your phone — we're going to summarise a manual page together!
```

**Step 5: Replace the suggested prompt**

Find:
```html
    <div class="prompt">
      <div class="lbl">💬 Your first question to try — copy this exactly:</div>
      "I'm a ham radio operator in VK4. Explain WSPR to me in simple terms. Is the 40m band open to Japan right now, and how would I check?"
    </div>
```
Replace with:
```html
    <div class="prompt">
      <div class="lbl">💬 Paste in any manual page, then ask:</div>
      "Here is a page from a radio manual or operating guide. Summarise the key points in plain English as a short dot-point checklist for someone returning to HF after 20 years."
    </div>
```

**Step 6: Open `ham-ai-presentation.html` in a browser and navigate to Slide 14. Verify:**
- Heading reads "Read a Radio Manual with AI 📄"
- Gold line updated
- Prompt text updated
- Red demo style and QR codes unchanged

---

## Task 2: Insert the new exam-tutor demo slide in the presentation file

**Files:**
- Modify: `ham-ai-presentation.html` — insert after line ~745 (end of current Slide 14 `</div>`)

**Step 1: Insert the new slide block**

After the closing `</div>` of Slide 14 (the line that ends with `</div>` before the `<!-- SLIDE 15 — WSPR INTRODUCTION -->` comment), insert:

```html

<!-- ══════════════════════════════════════════════════════
     SLIDE 15 — DEMO: AI AS YOUR EXAM TUTOR
══════════════════════════════════════════════════════ -->
<div class="slide demo-slide"
  data-notes="• DEMO — phones are already out from the previous demo (5 minutes).
• Ethical framing is important — say it before showing the prompts: 'Not to cheat — to understand why the answer is right.'
• Frame it as useful for anyone upgrading, mentoring a new member, or brushing up on theory.
• Walk through the three prompts in order — show how AI builds on each answer.
• Invite someone to share what level explanation they found most useful.">

  <div class="sh" style="background:var(--red);padding:14px 48px;">
    <div class="live"><div class="dot"></div> LIVE DEMO</div>
    <h2 style="margin-left:18px;margin-bottom:0;">AI as Your Exam Tutor 🎓</h2>
  </div>
  <div style="flex:1;padding:20px 48px;display:flex;flex-direction:column;gap:14px;">
    <div class="hl gold" style="font-size:21px;text-align:center;">
      Not to cheat — to understand <em>why</em> the answer is right
    </div>
    <div class="hl" style="font-size:20px;margin-bottom:4px;">
      <strong>Sample theory question:</strong><br>
      "What does an SWR of 3:1 indicate, and what is the likely effect on your transmitter?"
    </div>
    <div style="display:flex;flex-direction:column;gap:10px;">
      <div class="step">
        <div class="step-num">1</div>
        <div>"Explain why the correct answer is right, in plain English."</div>
      </div>
      <div class="step">
        <div class="step-num">2</div>
        <div>"Explain it at three levels: beginner, Standard licence, and Advanced licence."</div>
      </div>
      <div class="step">
        <div class="step-num">3</div>
        <div>"Give me two more practice questions on the same topic."</div>
      </div>
    </div>
  </div>
</div>
```

**Step 2: Update the old Slide 15 comment to Slide 16**

Find:
```html
<!-- ══════════════════════════════════════════════════════
     SLIDE 15 — WSPR INTRODUCTION
══════════════════════════════════════════════════════ -->
```
Replace with:
```html
<!-- ══════════════════════════════════════════════════════
     SLIDE 16 — WSPR INTRODUCTION
══════════════════════════════════════════════════════ -->
```

**Step 3: Update the old Slide 16 comment to Slide 17**

Find:
```html
<!-- ══════════════════════════════════════════════════════
     SLIDE 16 — DEMO: PROPAGATION TOOLS
══════════════════════════════════════════════════════ -->
```
Replace with:
```html
<!-- ══════════════════════════════════════════════════════
     SLIDE 17 — DEMO: PROPAGATION TOOLS
══════════════════════════════════════════════════════ -->
```

**Step 4: Update remaining slide comment numbers (17→18 through 22→23)**

Find and replace each in sequence:
- `SLIDE 17 — SAFETY TIPS` → `SLIDE 18 — SAFETY TIPS`
- `SLIDE 18 — LIMITATIONS` → `SLIDE 19 — LIMITATIONS`
- `SLIDE 19 — DISCUSSION` → `SLIDE 20 — DISCUSSION`
- `SLIDE 20 — FIRST STEPS` → `SLIDE 21 — FIRST STEPS`
- `SLIDE 21 — TOOLS DIRECTORY` → `SLIDE 22 — TOOLS DIRECTORY`
- `SLIDE 22 — THANK YOU` → `SLIDE 23 — THANK YOU`

**Step 5: Navigate to the new Slide 15 in browser. Verify:**
- Red demo-slide style, animated LIVE dot
- Gold ethical-framing line visible
- Sample SWR question readable at a glance
- Three `.step` cards render correctly
- No QR codes (correct — phones already out)

---

## Task 3: Update the script file — Slide 14

**Files:**
- Modify: `ham-ai-script.html` lines ~804–855

**Step 1: Replace the Slide 14 heading**

Find:
```html
    <h2>🔴 Live Demo — Try ChatGPT Now</h2>
```
Replace with:
```html
    <h2>🔴 Live Demo — Read a Radio Manual with AI</h2>
```

**Step 2: Replace the Slide 14 talking points `<ul>`**

Find:
```html
      <ul>
        <li>Ask everyone to get out their phone or tablet</li>
        <li>QR codes on screen — scan to open ChatGPT or Claude</li>
        <li>Walk around the room and help anyone who needs it</li>
        <li>Have a backup device (club tablet/laptop) ready for anyone who can't access it</li>
        <li>The suggested question on screen gives a great result every time</li>
        <li>Allow time for people to see results and react</li>
      </ul>
```
Replace with:
```html
      <ul>
        <li>Ask everyone to get out their phone or tablet</li>
        <li>QR codes on screen — scan to open ChatGPT or Claude</li>
        <li>Walk around the room and help anyone who needs it</li>
        <li>Have a backup device (club tablet/laptop) ready for anyone who can't access it</li>
        <li>Intro line: "Most of us have opened a radio manual, found the answer on page 83, and still not felt much wiser."</li>
        <li>Invite them to paste any manual page — or use the on-screen example prompt as-is</li>
        <li>Follow-up prompts: "Turn this into a 5-step checklist" / "Explain this for someone returning to HF after 20 years"</li>
      </ul>
```

**Step 3: Replace the Slide 14 script paragraphs**

Find the entire script section for Slide 14:
```html
      <p>
        <span class="cue red">DEMO — Pause the slides. Get everyone hands-on.</span>
      </p>
      <p>
        Alright — this is the bit I've been looking forward to. Please get out your phone or your tablet if you have one.
        We're going to try this together right now.
      </p>
      <p>
        On the screen you can see two QR codes. Scan one of them — either ChatGPT or Claude — with your phone camera.
        If you're not sure how to scan a QR code, just point your camera at the big square pattern and a link should appear on the screen.
        <span class="cue">Walk around and help anyone who's struggling. Give it a minute.</span>
      </p>
      <p>
        If you already have an account, brilliant — just log in.
        If not, tap "Sign up," enter your email address, choose a password, and you're in.
        It takes about ninety seconds.
        <span class="cue">Wait for most of the room to be at the text box.</span>
      </p>
      <p>
        Now — on the screen there's a question. Type it in, or something like it, and hit send.
        <span class="cue">Read the suggested question aloud:</span>
        "I'm a ham radio operator in VK4. Explain WSPR to me in simple terms. Is the 40m band open to Japan right now, and how would I check?"
      </p>
      <p>
        <span class="cue">Wait 30–60 seconds while people read their answers.</span>
        What did it say? Has anyone got an interesting response? 
        <span class="cue green">Invite two or three people to share what their screen said. React naturally — "yes, that's a good explanation," "interesting, it gave you a slightly different example," etc.</span>
      </p>
      <div class="transition">➜ Next slide — WSPR background, then second demo</div>
```
Replace with:
```html
      <p>
        <span class="cue red">DEMO — Pause the slides. Get everyone hands-on.</span>
      </p>
      <p>
        Alright — this is the bit I've been looking forward to. Please get out your phone or your tablet if you have one.
        We're going to try this together right now.
      </p>
      <p>
        On the screen you can see two QR codes. Scan one of them — either ChatGPT or Claude — with your phone camera.
        If you're not sure how to scan a QR code, just point your camera at the big square pattern and a link should appear on the screen.
        <span class="cue">Walk around and help anyone who's struggling. Give it a minute.</span>
      </p>
      <p>
        If you already have an account, brilliant — just log in.
        If not, tap "Sign up," enter your email address, choose a password, and you're in.
        It takes about ninety seconds.
        <span class="cue">Wait for most of the room to be at the text box.</span>
      </p>
      <p>
        Most of us have opened a radio manual, found the answer somewhere on page 83, and still not felt much wiser.
        Let's see what AI does with the same page.
      </p>
      <p>
        On the screen is a prompt you can use as-is — or if you have a manual, a rig guide, or any technical page handy on your phone, paste that in instead.
        <span class="cue">Read the suggested prompt aloud:</span>
        "Here is a page from a radio manual or operating guide. Summarise the key points in plain English as a short dot-point checklist for someone returning to HF after 20 years."
      </p>
      <p>
        <span class="cue">Wait 30–60 seconds while people read their answers.</span>
        What came back? Anyone get a clean checklist?
        <span class="cue green">Invite two or three people to share. Then suggest a follow-up:</span>
        If you want to keep going, try asking: "Turn this into a 5-step checklist" — or — "Explain this for someone returning to HF after 20 years."
        That shows how you can have a conversation with it, not just ask one question.
      </p>
      <div class="transition">➜ Next slide — exam tutor demo</div>
```

---

## Task 4: Insert new exam-tutor slide block in the script file

**Files:**
- Modify: `ham-ai-script.html` — insert after line ~855 (end of Slide 14 `</div>`)

**Step 1: Insert new slide block after the closing `</div>` of Slide 14, before the `<!-- SLIDE 15 -->` comment**

```html

<!-- SLIDE 15 -->
<div class="slide-block">
  <div class="slide-header">
    <div class="slide-num">15</div>
    <h2>🔴 Live Demo — AI as Your Exam Tutor</h2>
    <span class="timing">~5 min</span>
  </div>
  <div class="slide-body">
    <div class="points">
      <h3>Talking Points</h3>
      <ul>
        <li>Phones are already out — no QR codes needed, just use what's open</li>
        <li>Ethical framing first: "Not to cheat — to understand why the answer is right"</li>
        <li>Useful for anyone upgrading, mentoring a new member, or brushing up on theory</li>
        <li>Walk through the three prompts in order — show how AI builds on each answer</li>
        <li>The three-level explanation (beginner / Standard / Advanced) is the most impressive step</li>
      </ul>
    </div>
    <div class="script">
      <h3>Script</h3>
      <p>
        <span class="cue red">DEMO — Phones are still out. No new QR codes needed.</span>
      </p>
      <p>
        Now I want to show you something that is really useful for anyone who is studying for their Standard or Advanced licence — or for anyone mentoring a new member, or just brushing up on theory they learned decades ago.
      </p>
      <p>
        Before I show you, one thing I want to say clearly: this is not about cheating on an exam.
        The WIA exam is closed-book and invigilated — AI won't help you in the room.
        What it <em>can</em> do is be a very patient tutor who explains concepts until they actually make sense.
      </p>
      <p>
        Here's the sample question on screen: "What does an SWR of 3:1 indicate, and what is the likely effect on your transmitter?"
        <span class="cue">Give people a moment to read it.</span>
      </p>
      <p>
        Now try this first prompt in ChatGPT or Claude — type:
        <span class="cue">Read aloud:</span>
        "Explain why the correct answer is right, in plain English."
        <span class="cue">Wait for responses.</span>
        That's step one — understanding the concept.
      </p>
      <p>
        Now try step two:
        <span class="cue">Read aloud:</span>
        "Explain it at three levels: beginner, Standard licence, and Advanced licence."
        <span class="cue">Wait. Then invite someone to share the beginner version versus the Advanced version.</span>
        Notice how it adapts the depth depending on what you asked for. That's what a good tutor does.
      </p>
      <p>
        And finally, step three:
        <span class="cue">Read aloud:</span>
        "Give me two more practice questions on the same topic."
        <span class="cue">Wait for responses.</span>
        Suddenly you have a personalised study session on exactly the topic you're working on.
      </p>
      <p>
        <span class="cue green">Ask: "Has anyone used AI for study like this before?" — take a show of hands or a brief comment.</span>
        That is AI as a tutor — not an answer machine.
      </p>
      <div class="transition">➜ Next slide — WSPR background</div>
    </div>
  </div>
</div>
```

---

## Task 5: Renumber script slide blocks 15→16 through 22→23

**Files:**
- Modify: `ham-ai-script.html`

The old Slide 15 block (WSPR intro) through old Slide 22 (Thank You) each need their `<!-- SLIDE N -->` comment and `<div class="slide-num">N</div>` updated.

Make these replacements in order:

| Find (comment) | Replace | Find (slide-num) | Replace |
|---|---|---|---|
| `<!-- SLIDE 15 -->` | `<!-- SLIDE 16 -->` | `<div class="slide-num">15</div>` | `<div class="slide-num">16</div>` |
| `<!-- SLIDE 16 -->` | `<!-- SLIDE 17 -->` | `<div class="slide-num">16</div>` | `<div class="slide-num">17</div>` |
| `<!-- SLIDE 17 -->` | `<!-- SLIDE 18 -->` | `<div class="slide-num">17</div>` | `<div class="slide-num">18</div>` |
| `<!-- SLIDE 18 -->` | `<!-- SLIDE 19 -->` | `<div class="slide-num">18</div>` | `<div class="slide-num">19</div>` |
| `<!-- SLIDE 19 -->` | `<!-- SLIDE 20 -->` | `<div class="slide-num">19</div>` | `<div class="slide-num">20</div>` |
| `<!-- SLIDE 20 -->` | `<!-- SLIDE 21 -->` | `<div class="slide-num">20</div>` | `<div class="slide-num">21</div>` |
| `<!-- SLIDE 21 -->` | `<!-- SLIDE 22 -->` | `<div class="slide-num">21</div>` | `<div class="slide-num">22</div>` |
| `<!-- SLIDE 22 -->` | `<!-- SLIDE 23 -->` | `<div class="slide-num">22</div>` | `<div class="slide-num">23</div>` |

> **Note:** The existing new `<!-- SLIDE 15 -->` inserted in Task 4 is already correct. Start renumbering from the first old-15 comment that appears *after* that inserted block.

---

## Task 6: Update the timing table and section divider in the script file

**Files:**
- Modify: `ham-ai-script.html` lines ~258–270

**Step 1: Replace the run-sheet timing table rows**

Find:
```html
  <tr class="demo"><td>14</td><td>🔴 LIVE DEMO — Try ChatGPT</td><td>8–10 min</td><td>42 min</td></tr>
  <tr><td>15–16</td><td>WSPR + propagation tools</td><td>6 min</td><td>48 min</td></tr>
  <tr class="demo"><td>16</td><td>🔴 LIVE DEMO — WSPR maps</td><td>5 min</td><td>53 min</td></tr>
  <tr><td>17–18</td><td>Safety &amp; limitations</td><td>8 min</td><td>61 min</td></tr>
  <tr class="disc"><td>19</td><td>💬 Discussion</td><td>12–15 min</td><td>76 min</td></tr>
  <tr><td>20–22</td><td>First steps, tools &amp; close</td><td>6 min</td><td>82 min</td></tr>
```
Replace with:
```html
  <tr class="demo"><td>14</td><td>🔴 LIVE DEMO — Manual search &amp; summary</td><td>8–10 min</td><td>42 min</td></tr>
  <tr class="demo"><td>15</td><td>🔴 LIVE DEMO — Exam tutor</td><td>5 min</td><td>47 min</td></tr>
  <tr><td>16–17</td><td>WSPR + propagation tools</td><td>6 min</td><td>53 min</td></tr>
  <tr class="demo"><td>17</td><td>🔴 LIVE DEMO — WSPR maps</td><td>5 min</td><td>58 min</td></tr>
  <tr><td>18–19</td><td>Safety &amp; limitations</td><td>8 min</td><td>66 min</td></tr>
  <tr class="disc"><td>20</td><td>💬 Discussion</td><td>12–15 min</td><td>81 min</td></tr>
  <tr><td>21–23</td><td>First steps, tools &amp; close</td><td>6 min</td><td>87 min</td></tr>
```

---

## Task 7: Commit

```bash
cd /brandon/iadrc-ai-pres
git add ham-ai-presentation.html ham-ai-script.html
git commit -m "feat: update demo slides — manual summary and exam tutor demos

- Slide 14: replace generic WSPR prompt with radio manual summarise demo
- Slide 15 (new): AI exam tutor demo with SWR theory question and 3-step prompts
- Old slides 15–22 renumbered 16–23 in both presentation and script
- Timing table updated to reflect new demo sequence

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>"
```
