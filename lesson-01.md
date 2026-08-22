---
title: "Solana Off-line Lesson 1: Setup — GitHub, Zed, DeepSeek, Phantom & Devnet"
type: lesson
difficulty: beginner
tags: [solana, offline, github, zed, deepseek, api, homebrew, context, agents-md, phantom, devnet, faucet, colosseum]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 1
---

# Solana Off-line Lesson 1: Setup — GitHub, Zed, DeepSeek, Phantom & Devnet

**Format:** Instructor-led classroom — screen sharing + hands-on practice
**Duration:** ~3 hours — the heaviest setup day of the course; everything gets installed today

## How This Lesson Works

The instructor stands at a desk with a laptop connected to a big screen. Students sit at their desks with their own laptops.

**Flow for each section:**
1. Instructor explains what we're about to do and why
2. Instructor does it on screen — students watch
3. Instructor drops the prompt/link in the common chat
4. Students copy from chat, paste, and repeat on their own machines
5. We wait until everyone succeeds
6. Instructor answers questions if any
7. Move to the next section

**Common chat:** All prompts, links, and guides are dropped there. Students copy-paste — no typing from memory.

**Course rhythm:** 3 lessons per week, ~3 weeks total (~23 hours of class time). Lesson 9 finishes 2-3 weeks before the Colosseum fall hackathon starts (September 28, 2026) — your head start.

**Where the product actually gets built:** class time teaches the tools; your product grows on the *Product Build Track* — homework between lessons, with a supervised build sprint in Lesson 7. Budget 3-5 hours per week outside class.

---

## Prerequisites

Before the lesson, every student should have:

