---
title: "Solana Lesson 8: Hackathon Submission — Pitch, Demo, GitHub, Validation"
type: lesson
difficulty: advanced
tags: [solana, hackathon, colosseum, pitch, demo, github, validation, build-in-public]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 8
---

# Solana Lesson 8: Hackathon Submission — Pitch, Demo, GitHub, Validation

**Format:** Instructor-led, in the room or online — screen sharing + hands-on practice
**Duration:** ~2.5 hours

## How This Lesson Works

Same flow: instructor explains → demonstrates → drops prompt in chat → students copy-paste and repeat → wait for all → questions → next section.

This lesson packages everything you've built into a submission ready for the **Colosseum fall hackathon (September 28 — November 2, 2026)** — using Colosseum's own published guidance.

---

## Prerequisites

From Lessons 1-7, every student must have:
1. ✅ Working product: mobile app + APK + (optionally) backend
2. ✅ Judge-ready GitHub repository
3. ✅ Database connected
4. ✅ A few real users who tried the app
5. ✅ A Google/Gmail account (for Loom and Colosseum)

---

## Part 1: What a Colosseum Submission Actually Is

From Colosseum's own workshop ("Perfecting Your Hackathon Submission"), a submission has these parts:

| Part | What it is | Colosseum's bar |
|------|-----------|-----------------|
| **Project form** | Online form: name, description, links, answers | Fill EVERY field — empty optional fields hurt |
| **Pitch video** | ≤ 3 minutes, "why" | The FIRST thing judges watch — decides shortlisting |
| **Technical demo** | 2-3 minutes, "how" | Shows real implementation, Solana integration |
| **GitHub repo** | Your code, public | Judges read it — README, commits, quality |
| **Weekly updates** | Short progress videos during the hackathon | Signal of momentum and iteration |

**The two videos serve different purposes:**

```
Pitch video      = WHY    → team, problem, users, vision  (a startup pitch)
Tech demo video  = HOW    → stack, Solana integration, decisions (an engineering walkthrough)
```

**Chat drop:** Open colosseum.com/hackathon → read the FAQ answers about submission requirements. Write down the two video length limits.

---

## Part 2: Team — Solo or Together?

Colosseum's guidance: winning teams are small but rarely solo — commonly **2-4 people**, usually mixing technical and non-technical founders. Solo entries are allowed, but you have to explain why you're the right person to do this alone. Their own advice is blunt: find at least one cofounder, because a hackathon is an emotional rollercoaster and a team divides the work.

> ⚠️ Verify the current numbers on colosseum.com — this is the figure as of August 2026, and every season shifts it. The point that doesn't shift: judges fund *people*, and two committed people read as lower risk than one.

**You have options:**

| Option | How |
|--------|-----|
| **Classmate team (best)** | Pair up with someone from this course — you've built together for weeks |
| **Colosseum Cofounder Matching** | Platform feature: find founders by skills, commitment, location |
| **Solo** | Fine — prepare the "why I can do this alone" answer (AI helps below) |

In Zed:

```
Help me prepare for the team question in my hackathon submission.

My situation: [solo / team of N with roles X, Y, Z].

If solo: write a 3-sentence explanation of why I'm uniquely suited
to build this alone (my background, the AI tools I use, my speed).

If team: write a 2-sentence team background paragraph for the
submission form and pitch video.
```

**Chat drop:** Paste the prompt with your situation. Save the result — it goes into the pitch video script (Part 5).

---

## Part 3: Make Your GitHub Judge-Ready

Judges read repos. Colosseum's checklist, applied by AI. In Zed:

```
Run the code-review-and-quality skill on my repository, but with
hackathon judges as the audience.

Audit my GitHub repo:
1. README.md — does it explain: what the product is, why it
   matters, how to run it, the architecture, the Solana integration?
   Rewrite it to be excellent (screenshots welcome — tell me what
   to capture).
2. LICENSE file — add MIT if missing (open source is a grant
   criterion and judges like it).
3. Commit history — is it clean? Are messages descriptive?
4. Repo structure — can a stranger find the mobile app, backend,
   and docs in under a minute?
5. Secrets — one final scan for anything that shouldn't be public.
6. Links — add the APK download and any public URLs to the README.

Fix everything, commit, push. Show me a summary of changes.
```

**Chat drop:** Paste the prompt. Open your repo as if you were a judge seeing it for the first time — what's your first impression?

---

## Part 4: Validation — Find Your First Real Users

Colosseum's words: judges look for *"evidence that a team is solving a real problem for real users… feedback on platforms like Twitter or Telegram."* Even informal feedback counts.

**The homework from Lessons 6-7 already started this.** Now do it systematically — the goal is **5 real users** with concrete feedback:

1. Send your APK to 5 people (friends, family, group chats)
2. Ask each: "What did you expect? What confused you? Would you use this again?"
3. Write down their answers **verbatim** — real quotes are gold in the pitch

In Zed:

