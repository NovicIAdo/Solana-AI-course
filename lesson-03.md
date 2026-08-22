---
title: "Solana Off-line Lesson 3: Product Owner + AI Team — Spec-Driven Development with agent-skills"
type: lesson
difficulty: intermediate
tags: [solana, offline, product-owner, agent-skills, spec, plan, prd, ai-team, personas, build]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 3
---

# Solana Off-line Lesson 3: Product Owner + AI Team — Spec-Driven Development with agent-skills

**Format:** Instructor-led classroom — screen sharing + hands-on practice
**Duration:** ~3 hours

## How This Lesson Works

Same flow: instructor explains → demonstrates → drops prompt in chat → students copy-paste and repeat → wait for all → questions → next section.

This is the densest lesson of the course — it replaces two lessons from the original program (Architecture + AI Agent Team) with one workflow. Expect to feel behind at some point; that's normal, and the artifacts you produce today are used by every remaining lesson.

---

## Prerequisites

From Lessons 1-2, every student must have:
1. ✅ Zed with DeepSeek connected
2. ✅ RESEARCH.md — researched Colosseum + grants + ecosystem
3. ✅ Colosseum Copilot skill installed
4. ✅ Phantom wallet on devnet
5. ✅ GitHub working, AGENTS.md in place

---

## Part 1: You Are the Product Owner

From now on you don't write code and you don't write documents. You are a **Product Owner**: you decide WHAT to build, AI decides HOW.

**But this time the stakes are higher.** In Lessons 1-2 you built warm-up projects. Today you start the product you will submit to the Colosseum hackathon — the thing you'll demo on stage in Lesson 9.

