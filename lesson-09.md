---
title: "Solana Lesson 9: Final — Solana Mobile Grant Application & Project Defense"
type: lesson
difficulty: advanced
tags: [solana, grants, solana-mobile, application, budget, milestones, presentation, defense, notebooklm]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 9
---

# Solana Lesson 9: Final — Solana Mobile Grant Application & Project Defense

**Format:** Instructor-led, in the room or online — screen sharing + hands-on practice + final presentations
**Duration:** ~3 hours for a group of 8-10 (first half ~90 min of writing; second half 5-7 min per student plus questions). **Larger group?** Split the defenses across two sessions, or cut each slot to 4 minutes — do the arithmetic before the lesson, not during it.

## How This Lesson Works

**First half:** All students write their Solana Mobile grant application and prepare their defense with AI assistance.
**Second half:** Each student presents their product to the group (5-7 minutes each).

---

## Prerequisites

Every student must have:
1. ✅ Working product: Android app + APK + Solana integration (Lessons 6-7)
2. ✅ Submission package from Lesson 8 (videos, repo, validation)
3. ✅ GitHub repository, public
4. ✅ SPECIFICATION.md, PLAN.md, RESEARCH.md

---

## Part 0: Two Final Goals

Today has two deliverables:

1. **The Solana Mobile grant application** — a written proposal judged against six official criteria. Even if you don't apply this round, writing it forces you to think like a funded founder.
2. **The project defense** — you present your product to the group, exactly like the hackathon pitch you'll give judges.

The two feed each other: the grant application sharpens your story, and the defense gives you live practice.

---

## Part 1: Write the Grant Application

The official Solana Mobile Builder Grants criteria (from solanamobile.com/grants):

> ⚠️ **Open solanamobile.com/grants on the big screen right now and compare.** These six criteria are what the page said in August 2026. Grant programs get renamed, repriced and restructured. Writing an application against last season's criteria is the most avoidable mistake in this lesson — and if the program is closed this season, the application is still worth writing: it is the clearest statement of your product you will ever produce, and it feeds directly into the hackathon form.

| # | Criterion | What it asks |
|---|-----------|--------------|
| 1 | Mobile-First Implementation | Mobile-first UX on Android, native features where appropriate |
| 2 | Solana Mobile Stack Use | MWA and Seed Vault integration — seamless, secure mobile experience |
| 3 | Proposed Scope & Milestone Timeline | Realistic scope, major milestones, phased delivery |
| 4 | Team Ability to Execute | Open source record, technical expertise, ability to deliver |
| 5 | Clear Use of Funds | Detailed budget — exactly how the grant money is used |
| 6 | Community & Open Source | Public goods, ecosystem improvement, community benefit |

In Zed:

```
Write my Solana Mobile Builder Grant application.

Sources to read first: SPECIFICATION.md, PLAN.md, RESEARCH.md,
README.md (which documents my Solana Mobile Stack integration),
and my user validation notes.

Create GRANT_APPLICATION.md covering all six official criteria:

1. Mobile-First Implementation — describe the Android UX, the
   native-feeling flows, screenshots list (tell me what to capture)
2. Solana Mobile Stack Use — Mobile Wallet Adapter (integrated:
   connect + sign + send on devnet), Seed Vault (prepared, Seeker
   mode), dApp Store (planned)
3. Milestone Timeline — 3 milestones over ~3 months, each with
   deliverables and a "done when" criterion, derived from PLAN.md
4. Team — my background, what I built, the AI-assisted workflow,
   evidence (my public GitHub)
5. Budget — realistic line items in USD. First check what grant
   sizes this program actually offers right now; if you can't
   find a number, ask me and I'll read it off the page rather
   than you guessing. Then build the budget to fit: design,
   infrastructure, a test device, security review, marketing.
   Justify every line — a padded budget reads as inexperience
6. Community & Open Source — MIT license, public repo, build in
   public, how the app benefits the Solana ecosystem

Keep it under 250 lines. Professional but honest — no hype.
```

**Chat drop:** Paste the prompt. Read GRANT_APPLICATION.md. Mark the 2 criteria where you feel weakest — we'll strengthen them in Homework.

---

## Part 2: Product Analysis

