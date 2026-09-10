---
title: "Solana Course — Overview"
type: synthesis
difficulty: beginner
tags: [solana, colosseum, hackathon, mobile, grants, overview, course]
created: 2026-08-19
updated: 2026-08-19
---

# AI School × Solana — Course Overview

Nine instructor-led lessons (~23 hours, 3 per week) where you build a real **Solana Android app** using AI, and get ready to compete in the **Colosseum fall hackathon** (September 28 — November 2, 2026) and apply for the **Solana Mobile Builder Grants** program. No coding skills required — you describe what you want, AI builds it. Each lesson is taught live — in the room at Noviciado, or online in the shared room: you watch the screen, copy prompts from the chat, and repeat on your own laptop.

**Two things to know before you start.** First, class time teaches the stack; your product's own features are built on the **Product Build Track** — homework between lessons plus a supervised sprint in Lesson 7. Budget 3-5 hours a week outside class. Second, every date, prize and criterion below was accurate in **August 2026** and changes every season — Lessons 2, 8 and 9 all have you verify them against the live sites, and [verify-before-teaching](verify-before-teaching.md) lists every such claim, with the lesson it appears in, for the instructor to re-check before each cohort.

## The two targets of this course

- **Colosseum hackathon** — the world's largest online crypto hackathon; recent editions drew thousands of participants and thousands of submitted projects. Dozens of prizes, a large cash prize for the Grand Champion, and select winners join Colosseum's accelerator with pre-seed funding. The fall edition runs Sep 28 — Nov 2, 2026. Building before the official start is permitted within a published window — **verify that window in Lesson 2, because this entire course is built on it.**
- **Solana Mobile Builder Grants** — funding for teams building mobile-first crypto apps. The grant criteria are: mobile-first Android UX, **Solana Mobile Stack integration (Mobile Wallet Adapter + Seed Vault)**, realistic milestone timeline, team ability to execute, clear budget, open source. Grants run alongside the hackathon, with milestone-based payments.