1. **A computer** (Windows / Mac / Linux)
2. **A GitHub account** — [github.com](https://github.com) (free, sign up beforehand)
3. **A Gmail account** — needed for registrations
4. **A bank card with ~$15 available** — see the cost table below
5. **A Telegram account** — for the class chat and later user validation
6. **An Android phone** — we'll install our own app on it in Lessons 6-7
7. **Access to the common chat** (Telegram / WhatsApp / Discord)

### What the course costs

| What | When | Cost |
|------|------|------|
| DeepSeek API | Lesson 1 | **$5 — that covers the whole course.** DeepSeek charges about $0.22 per million input tokens and $0.66 per million output at off-peak rates, and off-peak is most of the day (peak is only 01:00-04:00 and 06:00-10:00 UTC). Verified against real usage |
| GitHub, Supabase, Expo, Vercel, Phantom, Colosseum | Lessons 1-8 | **Free** on their free tiers |
| EAS Build (Expo cloud builds) | Lessons 6-7 | **Free tier**: limited builds per month, queued behind paid users. Enough for this course if you don't rebuild constantly |
| fly.io (only if your product needs a backend) | Lesson 7 | **Not free** — usage-based, budget a few dollars a month. Most products in this course don't need it |
| Solana devnet | Lessons 4-9 | **Free** — devnet SOL is fake money |

**Total for a typical student: about $5**, plus a few dollars only if your product genuinely needs a fly.io backend. Nobody needs real SOL at any point.

### A note for Windows students

The course works on Windows, but most commands in the lessons are written for macOS. Two things differ everywhere:

| | macOS / Linux | Windows |
|---|---|---|
| Terminal | Terminal app | **PowerShell, run as Administrator** |
| Zed settings file | `~/.config/zed/settings.json` | `%APPDATA%\Zed\settings.json` |

Easiest fix: never type these paths. In Zed press **`Cmd/Ctrl+,`** — it opens the right settings file for your OS. And whenever you paste a prompt into the AI panel, add the line `My OS: Windows` — AI will translate the commands for you.

---

## Part 1: Understanding Where Code Lives

**Three places your code can be:**

| Where | What It Is | Example |
|-------|-----------|---------|
| **Locally** | A folder on your computer | `C:\Projects\my-app` (Windows) or `~/projects/my-app` (Mac/Linux) |
| **GitHub (remote)** | Cloud code storage | `github.com/yourname/my-app` |
| **Synced** | Both places — via Git | Most common: you work locally, save to GitHub |

```
Your computer ←——— Git ———→ GitHub (cloud)
```

**Why GitHub matters for the hackathon:** Colosseum judges explicitly look at your GitHub repository — commit history, README, code quality. Your repo is part of your submission. We start building good habits today.

**Chat drop:** `GitHub: https://github.com` — register if you haven't yet. Free account is all you need.

---

## Part 2: The Tool We're Installing — Zed

Today we install **Zed** — your AI-powered code editor. It's where you'll do all your work.

**What Zed is:** A code editor with an AI assistant built right inside. You open a project, see your files, and the AI panel lives next to your code. You describe what you want — AI writes and changes code for you. Like Google Docs, but for programming — with an AI copilot that never leaves your side.

**How you interact:** Press `Ctrl+Shift+A` (Mac: `Cmd+Shift+A`) — the AI panel opens. Type what you need, AI responds and edits files directly in the editor.

**Zed connects to the DeepSeek API** — that's the "brain" powering the AI. We'll set that up next.

---

## Part 3: Install Zed

1. Open browser → go to [zed.dev/download](https://zed.dev/download)
2. Download the right version for your OS
3. Install like any normal program

**Chat drop:** `Zed download: https://zed.dev/download` — install and open it once.

---

## Part 4: Get a DeepSeek API Key

**What is an API key?** It's a password that lets Zed connect to DeepSeek's AI brain. Without a key, Zed is just a text editor. With a key — it's an editor with an AI assistant built in.

**Cost: top up $5 and you're done for the whole course.** DeepSeek is astonishingly cheap: roughly $0.22 per million tokens in and $0.66 per million out at off-peak rates — and off-peak covers most of the day (peak is only 01:00-04:00 and 06:00-10:00 UTC). Even the heavy lessons where AI writes a whole mobile app cost cents. Check the Billing page after the first lesson anyway, so you see it with your own eyes.

1. Open browser → go to [platform.deepseek.com](https://platform.deepseek.com)
2. Sign up (can use Google account)
3. Go to **Billing** → Top up with $5
4. Go to **API Keys** → Create new key → name it `zed`
5. Copy the key — it looks like: `sk-a1b2c3d4e5f6...`

**IMPORTANT:** Save the key somewhere safe. Never share it. It gives access to AI on your behalf.

**Chat drop:**
- `DeepSeek platform: https://platform.deepseek.com`
- Sign up (Google) → Top up $5 → API Keys → Create key named "zed" → Copy it
- SAVE THE KEY. Do not share.

---

## Part 5: Connect DeepSeek to Zed

1. Open Zed
2. Open the AI panel: **`Ctrl+Shift+A`** (Mac: **`Cmd+Shift+A`**)
3. At the bottom of the AI panel, click the model name
4. Select "Configure" or "Add Provider"
5. Zed will ask for an API key — paste your DeepSeek key

**Always prefer this UI path.** Your key goes straight into Zed's own storage and is never sent to anyone.

**If Zed doesn't offer DeepSeek directly** — open the settings file yourself: press **`Cmd/Ctrl+,`** in Zed (this opens `~/.config/zed/settings.json` on Mac/Linux, `%APPDATA%\Zed\settings.json` on Windows) and ask AI for the exact block to paste:

```
Show me the JSON block that adds DeepSeek as a language model
provider in Zed's settings.json. Use a placeholder like
"YOUR_KEY_HERE" instead of a real key — I'll paste my key in
myself. Explain where in the file it goes.
```

Then replace `YOUR_KEY_HERE` with your key by hand and save.

> ⚠️ **Why the placeholder?** Anything you type into the AI panel is sent to DeepSeek's servers. Keys, tokens and seed phrases should go into settings files and `.env` files **by your own hands**, never through the chat. We repeat this rule in every lesson — it is the one habit that separates a safe builder from a hacked one.

After this, DeepSeek will appear as a model option in Zed.

**Chat drop:** In Zed AI panel (`Ctrl+Shift+A` / `Cmd+Shift+A`) → click model name → Add Provider → paste your DeepSeek key. If DeepSeek doesn't appear, press `Cmd/Ctrl+,` and paste the prompt above — then type the key yourself.

---

## Part 6: Homebrew for macOS + Install Git

Before we install anything, macOS users need **Homebrew** — a package manager. Without it, AI has a very hard time installing programs on Mac. Think of Homebrew as an "App Store for the terminal" — it lets AI install tools with simple commands.

Windows users can skip this — they'll use PowerShell as Administrator instead.

### macOS: Install Homebrew

**Instructor shows on screen:**

1. Open **Terminal** (Finder → Applications → Utilities → Terminal)
2. Go to [brew.sh](https://brew.sh) — copy the install command
3. Paste into terminal and run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

4. Follow the on-screen instructions — you'll need to enter your Mac password
5. After installation, the terminal will show "Next steps" — two lines to run:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

6. Verify: `brew --version` — should show a version number

**Chat drop (macOS only):**
- Open Terminal → copy install command from https://brew.sh → paste and run
- Enter your Mac password when asked
- Run the two "Next steps" lines shown at the end
- Verify: `brew --version`
- Windows users: skip this, use PowerShell as Administrator instead

### Now Install Git (all platforms)

**Create folder:**
- **Windows:** Open File Explorer → create `C:\Projects`
- **Mac/Linux:** Open Finder/Terminal → create `~/projects`

**Open it in Zed:** Zed → Open Project → select the `Projects` folder.

**Now ask AI to install Git.** In Zed's AI panel:

```
Install Git on my computer.

My OS: [Windows / Mac / Linux].

If macOS — use Homebrew: brew install git
If Git is already installed — check the version (git --version).
If not — give me the install command and explain what to press.

After installation, verify that Git works.
```

**Chat drop:**
- Create folder: Windows `C:\Projects`, Mac/Linux `~/projects`
- Open in Zed → Open Project → select the folder
- In Zed AI panel, paste the Git install prompt above
- ⚠️ Windows: Right-click PowerShell → Run as administrator first!

---

## Part 7: Install GitHub CLI

**GitHub CLI (`gh`)** is a tool that connects your computer to GitHub from the terminal. AI uses it to create repositories and push code for you.

Ask AI in Zed's AI panel:

```
Install GitHub CLI (gh) on my computer.

My OS: [Windows / Mac / Linux].

Install it. Verify it works: gh --version

Then help me authenticate with GitHub:
Run "gh auth login" and guide me through it step by step.
I'll choose: GitHub.com → HTTPS → authenticate via browser.

After that, verify: gh auth status
```

**Chat drop:** Paste the prompt above. When `gh auth login` asks — GitHub.com → HTTPS → browser. Confirm in browser. Then `gh auth status` should show your username.

---

## Part 8: First Project — Calculator

Now the fun part. We create a working calculator **without writing a single line of code**.

In Zed's AI panel (your `Projects` folder is open):

```
Create a simple calculator web app in a new folder called "calculator".

Use plain HTML, CSS, and JavaScript — no frameworks, no build tools.

Features:
- Buttons for digits 0-9 and operations + - * /
- A display showing the current input and result
- "C" button to clear
- "=" button to calculate
- Nice clean design

Create all files in the calculator folder. Explain what you created.
```

AI creates the files. Open `calculator/index.html` in the browser by double-clicking it. Test: 7 + 8 = 15. ✅

**Chat drop:** Paste the prompt above. Then double-click `index.html` in the calculator folder and try 7 + 8 = 15.

---

## Part 9: Push to GitHub

Let's save our calculator to the cloud. In Zed's AI panel:

```
Create a GitHub repository called "calculator" and push my calculator project to it.
Then give me the repository link.
```

**Chat drop:** Paste the prompt. Open the GitHub link AI gives you — your calculator is now on the internet.

---

## Part 10: What Are Tokens and Why Should You Care

A quick but important concept — **tokens** are the "currency" of AI:

| Concept | What It Means |
|---------|---------------|
| **Token** | A piece of text AI reads/writes (~0.75 of an English word) |
| **Context window** | How many tokens AI can "remember" in one conversation |
| **API cost** | You pay per token — more tokens = more money |
| **Context optimization** | Keeping the conversation short so AI stays focused and cheap |

**Why this matters for this course:** Every lesson you'll paste prompts into Zed. If you paste a whole 500-line file into the chat every time, AI gets slow, expensive, and forgetful. The skill in the next part fixes that.

---

## Part 11: Context Optimization Skill

We install a **skill** — a reusable set of instructions that makes AI work better. Skills are a theme of this course: in Lesson 2 we add Colosseum's own skill, and in Lesson 3 a full production skill pack.

**How skills work in practice:** a skill is a folder with a `SKILL.md` file. The `skills` CLI downloads it and registers it in your `AGENTS.md`, which Zed's agent reads automatically. So a skill is not a magic command — it's instructions your AI picks up. (You may see slash-command names like `/spec` in skill documentation. Those are shortcuts in some other AI tools; in Zed you get the same behaviour by naming the skill in your prompt: *"Use the spec-driven-development skill…"*. That's how every prompt in this course is written.)

Ask AI in Zed's AI panel:

```
Install a skill for my AI agent using the open skills CLI.

Run: npx skills add https://github.com/addyosmani/agent-skills/tree/main/skills/context-engineering

If npx isn't available, install Node.js first (macOS: brew install
node; Windows: download from nodejs.org).

Then:
1. Show me where the skill was installed
2. Show me the line it added to AGENTS.md
3. Read the SKILL.md and summarise its rules in 5 bullet points
4. Start following those rules from now on

If that exact skill isn't available, tell me so honestly, then
write the same rules into AGENTS.md yourself under a
"Context optimization" heading. Do not pretend it installed.

This skill is called "context-engineering" and it comes from the
same pack we use later in the course.
```

> The last paragraph matters. Skill catalogues change; an AI that can't find a package will sometimes *say* it installed one. We ask it to fail loudly instead — and we still get the rules.

**Chat drop:** Paste the prompt above. After installation, ask: `Explain what context optimization means and why it saves money.` Share the answer with your neighbor.

---

## Part 12: AGENTS.md — Rules for AI

Now we create **AGENTS.md** — a rules file. It's a note to every AI that works in your projects: "here's how to behave." Think of it as a job description you write once, and every AI agent reads automatically.

In Zed's AI panel:

```
Create an AGENTS.md file in my Projects folder.

It should contain rules for AI agents:

1. Language: always reply in English
2. Code style: simple, readable, with comments explaining non-obvious parts
3. Before making changes, explain what you're about to do in 1-2 sentences
4. Never push to GitHub without my explicit request
5. Never put secrets (API keys, tokens, private keys, seed phrases) in code or commits
6. After completing a task, summarize what was done and what to check
7. If something is unclear, ask me instead of guessing

Keep it short and clear.
```

Review the file, edit anything you want.

**Chat drop:** Paste the prompt above. Open AGENTS.md in Zed, read it, adjust to your taste.

---

## Part 13: Your Own Project

Time to repeat the full cycle on your own project. In Zed's AI panel:

```
I want to build my own small project. Ask me questions about what I want
to build (one question at a time). Based on my answers:
1. Create the project folder with all files
2. Test that it works
3. Create a GitHub repo and push it

Keep it simple — this is a warm-up project.
```

Ideas if you're stuck: a to-do list, a password generator, a unit converter, a quote-of-the-day page.

**Chat drop:** Paste the prompt. Answer AI's questions. Push to GitHub when AI suggests it.

---

## Part 14: Create Your Phantom Wallet — and Switch to Devnet

Now the Solana part. **Phantom** is the most popular Solana wallet — a browser extension (and phone app). It holds your keys and signs transactions.

**Three facts to understand right now:**

| Term | Meaning |
|------|---------|
| **Wallet** | Your identity on Solana. You send/receive SOL and tokens through it |
| **Seed phrase** | 12-24 words that are the ONLY way to recover your wallet. Write them on paper. Anyone with them controls your money |
| **Devnet** | Solana's free test network — fake SOL, zero risk, exactly where hackathon demos live |

**Create the wallet:**

1. Go to [phantom.app](https://phantom.app) → install the browser extension (Chrome/Brave/Firefox/Edge)
2. Create a new wallet → **write the seed phrase on paper** (never photograph it, never type it into a chat)
3. Set a password for the extension
4. Copy your **wallet address** — a long string of letters and digits

**Switch to devnet:**

1. Click the Phantom extension icon
2. Open **Settings** → **Developer Settings** → turn on **Testnet Mode**
3. The top of the wallet now shows a yellow "Devnet" badge

> 📱 **Keep that paper safe — you will need it in Lesson 6.** There we install Phantom on your Android phone and restore *this same wallet* from the seed phrase, so your app and your browser see the same devnet money. Restoring a wallet inside the official Phantom app is the one and only place that phrase may ever be typed.

**Chat drop:**
- `Phantom: https://phantom.app` → install → create wallet
- WRITE THE SEED PHRASE ON PAPER. Never share it, never photograph it, never type it in chat
- Settings → Developer Settings → Testnet Mode ON → yellow "Devnet" badge appears
- Keep the paper — Lesson 6 needs it for the phone app

---

## Part 15: Get Free Devnet SOL from the Faucet

Devnet SOL is free — you get it from a **faucet** (a tap of fake money).

1. Open [faucet.solana.com](https://faucet.solana.com)
2. Sign in if it asks (the official faucet usually wants a GitHub login to stop bots)
3. Paste your wallet address
4. Select **SOL**
5. Click **Confirm Airdrop** (or similar) — you typically get between 0.5 and 5 devnet SOL

**Faucets are the flakiest part of any Solana course.** They rate-limit, run dry, and change their rules. Expect it, and know the backups:

| If the faucet fails | Do this |
|---|---|
| "Rate limited" | Wait 15-30 minutes, or try again from a different network |
| Empty / errors | Try an alternative devnet faucet, or the airdrop button in the Solana Explorer's devnet view |
| Nothing works today | Ask a classmate who already has devnet SOL to send you some — it is fake money, sharing costs nothing. The instructor also keeps a funded devnet wallet for exactly this |

You need **at least 1 devnet SOL** to be comfortable for Lessons 4-7.

**See it on the blockchain:** open [explorer.solana.com](https://explorer.solana.com) (or [solscan.io](https://solscan.io)), switch to **Devnet**, paste your address — you'll see your account and the airdrop transaction. You are now on a real blockchain. 🎉

**Chat drop:**
- `Faucet: https://faucet.solana.com` → paste your address → SOL → Confirm
- `Explorer: https://explorer.solana.com` → Devnet → paste your address → find your airdrop transaction

---

## Part 16: Register Your Colosseum Builder Account

In Lesson 8 you'll submit your project to the **Colosseum hackathon**. Create the account today so it's ready.

1. Go to [colosseum.com](https://colosseum.com)
2. Click **Sign Up** — create your builder account (email or Google)
3. Explore the platform for 5 minutes: look at the hackathon page and the **Eternal** section

**What Colosseum is (30 seconds):** the world's largest online crypto hackathons, powered by Solana. The fall hackathon runs **September 28 — November 2, 2026**. ~40 prizes, and select winners join an accelerator with $250,000 pre-seed funding. We'll study it deeply in Lesson 2.

**Chat drop:** `Colosseum: https://colosseum.com` → Sign Up → look around for 5 minutes → find the hackathon dates.

---

## Homework

1. Make sure `gh auth status` works and your two projects are on GitHub
2. Ask AI to improve your own project from Part 13 (one new feature)
3. Check your wallet address on the devnet explorer — find your airdrop transaction
4. Re-read your AGENTS.md — would you add anything after today?
5. Share your wallet address in the group chat (it's public — safe to share; your seed phrase is NOT)

---

## Troubleshooting

### Zed Doesn't See DeepSeek

```
DeepSeek doesn't appear as a provider in Zed.
Check my settings and fix it. Explain what you're changing.
```

### Git Won't Install

```
Git installation failed. Here's the error: [paste error]
Diagnose and give me the exact next step for my OS: [Windows / Mac / Linux].
```

### Homebrew Won't Install (macOS)

```
Homebrew install failed. Here's the error: [paste error]
Diagnose and guide me through fixing it.
```

### Can't Push to GitHub

```
I can't push to GitHub. The error is: [paste error]
Check gh auth status, fix authentication if needed, then push.
```

### Accidentally Pushed Secrets to GitHub

If an API key ever lands on GitHub — revoke it immediately and tell AI:

```
I accidentally committed a secret to GitHub.
1. Tell me how to revoke the key
2. Remove the secret from git history
3. Make sure .gitignore and .env are set up so it never happens again
```

### Phantom Doesn't Show Devnet Mode

```
Phantom has no Testnet Mode in my settings. Find where devnet is
enabled in the current Phantom version and guide me step by step.
```

### Faucet Says "Rate Limited" or Is Empty

Wait a few minutes and try again, or ask AI: `The Solana faucet is rate-limited. What are the current alternative devnet faucets?`

---

## Related Materials

- [overview](overview.md) — Full course overview
- [lesson-02](lesson-02.md) — Next lesson: tokens, context & ecosystem research
- *off-line-lesson-01* — Original course Lesson 1 (same setup, general track)
- *lesson-01-github-ide-ai* — Online English Lesson 1 (source material)

## Result

After this lesson, each student has:
- Zed installed with DeepSeek connected
- Git and GitHub CLI working (`gh auth status`)
- Homebrew (macOS)
- First project — calculator — created by AI and pushed to GitHub
- A second project of their own on GitHub
- Context optimization skill installed
- AGENTS.md with rules for AI
- A Phantom wallet with seed phrase on paper, switched to devnet
- Free devnet SOL from the faucet, visible on the explorer
- A Colosseum builder account
- Understanding of tokens, context, and why secrets never go in code