In Zed, from your project folder:

```
Analyze my product.

Repository: [GitHub link]
APK: [how to get it]
Live demo: my phone / Expo

Tasks:
1. Study the code and architecture
2. Identify the 5 most important features
3. List all technologies used (Solana, MWA, SupaBase, Expo, AI…)
4. Highlight the smartest solutions and the Solana integration
5. List the security measures in place

Save to PRODUCT_ANALYSIS.md
```

---

## Part 3: Create the Presentation

In Zed:

```
Create a presentation of my product.

Use PRODUCT_ANALYSIS.md and my validation quotes.

Format: Markdown. Structure (7 slides):

1. Title — product name, my name, date
2. Problem — what pain it solves, for whom, why now
3. Solution — what the product does (screenshots list)
4. Demo — user scenario step by step, with the on-phone flow
5. Technologies — Solana (devnet, MWA), SupaBase, React Native/
   Expo, AI tools
6. Architecture — component diagram described in text
7. Conclusion — validation quotes, grant plan, vision

Add speaker notes under each slide.

Save to PRODUCT_PRESENTATION.md
```

---

## Part 4: Pitch Script

In Zed:

```
Write a 5-minute pitch script for my classroom defense.

This is SEPARATE from PITCH_VIDEO_SCRIPT.md (the 3-minute
hackathon video from Lesson 8) — read that one for consistency
of story, but write a new, longer script. Do not overwrite it.

Use PRODUCT_PRESENTATION.md. Tone: confident, simple, friendly —
presenting to fellow students.

Structure: hook (15s) → problem → solution → live demo moment
(what I say while showing the app on my phone) → validation quote
→ technologies in one sentence each → what's next (hackathon,
grant) → closing line.

Save to DEFENSE_SCRIPT.md
```

---

## Part 5: Q&A Preparation

In Zed:

```
Prepare me for questions after my presentation.

Generate 10 likely questions. For each: the question, a short
confident answer, and one deeper fact in case someone pushes.

Include at least:
- one hard question about security (keys, seed phrases)
- one about "why Solana and not X"
- one about "why should you get a grant"
- one about competitors

Save to QA_PREP.md (no "&" in the filename — it breaks links and shell commands)
```

---

## Part 6: Beautiful Slides via NotebookLM

