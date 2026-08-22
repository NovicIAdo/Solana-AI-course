---
title: "Solana Off-line Course — README"
type: lesson
difficulty: beginner
tags: [solana, offline, colosseum, hackathon, mobile, grants, readme, course]
created: 2026-08-19
updated: 2026-08-19
---

# Solana Off-line Course — Build for the Colosseum Hackathon & Solana Mobile Grants

**Instructor-led classroom course · 9 lessons · ~23 hours · no coding skills required**

Detailed lessons live in this repository (`lesson-01` … `lesson-09`) plus [the course overview](overview.md). This file is only the short roadmap.

| File | What it is |
|---|---|
| [overview.md](overview.md) | Full course overview — read this first |
| [lesson-01.md](lesson-01.md) … [lesson-09.md](lesson-09.md) | The nine classroom lessons |
| [instructor-checklist.md](instructor-checklist.md) | How to run the room, per-lesson prep, known rough edges |
| [verify-before-teaching.md](verify-before-teaching.md) | Every external dependency, with verification dates |

> Some "Related Materials" entries appear in *italics* rather than as links. Those point at other parts of the AI School wiki that aren't published in this repository.

**Teaching this course?** Start with [instructor-checklist](instructor-checklist.md) (how to run the room) and [verify-before-teaching](verify-before-teaching.md) (everything external that needs re-checking first).

**Goal:** after these lessons a person with zero technical background can build an Android app on Solana with AI, submit it to the Colosseum fall hackathon (Sep 28 — Nov 2, 2026) and apply for a Solana Mobile Builder Grant.

> ⚠️ **Dates, prize amounts and grant criteria in this course were correct in August 2026 and change every season.** Lessons 2, 8 and 9 all tell students to verify them against the live sites; [verify-before-teaching](verify-before-teaching.md) lists every such claim with the exact lesson it appears in. Treat this README as a map, not a source.

---

## Short Lesson Descriptions

**Lesson 1: Setup — GitHub, Zed, DeepSeek, Phantom & Devnet** *(~3h)*
Install Zed + connect the DeepSeek API. Homebrew, Git, GitHub CLI. First project pushed to GitHub. AGENTS.md rules for AI. Create a Phantom wallet, switch to devnet, get free devnet SOL from the faucet, and register a Colosseum builder account. Includes the course cost table and the Windows path notes.

**Lesson 2: Tokens, Context, ALL MCP Servers & Ecosystem Research** *(~2.5h)*
Tokens and context optimization. Create the one project folder the whole course uses, and a Supabase project. Connect four MCP servers to Zed at once: GitHub, Supabase, Solana (devnet, funded keypair), Playwright (browser) — each with a documented fallback if it won't connect. Research the three targets with AI using the Playwright MCP: colosseum.com, solanamobile.com/grants, and the Solana ecosystem. Install the Colosseum Copilot skill. Save everything to RESEARCH.md, in the project repo.

**Lesson 3: Product Owner + AI Team — Spec-Driven Development with agent-skills** *(~3h)*
Install the addyosmani/agent-skills pack (one command). Turn your idea into a PRD with the spec-driven-development skill (after a one-question-at-a-time interview), break it into the course's seven phases, execute Phase 1, verify, review with agent personas (code-reviewer, security-auditor), and ship. Output: SPECIFICATION.md, PLAN.md, TEAM.md — Phase 1 built, and the Product Build Track started.

**Lesson 4: Solana Fundamentals — Wallets, Transactions, Tokens (via MCP)** *(~2h)*
How Solana works in plain language: accounts, SOL and lamports, transactions, SPL tokens, devnet, RPC. All practice via the Solana MCP: check balance, get funds, send SOL to a classmate, deploy your own SPL token — in plain English, no code. Full Solana CLI fallback for anyone whose MCP didn't connect.

**Lesson 5: Database — SupaBase (project + MCP from Lesson 2)** *(~2h)*
Why an app needs a database. AI designs the schema from your spec, creates tables and applies migrations via MCP, enables row-level security — with a SQL Editor fallback if the MCP is read-only. Output: a data-access module and a passing test script, ready for the app screen in Lesson 6.

**Lesson 6: Solana Mobile — Android App, Mobile Wallet Adapter & Seed Vault** *(~3h)*
Put Phantom on your phone and fund it. Build a real Android app with React Native + Expo — then leave Expo Go behind for an **EAS development build**, because Mobile Wallet Adapter needs native code Expo Go cannot host. Integrate MWA (sign transactions from Phantom on your phone), wire in the Lesson 5 database, and document a credible Seed Vault plan. This is what the Solana Mobile grants ask for.

**Lesson 7: Deployment & APK** *(~2.5h)*
Build the standalone APK with EAS Build (`preview` profile), install it on your phone, distribute it. Deploy a backend to fly.io only if you actually need one; otherwise a landing page on Vercel. And while the build compiles: the course's one **supervised build sprint** on your own product features.

**Lesson 8: Hackathon Submission — Pitch, Demo, GitHub, Validation** *(~2.5h)*
The Colosseum playbook: 3-minute pitch video, 2-3 minute technical demo, a judge-ready GitHub repo, early user validation, build in public on X, weekly updates, team formation (Cofounder Matching). Plus a dry run of the real submission form — because you'll be filling it in alone, weeks after this course ends. AI prepares everything; NotebookLM sharpens the story.

**Lesson 9: Final — Solana Mobile Grant Application & Project Defense** *(~3h)*
Write the grant application with AI against the six official criteria. Prepare the project defense: product analysis, 7-slide presentation, pitch, Q&A — and present to the group. Then plan the weeks between the last lesson and the hackathon, with calendar reminders set in the room.

---

## Where the Product Actually Gets Built

Class time teaches the stack. Your product grows on the **Product Build Track** — Phase 4 of PLAN.md, built as homework between lessons, with one supervised sprint in Lesson 7. Lessons 5, 6 and 7 open with a two-minute checkpoint so nobody drifts silently.

**Budget 3-5 hours a week outside class.** Nine classroom sessions cannot both teach the whole stack and build nine different products; this is how the course stays honest about that.

---

## What It Costs

| What | Cost |
|------|------|
| DeepSeek API | **$5 covers the whole course** — off-peak rates are pennies per million tokens |
| GitHub, Supabase, Expo, EAS free tier, Vercel, Phantom, Colosseum | Free |
| fly.io (only if your product needs a backend — most don't) | Usage-based, a few dollars a month |
| Solana devnet | Free — it's fake money, and we never touch mainnet |

**Typical total: about $5.** Also required: an Android phone (borrowable) for Lessons 6-9.

---

## Timeline

9 lessons × 3 per week → ~3 weeks. The course finishes **2-3 weeks before** the Colosseum fall hackathon starts (Sep 28, 2026). Hackathon: ~5 weeks, online, global. Solana Mobile Builder Grants run alongside it.

Those 2-3 weeks between the last lesson and the hackathon are planned in Lesson 9, Part 9 — finish the ⭐ feature, re-record the pitch, submit early, post weekly.

---

## Goal

After these lessons a person with **zero technical background** can:
- set up a full AI development environment (GitHub, Zed, DeepSeek, MCP servers, skills)
- research and plan a hackathon product like a founder
- use Solana from code: wallets, devnet, transactions, tokens (via AI)
- build an Android app with the Solana Mobile Stack and install the APK
- prepare a complete Colosseum hackathon submission (pitch + demo + repo)
- write a Solana Mobile grant application
- ship and present a real Solana product built entirely with AI tools