*(Exact prize amounts, participant counts and grant sizes deliberately aren't listed here. They were checked in August 2026, they will be wrong by the time you read this, and a student who repeats a stale number to a judge looks careless. Lesson 2 has AI read the live pages instead.)*

One product hits both targets: **an Android app built on the Solana Mobile Stack**.

---

## Lesson 1: Setup — GitHub, Zed, DeepSeek, Phantom & Devnet

We set up the entire workspace. Install **Zed** and connect it to the **DeepSeek API** ($5 covers the whole course). Homebrew, Git, GitHub CLI, first AI-built project pushed to GitHub, and an **AGENTS.md** rules file. Then the Solana identity: a **Phantom wallet** (browser extension), switch to **devnet**, get free devnet SOL from the faucet, see it in the explorer, and register a **Colosseum** builder account. Two golden rules from day one: never share your seed phrase, never put keys in code.

## Lesson 2: Tokens, Context, All MCP Servers & Ecosystem Research

Tokens, the context window, and the skill that keeps AI cheap. Then the big move of the course: we connect **all four MCP servers to Zed in one pass** — **GitHub** (AI manages repos), **Supabase** (AI administers the database in Lesson 5), **Solana** (AI moves devnet money in Lesson 4), and **Playwright** (AI browses the web) — each with a written fallback if it refuses to connect. We also create the one project folder the whole course lives in, and the Supabase project Lesson 5 needs. After that we research the battlefield: **colosseum.com** (how the hackathon works, what judges look for, why AI tools now let very small teams compete), **solanamobile.com/grants** (the six evaluation criteria), and the Solana developer ecosystem — with AI reading the sites itself through the browser MCP. We install the **Colosseum Copilot skill**. Everything is saved to RESEARCH.md.

## Lesson 3: Product Owner + AI Team — Spec-Driven Development with agent-skills

Architecture and the AI team in one lesson, powered by one skill pack: **addyosmani/agent-skills** — 24 production-grade workflows from Google engineering culture, installed with one command. The workflow: *interview-me* (one question at a time until your idea is clear) → *spec-driven-development* (the PRD) → *planning-and-task-breakdown* (the course's seven phases, atomic tasks) → *incremental-implementation* (thin slices, committed one by one) → verification → review by agent personas (code-reviewer, security-auditor) → clean ship. In Zed you invoke a skill by naming it in your prompt; the `/spec`-style slash commands you'll see in skill docs belong to other tools. Output: SPECIFICATION.md, PLAN.md, TEAM.md, Phase 1 built and pushed — and the Product Build Track started.

## Lesson 4: Solana Fundamentals — Wallets, Transactions, Tokens (via MCP)

How Solana actually works, in plain language: accounts (wallet accounts vs data accounts), SOL and lamports, transactions and instructions, SPL tokens, devnet vs mainnet, RPC providers and explorers. Then practice — all through the **Solana MCP**, no code: AI checks the balance, funds the wallet, sends SOL to a classmate, and deploys the student's own SPL token on devnet. By the end of the lesson you've moved money on a blockchain and minted a token — from sentences, not code.

## Lesson 5: Database — SupaBase (via Zed MCP)

A real app stores data. We learn why (users, settings, game state) and how, with **SupaBase**: tables, row-level security, and a clean split between three kinds of key. The project and the **MCP server** were set up back in Lesson 2, so AI creates the schema, applies migrations and queries the database with its own tools — and if the MCP is read-only, AI writes SQL you paste into the dashboard instead. There's no app screen yet (that's Lesson 6), so the output is a data-access module plus a passing test script.

## Lesson 6: Solana Mobile — Android App, Mobile Wallet Adapter & Seed Vault

The core of the course. First we put **Phantom on your phone** and fund it on devnet. Then we build an **Android app** with React Native + Expo — and immediately leave Expo Go behind for an **EAS development build**, because the **Mobile Wallet Adapter** needs native Android code that Expo Go cannot host. (Expect this to be the surprise of the course; it's also the thing most tutorials get wrong.) With MWA integrated, your phone signs a real devnet transaction inside your own app, no seed phrase ever touching your code. **Seed Vault** — the secure key storage in Solana's Saga/Seeker phones — is researched, wired up to integration points and documented honestly: full testing needs a Solana phone, and grant reviewers know that. We also wire in the Lesson 5 database, so the app finally has real data.

## Lesson 7: Deployment & APK

The app leaves the laptop. We build the standalone **APK** with EAS Build's `preview` profile, transfer it to the phone and install it — no laptop required to run it any more. A backend goes to **fly.io** *only if the product genuinely needs one* (most don't, and fly.io is not free); otherwise a landing page on **Vercel**. Secrets live in `.env` and in platform vaults, never in code. And because cloud builds mean waiting, the wait is spent on the course's one **supervised build sprint** — 40 minutes on your own Phase 4 features, with the instructor walking the room.

## Lesson 8: Hackathon Submission — Pitch, Demo, GitHub, Validation

The Colosseum playbook, straight from their own workshop: a **pitch video ≤ 3 minutes** (team, problem, who it's for, validation, vision — a startup pitch, not a product tour), a **technical demo 2-3 minutes** (tech stack, Solana integration, the reasoning behind decisions), a judge-ready **GitHub repo**, early **user validation** (find 5 real users), **build in public** on X, weekly updates, and team formation via **Cofounder Matching**. AI writes the scripts, you record. We finish by opening the real submission form and drafting every field — because you'll be filling it in alone, weeks after the course ends.

## Lesson 9: Final — Solana Mobile Grant Application & Project Defense

The finish line. AI drafts the **grant application** against the six official criteria: mobile-first implementation, SMS integration, milestone timeline, team, budget, open source. Then the defense: product analysis, 7-slide presentation, 5-minute pitch, prepared Q&A — and every student presents live to the group. Last act: planning the two-to-three weeks between this lesson and September 28, with the calendar reminders set before anyone leaves the room.

---

**After this course you can:**
- Set up a complete AI development environment and work like a Product Owner
- Research, spec, plan, build and review a product with an AI team (agent-skills)
- Use Solana from code: devnet, faucet, transfers, tokens — via prompts
- Build an Android app on the Solana Mobile Stack and install the APK on your phone
- Prepare a complete Colosseum hackathon submission (pitch + demo + repo + validation)
- Write a Solana Mobile grant application
- Present and defend your product
- Plan the gap between the course and the hackathon, and submit on time
- All without writing a single line of code by hand