```
Help me turn user feedback into submission material.

Here is the feedback I collected:
[Paste your users' quotes]

Write:
1. A "Validation" paragraph for my submission form: what users
   said, what I changed because of it, with 1-2 direct quotes
2. One specific improvement to make to the product based on the
   most common complaint — add it to PLAN.md as the next task
```

**Chat drop:** Paste the prompt with your real quotes. Make the one improvement AI identified (with AI's help), commit, push.

---

## Part 5: The Pitch Video — ≤ 3 Minutes, "Why"

This video decides whether judges look deeper. Colosseum's recipe:

- **No more than 3 minutes** (over = instant fail signal)
- Team background, the problem, who it's for, validation received, the vision
- A clear narrative beats fancy editing — voiceover over slides is fine
- It's a **startup pitch**, not a product tour

In Zed:

```
Write the script for my 3-minute hackathon pitch video.

Use Colosseum's guidance:
- ≤ 3 minutes when spoken (~400-450 words)
- Structure: hook (15s) → team (20s) → problem (30s) → solution
  (40s) → live demo moment (30s, I'll show the app) → validation
  with real user quotes (30s) → Solana integration in one sentence
  (15s) → vision & what's next (20s)
- Simple, spoken English — no buzzwords, no jargon

Base it on: SPECIFICATION.md, my user feedback, and the team
paragraph from Part 2.

Save to PITCH_VIDEO_SCRIPT.md. Then give me recording tips:
- what to show on screen when (app, explorer, GitHub)
- one take vs multiple takes advice
```

**Record it** with [Loom](https://loom.com) (free) — screen + your voice. 3 minutes. Don't chase perfection; clarity wins.

> 📄 This is the **hackathon** pitch (3 minutes, for judges). In Lesson 9 you'll write a longer one for your classroom defense, saved as `DEFENSE_SCRIPT.md`. Two audiences, two scripts, two files — don't overwrite one with the other.

**Sharpening your story with NotebookLM (notebook.google.com):** NotebookLM is Google's AI notebook — you upload your documents and it reads them. Use it as a second brain for the pitch:

1. Go to [notebook.google.com](https://notebook.google.com) → create a notebook
2. Upload RESEARCH.md, SPECIFICATION.md, and your user feedback notes
3. Ask it: "What's the strongest angle for my 3-minute pitch? What should I cut?"
4. Steal its best 2-3 phrasings for your script — it reads your sources, not generic advice

**Chat drop:** Paste the script prompt → practice reading aloud twice → record with Loom → watch your own video → re-record if needed (most people do 2-3 takes).

**Bonus (optional):** In NotebookLM, generate an **Audio Overview** of your materials — a podcast-style discussion of your project. Listening to it is a fast way to hear how strangers perceive your idea.

---

## Part 6: The Technical Demo — 2-3 Minutes, "How"

Colosseum: *"technical, direct, and specific to implementation… walk through the core features, explain the tech stack, and the decisions made… particularly with regard to Solana integration, on-chain logic, and overall architecture."*

In Zed:

```
Write the script for my 2-3 minute technical demo video.

Colosseum's guidance:
- 2-3 minutes (~350-450 words)
- Structure: architecture overview (30s) → tech stack (20s) →
  walkthrough of the Solana integration (60s: wallet connect,
  what's on-chain, why) → the trickiest technical decision and
  why I made it (30s) → what I'd improve (20s)
- I'll screen-record: code on one side, app demo on the other
  (or cut between them)

Save to TECH_DEMO_SCRIPT.md. Add a shot list: what to record in
order (screen areas, app screens, explorer links).
```

**Record it** the same way — Loom, screen recording. Show real code, a real transaction on the explorer, and the app working.

**Chat drop:** Paste the script prompt → record → watch → re-record if needed.

---

## Part 7: Build in Public — X Account + Weekly Updates

Colosseum: *"we strongly recommend that hackathon participants build in the open from the start… create a project X account and begin sharing your product vision."* Why: it forces you to articulate the product, and it attracts beta testers.

In Zed:

```
Help me build in public for my hackathon project.

1. Write a profile bio and pinned post for a new X account
   for my product (name suggestion, one-line pitch, what I'll post)
2. Draft 5 initial posts (launch announcement, what I'm building,
   first transaction from my phone, user feedback, lesson learned)
3. Draft a "weekly update" template — Colosseum wants short weekly
   progress updates during the hackathon (what I shipped, what I
   learned, what's next)
4. Suggest 5 Solana/Colosseum accounts to follow and engage with

Save to BUILD_IN_PUBLIC.md.
```

**Chat drop:** Paste the prompt. Create the X account, post the first post. Follow @colosseum and @solana.

---

## Part 8: The Submission Checklist

Final pass. In Zed:

```
Act as my hackathon submission coach. Read Colosseum's common
mistakes list and audit my submission package:

1. Pitch video — under 3 minutes? Clear idea + impact? Team
   mentioned? Validation mentioned?
2. Tech demo — 2-3 minutes? Solana integration explained? Real
   product shown?
3. GitHub — README great? License? Clean history? Links work?
4. Form fields — draft answers for: project name, tagline,
   description, how it uses Solana, what stage it's at, links
5. Access check — if I shared any Google Docs/videos, are
   permissions set so judges can view them?

Create SUBMISSION_CHECKLIST.md with everything, marked ✅/❌,
and fix what we can today. Then mark the Phase 6 tasks in
PLAN.md accordingly.
```

**Chat drop:** Paste the prompt. Fix the ❌ items. This checklist is your week-before-hackathon ritual.

---

## Part 9: Dry-Run the Actual Submission

Here's the thing nobody tells you: **the submission itself happens weeks after this course ends.** The hackathon opens September 28; you'll be doing it alone, at home, possibly at 11pm on deadline day. So we rehearse it now, while there's a room full of people to ask.

**Open the real thing.** Go to [colosseum.com](https://colosseum.com), find the hackathon page, and open the submission form (or the FAQ describing it if registration hasn't opened for your season).

**Write down every field it asks for.** Then, in Zed:

```
Here are the fields the Colosseum submission form asks for:
[paste the list you just wrote down]

For each field, draft my answer using SPECIFICATION.md,
README.md, my validation quotes and PITCH_VIDEO_SCRIPT.md.

Rules:
- Respect any character limits; if I didn't note one, keep it
  tight anyway
- No field left empty — an empty optional field is a signal to
  judges that I gave up early
- Mark with ⬜ anything that can only be filled in later (video
  links, final repo state) so I know what's still missing
- Flag any field I can't answer well yet — that's a gap in the
  product, not just in the form

Save to SUBMISSION_DRAFT.md.
```

**Then the four things that go wrong every year:**

| Trap | Fix, today |
|------|-----------|
| Videos are private / "request access" | Set Loom links to *anyone with the link*. Test in a private browser window |
| Waiting for the product to be "ready" before submitting | Submit early — most forms let you edit until the deadline. A saved draft beats a perfect idea you never entered |
| Repo made public on deadline day, full of surprises | Yours has been public since Lesson 3. Check it once more anyway |
| Deadline in a timezone that isn't yours | Write the deadline in **your** local time in your calendar, with a reminder 48 hours before |

**Chat drop:** Open the form → list its fields → paste the prompt → get SUBMISSION_DRAFT.md → set your calendar reminders before you leave the room.

---

## Homework

1. Post your second build-in-public update on X
2. Watch 2 winning pitch videos from a past hackathon (find them via Colosseum's winner announcements) — write what made them good
3. Get one more real user (goal: 6+ total)
4. Put the hackathon dates in your calendar: Sep 28 — Nov 2, 2026; and a reminder to submit the form early (you can iterate after)
5. Group chat: post your pitch video link for peer feedback

---

## Troubleshooting

### My Pitch Is Over 3 Minutes

```
My pitch script is too long. Cut it to ~420 words while keeping:
hook, problem, solution, one validation quote, and the vision.
Rewrite it tighter.
```

### I'm Camera-Shy / My English Feels Weak

```
I'm nervous about recording. Give me 5 practical tips for a
3-minute voiceover, and simplify my script's language — short
sentences, simple words, no jargon.
```

### Loom Video Is Blurry / Audio Bad

```
My recording looks/sounds bad: [describe]. Give me Loom recording
settings advice (resolution, mic, screen area) and a better
recording setup.
```

### I Missed the Hackathon Start — Now What?

Colosseum runs **Eternal** year-round: 4-week sprints with weekly updates, judged by ecosystem founders, feeding the same accelerator. Ask AI: `Explain Colosseum Eternal and how I submit my product there instead.`

### Solo Founder Doubts

```
As a solo founder, what should I emphasize in my submission to
compensate for having no cofounder? Write the exact sentences for
the form and pitch.
```

---

## Related Materials

- [lesson-07](lesson-07.md) — Previous lesson: deployment & APK
- [lesson-09](lesson-09.md) — Next lesson: grant application & defense
- [lesson-02](lesson-02.md) — The research behind this playbook (Colosseum sources)
- *lesson-10-diploma* — Online English Lesson 10 (presentation source)
- *near-offline-lesson-06* — NEAR course final lesson (same defense format)

## Result

After this lesson, each student has:
- A submission package built to Colosseum's published standards:
  - Pitch video ≤ 3 minutes (PITCH_VIDEO_SCRIPT.md + recording)
  - Technical demo 2-3 minutes (script + recording)
  - Judge-ready GitHub repo (README, license, clean history)
  - SUBMISSION_DRAFT.md — every form field drafted, gaps marked
  - SUBMISSION_CHECKLIST.md
- 5+ real users with verbatim feedback, one improvement shipped from it
- A build-in-public presence: X account, first posts, weekly update template
- Team strategy (classmate, Cofounder Matching, or a solo explanation)
- A clear picture of the Sep 28 — Nov 2 hackathon timeline, with calendar reminders already set