**NotebookLM** (Google's AI notebook at [notebook.google.com](https://notebook.google.com)) turns your documents into visuals:

1. Open [notebook.google.com](https://notebook.google.com) → new notebook
2. Upload `PRODUCT_PRESENTATION.md` and `PRODUCT_ANALYSIS.md`
3. Use its slides feature to generate a visual deck
4. Compare with your markdown — keep the better version, or mix
5. Download as PDF/PPTX

If the result misses the mark, tell AI in Zed:

```
The generated slides missed [what's missing]. Update
PRODUCT_PRESENTATION.md so NotebookLM produces a better result,
emphasizing [what matters].
```

**Chat drop:** NotebookLM → new notebook → upload → generate → download.

---

## Part 7: Rehearse with AI

In Zed:

```
You are a friendly but skeptical audience member at my final
presentation. I'll paste my script.

After I paste it, you:
1. Ask me the 3 hardest questions first
2. Point out the weakest part of my story
3. Suggest how to make the live demo moment memorable
4. Grade my pitch: clarity, structure, confidence — out of 10

Here is my script:
[Paste DEFENSE_SCRIPT.md]
```

**Chat drop:** Paste the rehearsal prompt → answer the 3 questions → fix your script → rehearse once more.

---

## Part 8: The Defense — Present to the Group

**Each student presents (5-7 minutes):**
1. Title + one-sentence idea
2. Problem → Solution (2 slides)
3. **Live demo** — the app on your phone: connect wallet, sign a transaction (or show the recording from Lesson 8 if Wi-Fi fails)
4. Technologies (1 slide)
5. Validation quote + what's next (grant, hackathon)
6. Audience questions (use your QA_PREP.md!)

**While others present:** write down one thing you'd steal for your own product.

---

## Part 9: The Weeks After This Course

The course ends today. The hackathon starts **September 28**. That gap — two to three weeks — is not a break; it's the part where most people quietly stop. Leave the room with it planned.

**The calendar, written down before you go:**

| When | What |
|------|------|
| This week | Finish the ⭐ Phase 4 feature if it's still open. Nothing else matters as much |
| Every week until Sep 28 | One build-in-public post. One new user. That's the whole ritual |
| ~Sep 21 | Re-record the pitch video with the finished product. The Lesson 8 version was a rehearsal |
| **Sep 28** | Hackathon opens → **submit the form the same week**, even if the product isn't finished. Most forms stay editable until the deadline |
| Weekly, Sep 28 → Nov 2 | Post the weekly update Colosseum asks for. Momentum is a judging signal |
| ~48h before the deadline | Final pass on SUBMISSION_CHECKLIST.md. Check every link in a private browser window |

**Set three calendar reminders right now, in this room:** Sep 28 (submit), the deadline minus 48 hours, and a weekly recurring one for the update post. Phone out, do it — this takes ninety seconds and it is the difference between having submitted and having meant to.

**Where to get help once the classroom is gone:**

- **Your class chat.** Keep it alive. These are the only people who know your product and your skill level. Agree today on a weekly check-in message
- **Your AI team.** TEAM.md, SPECIFICATION.md and PLAN.md still work. Nothing about your workflow depended on the classroom
- **Colosseum's own channels** — their Discord/community and Cofounder Matching, both researched back in Lesson 2
- **Missed the hackathon entirely?** Colosseum runs Eternal year-round. Ask AI: `Explain Colosseum Eternal and how I submit there instead.`

**Chat drop:** Everyone sets the three reminders now, out loud, together. Then post in the group chat: "Reminders set. Submitting on [date]."

---

## Homework

1. Push all final documents to GitHub (GRANT_APPLICATION.md, PRODUCT_ANALYSIS.md, PRODUCT_PRESENTATION.md, DEFENSE_SCRIPT.md, QA_PREP.md)
2. Strengthen your 2 weakest grant criteria (from Part 1) with AI
3. Actually submit the grant application if the round is open (solanamobile.com/grants) — or save it for the hackathon round
4. Put Sep 28 in your calendar: hackathon start, submit early
5. Set the three calendar reminders from Part 9 if you somehow left without them
6. Celebrate — you built a Solana product from zero, with AI.

---

## Troubleshooting

### Budget Feels Made-Up

```
My grant budget feels invented. Research what a typical mobile
dApp grant budget looks like and rebuild mine with realistic
line items and justifications.
```

### My Grant Application Is Too Long

```
GRANT_APPLICATION.md is over 250 lines. Compress it: cut repetition,
merge sections, keep every claim specific. Rewrite tighter.
```

### NotebookLM Won't Accept My File

Export as PDF or paste the content into a Google Doc and link that. Ask AI to convert if needed.

### I'm Nervous About Presenting

```
Act as my presentation coach. Give me 5 practical tips for a
5-minute demo presentation to a friendly student audience, and
one relaxation technique to use right before I start.
```

### Demo Fails Live (No Wi-Fi / Wallet Won't Open)

Always have the Lesson 8 recording as backup. And a screenshot. Tell the group honestly: "Wi-Fi is fighting me — here's the recorded demo." Judges respect preparation.

---

## Related Materials

- [lesson-08](lesson-08.md) — Previous lesson: hackathon submission
- [overview](overview.md) — Full course overview
- [lesson-02](lesson-02.md) — Grant criteria research (the source for Part 1)
- *lesson-10-diploma* — Online English Lesson 10 (defense source)
- *near-offline-lesson-06* — NEAR course final lesson (same format)

## Result

After this lesson, each student has:
- **GRANT_APPLICATION.md** — a complete Solana Mobile grant application against all six official criteria
- PRODUCT_ANALYSIS.md, PRODUCT_PRESENTATION.md (7 slides + speaker notes)
- DEFENSE_SCRIPT.md (5-minute defense pitch) and QA_PREP.md (10 prepared answers)
- Visual slides generated via NotebookLM
- Rehearsal with AI as the audience, graded
- A live 5-7 minute defense presented to the group
- A written plan and three calendar reminders for the weeks between today and the hackathon
- **A complete, deployed, demonstrated Solana mobile product — hackathon-ready and grant-ready**
