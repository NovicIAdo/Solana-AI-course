---
title: "Solana Off-line Lesson 2: Tokens, Context, All MCP Servers & Ecosystem Research"
type: lesson
difficulty: beginner
tags: [solana, offline, tokens, context, research, colosseum, grants, solana-mobile, mcp, skills]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 2
---

# Solana Off-line Lesson 2: Tokens, Context, All MCP Servers & Ecosystem Research

**Format:** Instructor-led classroom — screen sharing + hands-on practice
**Duration:** ~2.5 hours

## How This Lesson Works

Same flow: instructor explains → demonstrates → drops prompt in chat → students copy-paste and repeat → wait for all → questions → next section.

**Big idea of this lesson:** from now on your AI has *superpowers*. We plug in **all the MCP servers we'll ever need, today** — so in every future lesson AI just uses tools that already work, instead of you doing things by hand.

---

## Prerequisites

From Lesson 1, every student must have:
1. ✅ Zed with DeepSeek connected
2. ✅ Git and GitHub CLI working
3. ✅ Phantom wallet on devnet with some devnet SOL
4. ✅ Colosseum builder account
5. ✅ AGENTS.md in the Projects folder

---

## Part 1: Tokens — The Currency of AI (Quick Version)

A short refresher from Lesson 1, with one addition:

| Concept | Meaning |
|---------|---------|
| **Token** | A piece of text AI reads/writes (~0.75 of an English word) |
| **Context window** | How many tokens AI can "remember" in one conversation |
| **Cost** | You pay per token — pennies, but it adds up |

**The three habits that keep AI cheap and sharp:**
1. Don't re-paste files AI already read — reference them by name
2. Ask AI to summarize long outputs
3. Start a fresh conversation when switching tasks

**Chat drop:** Ask AI: `How many tokens did our last conversation use? Estimate the cost with DeepSeek pricing and explain how you calculated it.`

---

## Part 2: Skills and MCP — How AI Gains Superpowers

Two mechanisms we'll use all course long:

| Mechanism | What It Does | Example |
|-----------|--------------|---------|
| **Skill** | A `SKILL.md` file with instructions AI reads and follows | "context-optimization" from Lesson 1 |
| **MCP server** | A live plug that gives AI real tools (read data, act on your behalf) | Supabase MCP → AI creates tables itself |

**The rule for this course: use tools that already exist — don't build what's already built.** Every MCP server we install today replaces hours of manual work in future lessons:

| MCP server | What AI will be able to do with it |
|------------|-----------------------------------|
| **GitHub MCP** | Create repos, read code, manage issues — AI handles GitHub for you |
| **Supabase MCP** | Create tables, run SQL, check data — AI is your database admin (used in Lesson 5) |
| **Solana MCP** | Check balances, send SOL, create tokens on devnet — AI moves money for you (used in Lesson 4) |
| **Playwright MCP** | Open websites, read pages, click around — AI browses the web with eyes (used TODAY for research) |

**Chat drop:** Ask AI: `Explain the difference between a skill and an MCP server in 3 sentences, with one example of each.`

---

## Part 3: Create Your Project Folder and Your Supabase Project

Two five-minute chores before the big setup — both of them are things every later lesson assumes exist.

### 3a. One folder for the whole course

Everything from today until Lesson 9 lives in **one folder**: research, spec, plan, the app, the pitch. Create it now:

```
Create a folder ~/projects/my-hackathon-app (Windows:
C:\Projects\my-hackathon-app), initialise a git repository in it,
and open it as my project in Zed. Add a .gitignore that already
excludes .env and node_modules.
```

You can rename the folder later when your product has a name. What matters is that there is exactly one of them.

### 3b. Create a Supabase project (we use it in Lesson 5)

The Supabase MCP needs an *account*; your app in Lesson 5 needs a *project*. Create both now, by hand, in the browser — it takes four minutes and saves a broken Lesson 5:

