---
title: "Solana Course — Instructor Checklist"
type: guide
difficulty: intermediate
tags: [solana, instructor, checklist, teaching, preparation]
created: 2026-08-19
updated: 2026-08-19
---

# Instructor Checklist — Solana Course

This course is taught live, to people who cannot debug their own machines. Almost every failure mode is preventable with 30 minutes of preparation. This file is that 30 minutes.

Related: [README](README.md) · [overview](overview.md)

---

## Before the Course Starts (once)

### 1. Re-verify every external claim

**→ [verify-before-teaching](verify-before-teaching.md)** — a complete inventory of every date, price, package, URL and API this course depends on, with the exact lesson each one appears in and a place to record what you found.

Work through it before each cohort. Sections A (technical blockers) and B (Colosseum + grant facts) are not optional: the hackathon dates, the "you may start building early" window and the six grant criteria are the premises the whole course rests on.

### 2. Run the whole course yourself, on a clean machine

Not a skim — actually do it. The four things that can end a lesson are listed as **section A** of [verify-before-teaching](verify-before-teaching.md): DeepSeek's MCP tool-calling reliability, `solana-mcp`'s startup requirements, the Supabase MCP write-mode flag, and which MWA packages build against the current Expo SDK.

Beyond those, run both EAS build profiles end to end and time them on the free tier — students plan their lesson around that number.

### 3. Prepare the safety net

- [ ] **A funded devnet wallet of your own** — for students the faucet refuses. Keep 20+ devnet SOL
- [ ] **Recordings of the three fragile demos**: MWA connect, on-phone signing, APK install. If the classroom Wi-Fi dies, the lesson continues
- [ ] **A finished reference project** — one repo containing every artifact the course produces (SPECIFICATION.md through GRANT_APPLICATION.md). Students who fall behind copy its structure
- [ ] **A spare Android phone**, or a firm answer for students without one — arranged *before* Lesson 6, never during it
- [ ] **A pre-started EAS build** on the day of Lesson 6, so you can show the finished flow even if every student is queued

---

## Before Each Lesson

| Lesson | Check |
|--------|-------|
| **1** | Wi-Fi allows brew/npm/GitHub. Students told to bring a card for DeepSeek, and paper for seed phrases |
| **2** | Supabase, GitHub token and faucet all reachable from the classroom network. Have the fallback table on screen |
| **3** | `npx skills add addyosmani/agent-skills` works today — catalogues move |
| **4** | Your own MCP/CLI wallet funded. Faucet status checked that morning |
| **5** | Every student has an "Active" Supabase project. Chase this in the class chat the day before |
| **6** | **Highest-risk lesson.** Students have Phantom on the phone, an expo.dev account, and their seed phrase paper. Wi-Fi allows Expo tunnel mode — classroom networks with client isolation break LAN connections |
| **7** | Start your demo APK build before class. Know which students have a backend and which don't |
| **8** | Loom accessible. The Colosseum submission form (or its FAQ) open on the big screen |
| **9** | Timing arithmetic done: 5-7 min per student + questions. Group of 12+ needs two sessions or 4-minute slots |

---

## Running the Room

**The Product Build Track is the course's real risk.** Lessons 5, 6 and 7 open with a two-minute checkpoint: each student states how many Phase 4 tasks they've finished. Watch for anyone at zero twice in a row — they don't need more homework, they need a smaller Phase 4. Rescope it with them personally, that week.

**The 10-minute rule.** No student debugs one problem for more than 10 minutes of class time. Every lesson has a fallback; use it and move on. A student who spends Lesson 4 fighting an MCP config learns nothing about Solana.

**Secrets discipline, every single lesson.** The course rule is: AI writes configs with placeholders, students type real keys themselves. It's easy to let this slide when you're behind schedule. Don't — it's the one habit with consequences outside the classroom.

**Pair the stragglers.** From Lesson 6 onward, a student whose build is stuck should work on a neighbour's laptop rather than watch. They lose their own environment for an hour; they'd lose the whole lesson otherwise.

---

## Known Rough Edges

Honest list of the places this course is thin, so you can compensate:

1. **Nine sessions can't teach the stack *and* build nine products.** Phase 4 lives in homework. Say this out loud in Lesson 3 — students who expect a finished app from class time will be disappointed at Lesson 8
2. **Everything depends on third-party services** that change without notice: MCP packages, Expo SDK, faucets, hackathon rules. Re-verify before every cohort
3. **Windows is second-class.** It works, but nearly every command is written mac-first. A Windows-heavy group needs extra time in Lessons 1-2
4. **No smart contracts.** Students ship transfers and SPL tokens, not custom on-chain programs. That is a legitimate scope choice — but be straight about it in the Lesson 8 tech demo, where judges expect "on-chain logic"
5. **DeepSeek is cheap, not strong.** On the hardest agentic steps (Lesson 6 especially) a stronger model finishes in one pass where DeepSeek needs five. Know which model you'd switch to, and what it would cost, before a student asks