**What makes a hackathon-worthy idea (from Colosseum's own guides):**

| Principle | What it means | Example |
|-----------|---------------|---------|
| **Solve your own pain** | Build what YOU wish existed | A pro trader built the NFT terminal he wanted → Tensor (now a top product) |
| **Founder-market fit** | Build where you have life experience | You're a teacher → build for education; a gamer → build for gaming |
| **Mobile-first** | Our course targets Solana Mobile grants — the app must shine on Android | "Group chat + trading for friends" won Frontier as a mobile app |
| **Ambitious vision** | The hackathon demo is step one of a 10-year company | Judges fund founders, not weekend projects |
| **New market or better market** | Crypto unlocks something impossible before, or removes middlemen | Payments to friends abroad without banks |

**Your idea checklist:** does it use Solana meaningfully? Can you demo it on devnet in weeks? Would YOU use it daily?

### When does the product actually get built? — the Product Build Track

Be clear-eyed about this, starting today:

| | Where it happens |
|---|---|
| **Tools and infrastructure** — spec, database, wallet, mobile app, APK | **In class.** Lessons 3-7 |
| **Your product's actual features** — the thing that makes it *yours* | **On the Product Build Track:** homework between lessons, plus one supervised build sprint in Lesson 7 |

Nine classroom sessions cannot both teach the whole stack and build your product. So the course teaches the stack, and you build the product in between — with the same AI team, using the same PLAN.md. **Budget 3-5 hours a week outside class.** Lessons 5, 6 and 7 each open with a two-minute checkpoint on that track, so nobody drifts silently.

The students who win hackathons are the ones who do the homework. That is not a motivational line — it is the design of this course.

**Chat drop:** Brainstorm round: 3 minutes, write 5 possible ideas (even silly ones). Then share the best one with the class. No filtering yet.

---

## Part 2: Meet Your AI Team — The agent-skills Pack

Instead of manually telling AI how to plan, build, and review, we install **addyosmani/agent-skills** — 24 production-grade workflows from Google's engineering culture, packaged as skills. One command turns your AI into a disciplined engineering team.

```
DEFINE          PLAN           BUILD          VERIFY         REVIEW          SHIP
 ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐
 │ Idea │ ───▶ │ Spec │ ───▶ │ Code │ ───▶ │ Test │ ───▶ │  QA  │ ───▶ │  Go  │
 │Refine│      │  PRD │      │ Impl │      │Debug │      │ Gate │      │ Live │
 └──────┘      └──────┘      └──────┘      └──────┘      └──────┘      └──────┘
 interview-  spec-driven-   incremental-  debugging-   code-review-  git-workflow-
    me       development  implementation  and-error-   and-quality   and-versioning
                                           recovery
```

> 📎 **A note on `/spec`, `/plan`, `/build`.** Skill documentation often shows names like these — they are slash-command shortcuts in *some* AI tools. Zed has no such shortcuts. In Zed you invoke a skill by naming it in the prompt: *"Use the spec-driven-development skill…"*. Every prompt below is already written that way, so you can copy them verbatim.

**The skills we'll use today:**

| Stage | Skill | What it does for you |
|-------|-------|---------------------|
| Define | `interview-me` | Interviews you ONE question at a time until your idea is crystal clear |
| Define | `spec-driven-development` | Writes the PRD (product requirements) before any code |
| Plan | `planning-and-task-breakdown` | Breaks the spec into small, verifiable tasks |
| Build | `incremental-implementation` | Builds in thin slices, commits each step |
| Verify | `debugging-and-error-recovery` | Reproduces → localizes → fixes → guards |
| Review | `code-review-and-quality`, `security-and-hardening` | Reviews like a senior engineer; catches security issues |
| Ship | `git-workflow-and-versioning` | Clean, atomic commits |

**Your "team members" (agent personas included in the pack):**

| Persona | Role |
|---------|------|
| **code-reviewer** | Senior staff engineer — "would a staff engineer approve this?" |
| **security-auditor** | Security engineer — hunts vulnerabilities, checks secrets handling |
| **test-engineer** | QA specialist — proves the product works |
| **web-performance-auditor** | Performance engineer — we don't use it in this course, but it ships with the pack |

**Install the pack.** In Zed's AI panel:

```
Install the addyosmani/agent-skills pack for my AI agent.

Run: npx skills add addyosmani/agent-skills

If the open skills CLI (vercel-labs/skills) isn't installed, install
it first. Guide me step by step and verify at the end.

After installation, confirm you can read the skills and list the
skills we'll use for: spec-driven-development, interview-me,
planning-and-task-breakdown, incremental-implementation,
code-review-and-quality, security-and-hardening.
```

**Chat drop:** Paste the install prompt above. When done, ask AI: `List the agent personas in the agent-skills pack and what each one does.`

---

## Part 3: Define — Turn Your Idea into a PRD

Now we run the **Define** stage. The `interview-me` skill will interrogate you — one question at a time — until it understands what you actually want.

In Zed's AI panel, working in the project folder you created in Lesson 2 (`~/projects/my-hackathon-app` — the one with RESEARCH.md in it):

```
Use the interview-me skill from the agent-skills pack.

I'm a beginner Product Owner. Interview me ONE question at a time
about my hackathon project idea. Wait for each answer before the
next question. Keep questions simple — no jargon.

My rough idea: [YOUR IDEA — e.g. "an app where friends bet on
who can walk the most steps this week, with crypto stakes"]

Context about my goals:
- Target: Colosseum fall hackathon (Sep 28 - Nov 2, 2026)
- Also aiming for Solana Mobile grants → mobile-first Android
- I build with AI assistance, no manual coding
- Demo must run on Solana devnet

Interview me until you're ~95% confident you understand:
- who the user is, the core problem, and the moment of "aha"
- the 3 must-have features vs nice-to-haves
- how Solana is actually used (not bolted on)
- what we can realistically demo in ~4 weeks
```

Then, when the interview is done:

```
Now use the spec-driven-development skill to write the PRD
(SPECIFICATION.md) for my project.

Cover: objective, target user, core user flows, features (must-have /
later), the Solana integration (exactly which on-chain actions),
data model, tech stack suggestion (keep it simple: React Native +
Expo frontend, SupaBase for data, Solana devnet), security
boundaries (never log seed phrases; keys only via Mobile Wallet
Adapter), and success criteria for the hackathon demo.

Keep it under 150 lines. Save to SPECIFICATION.md in the project root.
```

**Chat drop:** Paste the interview prompt → answer honestly → paste the PRD prompt → read SPECIFICATION.md. This is your product, in writing, for the first time. Fix anything with: `In SPECIFICATION.md change [X] to [Y].`

---

## Part 4: Plan — Break It into Phases and Tasks

Now the **Plan** stage. In Zed's AI panel:

```
Use the planning-and-task-breakdown skill from the agent-skills pack.

Read SPECIFICATION.md. Break the project into exactly these seven
phases — do not invent your own numbering, the whole course
depends on these:

- Phase 1 — Project skeleton (Lesson 3, today): repo structure,
  README, .gitignore, .env.example, a runnable placeholder,
  docs folder
- Phase 2 — Data layer (Lesson 5): SupaBase schema, row-level
  security, a data-access module, one working read/write
- Phase 3 — Mobile app + Solana Mobile Stack (Lesson 6): Expo
  app, Mobile Wallet Adapter connect, sign a devnet transaction
- Phase 4 — Core product features (Product Build Track): the
  must-have features from SPECIFICATION.md, built as homework
  after Lessons 3-6 and in the Lesson 7 build sprint
- Phase 5 — Packaging & deployment (Lesson 7): APK via EAS,
  backend or landing page
- Phase 6 — Hackathon submission (Lesson 8): README for judges,
  videos, validation, submission checklist
- Phase 7 — Grant application & defense (Lesson 9)

For each phase: small atomic tasks with acceptance criteria
("done when…"), ordered by dependency. Note the lesson number
next to each phase heading.

Phase 4 is where MY product lives — give it the most detail, and
order its tasks so that the single most demo-able feature comes
first.

Save to PLAN.md. Keep it under 200 lines.
```

**The seven phases, at a glance:**

| Phase | What | Where it happens |
|---|---|---|
| 1 | Project skeleton | Lesson 3 — today, in class |
| 2 | Data layer (SupaBase) | Lesson 5 |
| 3 | Mobile app + Solana Mobile Stack | Lesson 6 |
| 4 | **Core product features** ⭐ | **Product Build Track** — homework + Lesson 7 sprint |
| 5 | Packaging & deployment (APK) | Lesson 7 |
| 6 | Hackathon submission | Lesson 8 |
| 7 | Grant application & defense | Lesson 9 |

Lesson 4 (Solana fundamentals) doesn't own a phase — it's where you learn what the blockchain can do and decide the **on-chain core** of Phase 3.

**Chat drop:** Paste the plan prompt. Read PLAN.md. Tell your neighbor what your first Phase 4 task is — that's the feature your whole pitch will be about.

---

## Part 5: TEAM.md — Your Standing Team

The personas are your team. We write it down once, and every future lesson reuses it. In Zed's AI panel:

```
Create TEAM.md in my project root. It defines my AI development team
for this project.

Team roles (from the addyosmani/agent-skills pack personas):

1. Team Lead — orchestrates, follows PLAN.md, delegates
2. code-reviewer — reviews every change before commit:
   would a staff engineer approve this?
3. security-auditor — checks: no secrets in code, no seed phrase
   handling, safe .env usage, least privilege
4. test-engineer — verifies each task against its acceptance criteria

Team rules:
- Work one task at a time from PLAN.md
- Commit after every completed task (atomic commits)
- Update PLAN.md as tasks complete
- Never commit .env or any real secret
- Never push to GitHub without my explicit request
- Report in 3 lines: what was done, what changed, what's next
- If blocked: diagnose, try one fix, then ask me

Keep it under 80 lines. Save to TEAM.md.
```

**Chat drop:** Paste the TEAM.md prompt. Read it. This file is now required reading for AI in every future lesson.

---

## Part 6: Build — Execute Phase 1

The exciting part — your team starts building. In Zed's AI panel:

```
Read TEAM.md, SPECIFICATION.md, and PLAN.md.

You are the Team Lead. Execute Phase 1 from PLAN.md.

Use the incremental-implementation skill: thin vertical slices,
one task at a time. After each task:
1. Test it works
2. Commit atomically with a clear message
3. Mark the task done in PLAN.md

When Phase 1 is complete, run the code-review-and-quality skill
on everything you wrote, then the security-and-hardening skill.
Fix anything important they find.

End with a 5-line report.
```

If progress stalls:

```
Show me current progress: which Phase 1 tasks are done, which are
in progress, what's blocked. Diagnose and fix any issues.
```

**Chat drop:** Paste the build prompt → watch the team work → paste the progress prompt if anything stalls.

---

## Part 7: Verify & Review — Prove It Works

The pack's philosophy: **"tests are proof"** and **"verification is non-negotiable."** In Zed's AI panel:

```
Use the test-engineer persona approach: verify all Phase 1 tasks
against their acceptance criteria from PLAN.md.

1. Does the app run?
2. Do the files match the SPECIFICATION.md structure?
3. Any bugs or broken pieces?

Then run one final review pass with the code-reviewer persona.
Report: what passed, what failed, what you fixed.
```

**Chat drop:** Paste the verification prompt. If anything fails — let AI fix it, then re-verify.

---

## Part 8: Ship — Push to GitHub

In Zed's AI panel:

```
Use the git-workflow-and-versioning skill.

Check my repo state, then push everything to GitHub:
- Create the repository if it doesn't exist
- Verify .gitignore excludes .env and any keys
- Verify no secrets are in the committed files
- Clean commit history with clear messages
- Give me the repository link
```

**Chat drop:** Paste the ship prompt. Open your repo on GitHub — your hackathon project now exists in public. (That's intentional: open source is a grant criterion and judges read repos.)

---

## Homework

1. Re-read your SPECIFICATION.md — sleep on it, then make 1 change tomorrow if needed
2. **Product Build Track starts now.** Look at your Phase 4 tasks. Mark the single most demo-able one with a ⭐ — that's your pitch in Lesson 8. Then let the team start on it:
   `Read TEAM.md, SPECIFICATION.md and PLAN.md. Start Phase 4. Work only on tasks that don't need the database or the mobile app yet — plain logic, data shapes, sample content. One task at a time, test it, commit it, mark it done in PLAN.md.`
3. Aim for **2-3 finished Phase 4 tasks before Lesson 5.** Lesson 5 opens with a checkpoint on exactly this
4. Push all changes to GitHub
5. In the group chat: one line about your product — "I'm building [X] for [Y], because [Z]"

---

## Troubleshooting

### `npx skills add addyosmani/agent-skills` Fails

```
The command failed with: [paste error].
Check whether the open skills CLI is installed (vercel-labs/skills),
install it if needed, then retry. If it still fails, clone
https://github.com/addyosmani/agent-skills.git and tell me where
to place the skills so my AI agent reads them.
```

### The Interview Feels Too Slow

```
The interview is taking too long. Skip ahead: propose your best
understanding of my product in 10 bullet points, and I'll correct
anything wrong.
```

### AI Builds Without Committing

```
You built several things without committing between tasks.
Re-read TEAM.md. Commit each task separately with clear messages,
then continue.
```

### Plan Is Too Big / Too Vague

```
Phase [N] tasks are too vague. Re-run planning-and-task-breakdown
on that phase: smaller tasks, each with a "done when…" criterion.
```

### I Want to Change My Idea

It's the cheapest moment to change it. Tell AI: `My idea changed. Here's what's different: [describe]. Update SPECIFICATION.md and PLAN.md accordingly, keeping what still applies.`

---

## Related Materials

- [lesson-02](lesson-02.md) — Previous lesson: research & strategy
- [lesson-04](lesson-04.md) — Next lesson: Solana fundamentals
- *lesson-03-architecture-specification-plan* — Online English Lesson 3 (source)
- *lesson-04-ai-agents-team* — Online English Lesson 4 (source, superseded by agent-skills)
- *near-offline-lesson-02* — NEAR course equivalent (Product Owner method)

## Result

After this lesson, each student has:
- The addyosmani/agent-skills pack installed (24 workflows + 4 personas)
- A hackathon product idea refined through a structured interview
- SPECIFICATION.md — the PRD (what we're building and why)
- PLAN.md — the seven course phases with atomic tasks and acceptance criteria, and a ⭐ on the feature that will carry the pitch
- TEAM.md — their standing AI team with roles and rules
- Phase 1 built, tested, reviewed, and pushed to GitHub
- Working knowledge of the full workflow: spec → plan → build → test → review → ship
- A started Product Build Track — the habit that decides whether there's a product to submit