1. Go to [supabase.com](https://supabase.com) → **Sign up** (GitHub login is easiest)
2. **New project** → name it after your course project → pick the region closest to you
3. **Set a database password** and save it with your other passwords — Supabase shows it once
4. Wait ~2 minutes while the project provisions (green "Active" status)
5. Leave the tab open — we come back to it in Lesson 5

**Chat drop:** `Supabase: https://supabase.com` → Sign up → New project → name + region + database password (SAVE IT) → wait for "Active".

---

## Part 4: Connect ALL the MCP Servers — One Big Setup

We install every MCP server the course needs, now, in one pass. (Later lessons still install *project* tools — Expo, the EAS CLI, flyctl — but this is the last time we touch the AI's own plumbing.)

**Where do MCP servers live?** In Zed's `settings.json`. Press **`Cmd/Ctrl+,`** in Zed to open it — that works on every OS and every Zed version. (For reference: it's `~/.config/zed/settings.json` on Mac/Linux and `%APPDATA%\Zed\settings.json` on Windows. Older guides say `~/.zed/settings.json`; that path is out of date.)

Paste this prompt in Zed's AI panel:

```
I want to connect four MCP servers to Zed, all at once.

Add them under the "context_servers" key in Zed's settings.json.
Tell me to open it with Cmd/Ctrl+, — do not guess the file path,
and tell me exactly where to paste each block.

My OS: [Windows / Mac / Linux]

Use the current official packages. Before configuring each one,
check its README for the environment variables it ACTUALLY
requires today, and tell me if it needs anything I haven't
mentioned:

1. GitHub MCP — the official GitHub MCP server. I'll need a
   GitHub personal access token: guide me to create it
   (github.com → Settings → Developer settings → Personal access
   tokens, minimal scopes for repos). Give me the config with
   YOUR_TOKEN_HERE as a placeholder — I'll type the real token
   into the file myself.

2. Supabase MCP — @supabase/mcp-server-supabase
   I already have a Supabase account and project. Guide me to
   create an access token (supabase.com → Account → Access
   Tokens, name "zed-mcp"). Placeholder again — I type it in.
   IMPORTANT: do NOT pass the --read-only flag. It defaults to
   off, which is what we want — in Lesson 5 this server has to
   create tables and apply migrations. If you see --read-only
   anywhere in the config, remove it and tell me.

3. Solana MCP — the "solana-mcp" package (by sendaifun, powered
   by Solana Agent Kit). It needs only RPC_URL and
   SOLANA_PRIVATE_KEY; its OPENAI_API_KEY variable is optional,
   so skip it. Configure it for DEVNET:
   RPC_URL=https://api.devnet.solana.com
   SOLANA_PRIVATE_KEY — generate a FRESH devnet keypair for me
   (do NOT use my Phantom key!), show me the public address, and
   show me where to paste the private key myself.
   Then fund the new address and verify the balance.

4. Playwright MCP — @playwright/mcp (browser automation).
   No keys needed.

Do them one at a time. After each: verify the connection works
(list its tools, restart Zed's MCP if needed).

Security rules: tokens and private keys go into Zed's settings
file, typed by me — never into this chat, never into project
files, never onto GitHub.
```

> 🔑 **Why the placeholders again?** Everything you type in the AI panel travels to DeepSeek's servers. AI writes the config *around* the secret; you paste the secret in yourself. It costs 10 extra seconds per server.

**For the instructor — what students will experience:**
1. AI creates the GitHub token steps → student pastes token → done
2. Supabase: sign-up if needed → token → done
3. Solana: AI generates a devnet keypair, configures it, funds it — **no manual work at all**
4. Playwright: installs and connects

**Chat drop:** Paste the big prompt above. Work through each server with AI. Finish line: ask AI `List all your MCP tools now.` — you should see GitHub, Supabase, Solana, and Playwright tools.

### If a server won't connect — the fallback table

Don't let a stubborn MCP server eat the lesson. Every one of them has a manual path, and the course still works:

| Server | Used in | If it won't connect |
|--------|---------|---------------------|
| **Playwright** | Today | Use plain web search instead — tell AI `Use web search, not the browser` |
| **Solana** | Lesson 4 | Lesson 4 has a full **Solana CLI fallback** — same operations, one extra install |
| **Supabase** | Lesson 5 | Use the Supabase dashboard: AI writes the SQL, you paste it into the SQL Editor |
| **GitHub** | Lessons 2-9 | You already have `gh` from Lesson 1 — AI uses it exactly the same way |

Mark on paper which of the four connected. Bring that note to the next lesson — the instructor plans around it.

---

## Part 5: Research Target #1 — How the Colosseum Hackathon Works

Now we research — but this time **AI uses the Playwright MCP to browse the sites itself**, instead of you copying pages. In Zed:

```
Use the Playwright MCP (browser tools) to research the Colosseum
hackathon. I'm a beginner preparing for the fall hackathon
(Sep 28 - Nov 2, 2026).

Open and read:
- https://colosseum.com (main page + hackathon page + eternal page)
- https://blog.colosseum.com/how-to-win-a-colosseum-hackathon/
- https://blog.colosseum.com/perfecting-your-hackathon-submission/
- https://blog.colosseum.com/the-volta-prize-colosseum-and-hackathons-in-the-age-of-ai/

If a page won't load in the browser, use web search instead.

Explain in simple language:
1. How the hackathon works (length, format, what I submit)
2. What judges look for — the winning criteria
3. Pitch video and tech demo rules (exact lengths)
4. What the accelerator is and what winners get
5. What Colosseum says about AI-era founders — can 1-2 people
   with AI tools compete?
6. When am I allowed to start building?

Save to RESEARCH.md in my project folder
(~/projects/my-hackathon-app), section "Colosseum Hackathon".
```

**Key facts to check against what AI found (instructor reads aloud after AI finishes):**

> ⚠️ **These are the numbers as we wrote this course (August 2026). Hackathon rules change every season.** Whatever AI reads off the live site today wins over this table. If AI's answer differs, correct the table on screen — and note it in RESEARCH.md. Treating a stale number as fact is exactly the mistake this lesson teaches you to avoid.

| Fact (as of Aug 2026) | Why it matters for us |
|------|----------------------|
| Hackathon: Sep 28 — Nov 2, online, ~5 weeks | We finish this course 2-3 weeks before it starts |
| Dozens of prizes; a large cash prize for the Grand Champion; select winners enter Colosseum's accelerator with pre-seed funding | Real money, real startup path — check the current amounts on the site |
| You may start building before the official start | This whole course is our head start — **verify the exact window, it decides whether our head start is legal** |
| Pitch video ≤ 3 min, tech demo 2-3 min | We'll practice exactly this in Lesson 8 |
| Most winning teams are small — commonly 2-4 people, tech + non-tech mix. Solo entries are allowed but have to justify themselves | Your classmate is a potential co-founder |
| Colosseum's own framing: AI tools let very small teams compete with big ones | You are the audience they're betting on |

**Chat drop:** Paste the research prompt above. Read the Colosseum section of RESEARCH.md. Discuss: which fact surprised you most?

---

## Part 6: Research Target #2 — Solana Mobile Grants

In Zed:

```
Use the Playwright MCP (or web search) to research the Solana
Mobile Builder Grants program.

Open and read:
- https://solanamobile.com/grants

Explain in simple language:
1. What the grants fund (who is it for)
2. ALL the official evaluation criteria
3. What "Solana Mobile Stack" means (Mobile Wallet Adapter,
   Seed Vault, dApp Store) — one sentence each
4. How milestones-based grants work
5. How the grants relate to Colosseum hackathons
6. How and when to apply

Save to RESEARCH.md, section "Solana Mobile Grants".
```

**Key facts to check against what AI found:**

> ⚠️ Same rule as above: the live page at solanamobile.com/grants beats this table. Criteria names and grant sizes change between seasons.

| Criterion (official, as of Aug 2026) | What it means for us |
|----------------------|----------------------|
| Mobile-First Implementation | Our app must be Android-first |
| Solana Mobile Stack Use (MWA + Seed Vault) | Lesson 6 is dedicated to exactly this |
| Scope & Milestone Timeline | We learn this in Lesson 3 (PLAN.md) and Lesson 9 |
| Team Ability to Execute | Your GitHub and shipped demo ARE the evidence |
| Clear Use of Funds | Lesson 9 — AI writes the budget |
| Community & Open Source | Public repo, MIT license — free points |

**Chat drop:** Paste the prompt. Read the grants section. Discuss: what's the difference between winning a hackathon prize and receiving a grant?

---

## Part 7: Research Target #3 — The Solana Developer Ecosystem

In Zed:

```
Use the Playwright MCP (or web search) to research the Solana
developer ecosystem for a beginner who builds with AI assistance.

Open and read:
- https://solana.com/docs (intro sections)
- https://phantom.app and its developer docs (what Phantom is)

Explain in simple language, one paragraph each:
1. What Solana is (blockchain basics for a beginner)
2. Phantom wallet, devnet vs mainnet
3. How apps connect to Solana (web3.js — is it now called
   "Kit"?) and what RPC means
4. What SPL tokens are
5. The Solana Mobile Stack: Mobile Wallet Adapter, Seed Vault,
   dApp Store
6. What the Solana MCP we installed can do (read its tool list)
7. Free learning resources (Solana docs, Cyfrin Updraft course)

Save to RESEARCH.md, section "Solana Ecosystem".
```

**Chat drop:** Paste the prompt. Read the ecosystem section. Mark the three tools you expect to use in your project.

---

## Part 8: Install the Colosseum Copilot Skill

Colosseum publishes a **skill for AI agents** that encodes 8,000+ past hackathon submissions and judging patterns. In Zed:

```
Install the Colosseum skill for AI agents.

Run: npx skills add ColosseumOrg/colosseum-resources

If the open skills CLI isn't installed, install it first
(vercel-labs/skills). Guide me step by step and verify the
installation. Explain what this skill gives me.
```

**Chat drop:** Paste the prompt above. After install, ask AI: `Using the Colosseum skill if available: what do past winning hackathon projects have in common?`

---

## Part 9: Your RESEARCH.md — The Course Compass

In Zed:

```
Read RESEARCH.md. Polish it:

1. Add a one-paragraph "Executive Summary" at the top:
   what we're doing, the two targets (Colosseum hackathon
   Sep 28 - Nov 2, 2026 + Solana Mobile grants), and why
   mobile-first is our strategy
2. Add a "Strategy" section:
   - How a team of 1-2 non-coders with AI can compete
   - What we must have by Sep 28 (based on judging criteria)
   - Top 5 risks and how we mitigate them
3. Add a "My Toolkit" section: the MCP servers we connected
   today and what each one does for me
4. Keep it under 200 lines total
```

Then push to GitHub — using the GitHub MCP:

```
Using the GitHub MCP, create a repository for the project folder
we made in Part 3a (~/projects/my-hackathon-app) and push
RESEARCH.md to it with a clean commit. Verify .env is gitignored
before pushing.
```

> 📁 **One folder, one repo, all course long.** RESEARCH.md lives *inside your product repo* — not in a separate research repo. Lesson 3 writes SPECIFICATION.md next to it, Lesson 9 reads both when it writes your grant application. Splitting them is the single easiest way to lose your own work.

**Chat drop:** Paste both prompts. Open your final RESEARCH.md — this document guides every lesson from here.

---

## Homework

1. Read the three Colosseum blog posts yourself (links are in RESEARCH.md) — 20 minutes
2. Ask AI (via Solana MCP) to check the devnet balance of the keypair it created — confirm it has SOL
3. Find 2 projects that won past Colosseum hackathons — write their names + one-line description in the group chat
4. Ask AI: what would be a good hackathon project for YOUR interests? Let it ask you questions first. Just collect ideas — no building yet
5. Push RESEARCH.md to GitHub if you haven't

---

## Troubleshooting

### GitHub MCP Won't Connect

```
The GitHub MCP server fails with: [paste error].
Check my token has the right scopes and that the context_servers
entry is correct. Guide me to regenerate the token if needed.
```

### Supabase MCP Won't Connect

```
The Supabase MCP fails with: [paste error]. Check the token
(sbp_...), the package name, and the Zed settings entry. Fix it.
```

### Solana MCP Says "Invalid Private Key"

```
The Solana MCP says the private key is invalid. Generate a fresh
devnet keypair, set it in the MCP env config, fund it via the
devnet faucet, and verify with the BALANCE tool.
```

### Playwright Browser Won't Start

```
Playwright MCP can't launch a browser: [paste error]. Install the
required browser (npx playwright install chromium) or use web
search as a fallback for research.
```

### A Page Won't Load in the Research Browser

Tell AI: `The page [URL] didn't load in the browser. Use web search instead and cite sources.` (Colosseum's site is JavaScript-heavy — this is expected.)

### AI Hallucinates Criteria

```
Show me the exact source for each claim in the "Colosseum
Hackathon" section of RESEARCH.md. If a claim has no source,
mark it UNVERIFIED or remove it.
```

---

## Related Materials

- [lesson-01](lesson-01.md) — Previous lesson: setup
- [lesson-03](lesson-03.md) — Next lesson: Product Owner + AI Team (agent-skills)
- *lesson-02-free-tokens-optimization* — Online English Lesson 2 (source material)
- *near-offline-lesson-02* — NEAR course research lesson (same method)

## Result

After this lesson, each student has:
- Deep understanding of tokens, context, and keeping AI cheap and sharp
- One project folder + git repo that every remaining lesson builds on
- A Supabase account **and a provisioned project** (Lesson 5 needs the project, not just the account)
- **Four MCP servers connected to Zed**: GitHub, Supabase (write mode — the default), Solana (devnet, funded keypair), Playwright — plus a written note of which ones failed and their fallbacks
- RESEARCH.md with three researched sections (Colosseum, grants, ecosystem) + executive summary, strategy, and toolkit inventory
- The Colosseum Copilot skill installed
- A clear picture of what winning requires (from Colosseum's own guides)
- The six official Solana Mobile grant criteria understood
- Their own project idea starting to form
- Everything pushed to GitHub — via the GitHub MCP, into the one repo the whole course uses
