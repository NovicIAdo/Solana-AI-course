---
title: "Solana Course — What to Verify Before Teaching"
type: guide
difficulty: intermediate
tags: [solana, instructor, verification, checklist, preparation, maintenance]
created: 2026-08-19
updated: 2026-08-20
---

# What to Verify Before Teaching

Every claim in this course was true in **August 2026**. Hackathon rules, npm packages, free tiers and AI-tool behaviour all change without notice, and this course depends on roughly forty external things it does not control.

This file lists all of them. Work through it before each cohort. Write the date and the answer in the right-hand column — a checklist nobody dates is a checklist nobody trusts.

**Everything except A4 was verified on 2026-08-19** against live sources. Two errors in the course were found and fixed as a result (see C3 and E2). Read section A first: **A4 is the only thing still open**, it needs a phone, and the run-through that closes it is scripted directly underneath the table.

**Priority key:** 🔴 stops a lesson dead · 🟡 makes you look wrong in front of the room · 🟢 minor

Related: [instructor-checklist](instructor-checklist.md) · [README](README.md)

---

## A. Technical blockers — test on a clean machine

These are the four unknowns that can end a lesson. **Do not teach without testing them yourself.** Reading a README is not testing.

| # | What to test | Why it matters | Where it breaks | Checked (date / result) |
|---|---|---|---|---|
| A1 | 🟢 **Does DeepSeek reliably call MCP tools?** | The entire course is "AI uses tools for you" | Lessons 2, 4, 5 | **2026-08-19 ✅ 10/10.** Tested the function-calling API directly: correct tool, correct arguments, ten times out of ten. Current models are `deepseek-v4-flash` / `deepseek-v4-pro`; `deepseek-chat` still works as an alias. Re-test only if you change provider |
| A2 | 🟢 **`solana-mcp` (sendaifun) startup requirements** | Students have DeepSeek and nothing else | Lessons 2, 4 | **2026-08-19 ✅ Not a problem.** Its README marks `OPENAI_API_KEY` as `# OPTIONAL`; only `SOLANA_PRIVATE_KEY` and `RPC_URL` are needed. Note the package is stale (v1.0.1, published 2025-04-10) — the CLI fallback matters more than the key question |
| A3 | 🟢 **Supabase MCP write mode** | Lesson 5 silently fails if the server is read-only | Lessons 2, 5 | **2026-08-19 ✅ Write is the default.** v0.10.0 (published 2026-08-10) accepts `--read-only` with `default: false`. Just don't pass the flag. Other options: `--access-token`, `--project-ref`, `--api-url`, `--features` |
| A4 | 🔴 **MWA packages against the current Expo SDK.** Which package combination actually builds and connects to Phantom today? | Lesson 6 is the heart of the course. AI researches this live, but you must already know the answer | Lesson 6 | **2026-08-20 ⏳ Scheduled** — the instructor has an Android phone; the run-through happens when it's on the desk. The packages themselves are alive and current (`@solana-mobile/mobile-wallet-adapter-protocol` and `-web3js`, both **v2.3.0, published 2026-08-17** — see C8), so this is now about the *build*, not the packages. Use the script below |

### The phone run-through (closes A4)

Do this once, in order, with the phone on the desk. Write the answers into A4 — the numbers matter more than the pass/fail, because students plan their lesson around them.

- [ ] **1. Scaffold** an Expo app exactly as Lesson 6 Part 4 does, and open it in Expo Go. *Record:* did the skeleton run?
- [ ] **2. `eas build -p android --profile development`.** *Record the real wall-clock time*, queue included — Expo documents 90+ minute waits on the free tier (E2), and Lesson 6's schedule depends on this number
- [ ] **3. Install the dev build**, run `npx expo start --dev-client`, confirm the phone connects. *Record:* did the venue-style network need tunnel mode?
- [ ] **4. Add MWA** and connect Phantom. *Record which package versions actually built* — that's the A4 answer, and it's the one thing no amount of reading substitutes for
- [ ] **5. Sign a devnet transaction** from inside the app. *Record:* did Phantom need to be on Testnet Mode for it to work?
- [ ] **6. `eas build -p android --profile preview`**, install the standalone APK, and check the Supabase keys reached it (Lesson 7 Part 2 step 2 — the step that produces a blank screen when skipped)
- [ ] **7. Zed settings path on your OS** — the course says `Cmd/Ctrl+,`; confirm that still opens the right file

If step 4 fails, the fix goes into Lesson 6 Part 6 and the answer into C8 — that's the whole point of doing it before a room full of people does.

---

## B. External facts the lessons state

Each row is a claim written into the course text. Open the source, compare, and **edit the lesson** if it differs.

### Colosseum hackathon

| # | Claim | Where it's written | Verify at | Checked |
|---|---|---|---|---|
| B1 | 🟢 Fall hackathon runs **Sep 28 — Nov 2, 2026** | README (Timeline), overview, L1 Part 16, L2 Part 5, L8 header, L9 Part 9 | colosseum.com | **2026-08-19 ✅ Confirmed** by Colosseum's own blog: "the spring online hackathon running from April 6 through May 11 and the fall edition from September 28 through November 2" |
| B2 | 🟢 **You may start building before the official start** | overview ("two targets"), L2 Part 5 fact table | blog.colosseum.com/how-to-win-a-colosseum-hackathon/ | **2026-08-19** ✅ **Confirmed, and it's generous:** "participants can start building **2 months prior to the start date**". The course's whole premise is legal. Same post confirms the hackathon "runs 5 weeks" |
| B3 | 🟡 Prize structure | overview, L1 Part 16, L2 Part 5 | colosseum.com + the how-to-win post | **2026-08-19** ✅ **"40 individual prizes per hackathon"** — confirmed verbatim, so "~40 prizes" is right. Accelerator: "mentor network, pre-seed funding, private platform features"; colosseum.com advertises **$250,000 in pre-seed**. ⚠️ The **$30K Grand Champion figure is NOT confirmed anywhere** — the course no longer states it, keep it that way |
| B4 | 🟢 **Pitch video ≤ 3 min, technical demo 2-3 min** | L2 Part 5, L8 Parts 1/5/6 | blog.colosseum.com/perfecting-your-hackathon-submission/ | **2026-08-19** ✅ **Exact:** pitch "no more than three minutes long", tech demo "2-3 minute video". Their common-mistakes list also matches L8 Part 9's trap table, including "forgetting to grant judges access to google docs, pitch videos, github repos" |
| B5 | 🟡 Winning teams are commonly **2-4 people**; solo allowed with justification | L2 Part 5, L8 Part 2 | both Colosseum posts | **2026-08-19** ⚠️ **Colosseum's own two posts disagree slightly** — quote whichever you use: "many of the top-performing teams are two or three people" (Perfecting) vs "the average winning team size now above 3" (How to win). Both confirm solo is allowed but must be justified. The course's "commonly 2-4, solo allowed with justification" spans both; don't over-precise it in class |
| B6 | 🟢 **Colosseum Eternal** runs year-round | L8 Troubleshooting, L9 Part 9 | colosseum.com/eternal | **2026-08-19** ✅ **Live** (HTTP 200), currently open with a countdown. Framing on the main page: "Launch a product in 4 weeks and compete for $250,000 in pre-seed funding" — so it's a genuine alternative for anyone who misses the fall window |
| B7 | 🟢 The three blog posts still exist | L2 Part 5 | blog.colosseum.com | **2026-08-19** ✅ **All three return HTTP 200** and their content still matches what L2's fact table claims |
| B8 | 🟢 Cofounder Matching still exists as a platform feature | L8 Part 2 | colosseum.com | **2026-08-19** ⏸ **Not verified** — it sits behind login. The user-facing claim in L8 is soft ("platform feature: find founders by skills"), so a rename wouldn't break the lesson. Check it when you next log in |
| B9 | 🟢 The submission form's actual field list | L8 Part 9 | The live form — students copy it down in class | **2026-08-19 ⏸ Registration not yet open** for the fall season. L8 Part 9 is written to work from whatever the site shows on the day — if the form isn't up, students use the FAQ and the Eternal form as a stand-in |

### Solana Mobile grants

| # | Claim | Where it's written | Verify at | Checked |
|---|---|---|---|---|
| B10 | 🟢 **The six evaluation criteria and their names** | L2 Part 6 table, L9 Part 1 table | solanamobile.com/grants | **2026-08-19 ✅ All six confirmed verbatim**: Mobile-First Implementation · Solana Mobile Stack Use (MWA + Seed Vault) · Proposed Scope and Milestone Timeline · Team Ability to Execute · Clear Use of Funds · Community and Open Source |
| B11 | 🟡 **Is the grant round open?** | L9 Part 1, L9 Homework #3 | solanamobile.com/grants | **2026-08-19 ✅ Open** — the page carries live "Apply now" buttons. Re-check each cohort |
| B12 | 🟡 **Grant sizes** | L9 Part 1 (budget prompt) | solanamobile.com/grants | **2026-08-19 ⚠️ Not published.** No amounts or ranges appear on the grants page. L9's approach — have AI look it up and ask you if it can't find one — is correct. Be ready to supply guidance yourself |
| B13 | 🟡 **Seed Vault: devices, SDK, simulator** | L6 Part 8 | docs.solanamobile.com/developers/seed-vault | **2026-08-19** ✅ **Three things to know.** (1) The SDK is the repo **`solana-mobile/seed-vault-sdk`** (⭐100, pushed 2026-08-17) — the npm package `@solana-mobile/seed-vault` that L6 names as "historical" **does not exist**, so let AI find the current artefact. (2) **A Seed Vault simulator exists** in that repo for testing on emulators — better than L6's "needs a real Seeker" framing. (3) **The important one:** Solana Mobile's own docs say Seed Vault is "designed for wallet app developers, not general dApp developers (who should use Mobile Wallet Adapter instead)" — yet the grant criteria ask for both. Know this before a student asks; the honest grant answer is "we use MWA because we're a dApp" |
| B14 | 🟢 dApp Store still part of the Solana Mobile Stack | L2 Part 6, L6 Part 1, L9 Part 1 | solanamobile.com | **2026-08-19** ✅ solanamobile.com and the grants page both still present the Stack as MWA + Seed Vault + dApp Store |

---

## C. Packages, CLIs and skills

Every install command in the course. If one has moved, the lesson stalls at exactly that step.

| # | Command / package | Used in | Checked (2026-08-19 unless noted) |
|---|---|---|---|
| C1 | 🟢 `npx skills add addyosmani/agent-skills` — **24 workflows + 4 personas** | L3 Part 2 | **2026-08-19** ✅ **Exact match.** Repo alive (⭐88 585, pushed 2026-08-14). `skills/` holds exactly **24** folders, including all seven the course names. `agents/` holds exactly **4**: code-reviewer, security-auditor, test-engineer, web-performance-auditor |
| C2 | 🟡 `npx skills add ColosseumOrg/colosseum-resources` | L2 Part 8 | **2026-08-19** ⚠️ **Repo exists but is thin and stale** — 0 stars, last push 2026-04-16. The install may work while the content underdelivers. L2 Part 8 is a nice-to-have; don't spend class time if it fails |
| C3 | 🟢 the context skill in L1 Part 11 | L1 Part 11 | **2026-08-19** ❌→✅ **This was broken and is now fixed.** `anthropics/skills` contains 19 skills and **context-optimization is not among them** — the command would have failed. Replaced with the verified `npx skills add https://github.com/addyosmani/agent-skills/tree/main/skills/context-engineering` (the skills CLI documents this direct-path form), which also means L1 previews the same pack L3 installs |
| C4 | 🟢 `@supabase/mcp-server-supabase` | L2 Part 4, L5 | **2026-08-19** ✅ v0.10.0, published 2026-08-10. See A3 for flags — write is the default |
| C5 | 🟡 `solana-mcp` — tool names | L2 Part 4, L4 Parts 4-6 | **2026-08-19** ✅ **All four tool names confirmed** in the package README, plus `GET_TPS`. Env vars per A2. ⚠️ Package is stale (v1.0.1, 2025-04-10) — it's the oldest dependency in the course. Keep the CLI fallback ready |
| C6 | 🟢 `@playwright/mcp` | L2 Part 4, L2 Troubleshooting | **2026-08-19** ✅ v0.0.79, published 2026-08-06 — actively maintained |
| C7 | 🔴 The official **GitHub MCP** server | L2 Part 4 | **2026-08-19** ⚠️ **Moved.** The npm package `@modelcontextprotocol/server-github` is **deprecated** ("Package no longer supported", last publish 2025-04-08). The official server is now **`github/github-mcp-server`** (⭐32 362, pushed today) — a Go binary / Docker image / hosted remote server, not an npm install. L2's prompt says "the official GitHub MCP server" and asks AI to check the current README, so it should survive — but if a student's AI reaches for the npm package, it will install a dead one. Watch for this |
| C8 | 🟢 `@solana-mobile/mobile-wallet-adapter-protocol` + web3js helpers | L6 Part 6 | **2026-08-19** ✅ **Both fresh: v2.3.0, published 2026-08-17.** Good news for the riskiest lesson in the course. Whether they *build* against your Expo SDK is still A4 |
| C9 | 🟡 `@solana-mobile/seed-vault` | L6 Part 8 | **2026-08-19** ❌ **Does not exist on npm.** See B13 — the artefact is the `solana-mobile/seed-vault-sdk` repo (Android/Kotlin), with a simulator. L6 already asks AI to find the current package, which is why this doesn't break the lesson |
| C10 | 🟢 `eas-cli` | L6 Part 5, L7 Part 2 | **2026-08-19** ✅ v22.0.0, published 2026-08-14 — actively maintained. Profile semantics unverified without a real build (A4) |
| C11 | 🟢 `@supabase/supabase-js` | L5 Part 5, L6 Part 7b | **2026-08-19** ✅ v2.112.3, published 2026-08-11 |
| C12 | 🟢 `create-expo-app`, `expo-dev-client` | L6 Parts 4-5 | **2026-08-19** ✅ `create-expo-app` v4.0.0 (2026-05-15), `expo-dev-client` v57.0.13 (2026-08-17) |
| C13 | 🟢 Homebrew install script | L1 Part 6 | **2026-08-19** ✅ brew.sh returns 200. The two `shellenv` lines are printed by the installer itself, so they self-correct |
| C14 | 🟢 `gh auth login` flow | L1 Part 7 | **2026-08-19** ✅ `gh` 2.86.0 installs and the flow is unchanged |

---

## D. URLs used in the lessons

Open each one. A dead link on the big screen costs five minutes and some credibility.

| Priority | URL | Used in | 2026-08-19 |
|---|---|---|---|
| 🔴 | `https://colosseum.com` | README, overview, L1, L2, L8 | ✅ 200 (also `/hackathon` and `/eternal`) |
| 🔴 | `https://solanamobile.com/grants` | overview, L2, L9 | ✅ 200, criteria intact, "Apply now" live |
| 🔴 | `https://platform.deepseek.com` | L1 Part 4 | ⚠️ 403 to `curl` — bot filtering. **Fine in a real browser**; don't panic when a script says it's down |
| 🔴 | `https://zed.dev/download` | L1 Part 3 | ✅ 200 |
| 🔴 | `https://phantom.app` | L1 Part 14, L2, L6 | ✅ 200 |
| 🔴 | `https://supabase.com` | L2 Part 3b, L5 | ✅ 200 |
| 🔴 | `https://expo.dev` | L6 Prerequisites | ✅ 200 |
| 🔴 | `https://faucet.solana.com` | L1 Part 15, L4 | ✅ 200. Page mentions **GitHub sign-in and a rate limit** — L1's "sign in if it asks" wording is correct |
| 🟡 | `https://api.devnet.solana.com` | L2 Part 4, L6 Part 7 | ✅ Reachable. Airdrop rate limits are the real constraint, not availability |
| 🟡 | `https://explorer.solana.com`, `https://solscan.io` | L1, L4 | ⚠️ 429 / 403 to `curl` — rate limiting and bot filtering. **Both fine in a browser** |
| 🟡 | The three `blog.colosseum.com` posts | L2 Part 5 | ✅ All 200, content still matches L2's claims |
| 🟡 | `https://notebook.google.com` | L8 Part 5, L9 Part 6 | ✅ 200 (redirects to notebooklm.google.com, which is also 200). ⚠️ **Slide export to PDF/PPTX is still unverified** — it needs a login, so check it yourself before L9 |
| 🟡 | `https://loom.com` | L8 Parts 5-6 | ✅ 200. Free-tier recording limits unverified — check before L8 |
| 🟢 | `https://brew.sh` | L1 Part 6 | ✅ 200 |
| 🟢 | `https://solana.com/docs` | L2 Part 7 | ✅ 200 |
| 🟢 | `https://github.com` | L1 | ✅ 200 |

> 🤖 **Three of these answer `403`/`429` to a script but load fine in a browser** (DeepSeek, Solana Explorer, Solscan). That's bot filtering, not downtime. If you automate this check, don't let it cry wolf.

## E. Money

The course promises specific costs to students in Lesson 1. Being wrong here damages trust more than any technical failure.

| # | Claim | Where | Verify at | Checked |
|---|---|---|---|---|
| E1 | 🟢 DeepSeek: **$5 covers the whole course** | README (What It Costs), L1 Prerequisites + Part 4 | api-docs.deepseek.com/quick_start/pricing | **2026-08-19 ✅ Verified and revised down.** `deepseek-v4-flash` off-peak: $0.22/M input (cache miss), $0.66/M output — half the peak rate. Peak is only 01:00-04:00 and 06:00-10:00 UTC, so normal class hours are off-peak. An earlier $10-20 estimate in this course was too high and has been corrected |
| E2 | 🔴 **EAS Build free tier** | README, L6 Part 5, L7 Part 2 | expo.dev/pricing | **2026-08-19** ⚠️ **Worse than the course assumed, now corrected.** Free tier: **15 Android builds/month**, **1 concurrent build**, **low-priority queue** with documented waits of **90+ minutes**, and a **45-minute build timeout**. L6 and L7 previously promised 10-20 minutes; both now carry the real numbers. **This is the single biggest scheduling risk in the course** — start your demo build before class, every time |
| E3 | 🟢 **fly.io is not free** | README, L7 Part 1 + Part 4 | fly.io/pricing | **2026-08-19** ✅ **Confirmed with figures.** "All organizations require a credit card on file." Cheapest always-on machine (shared-cpu-1x, 256 MB, iad): **$2.02/month**. The course's "not free, a few dollars a month" is accurate |
| E4 | 🟡 Free tiers still free: GitHub, Supabase, Vercel, Phantom, Colosseum, Loom, NotebookLM | README (What It Costs) | each site | **2026-08-19** 🟡 **All reachable and still advertising free tiers**, but the *limits* sit behind signup. Supabase free projects pause after inactivity — worth knowing if a cohort spans a break |
| E5 | 🟡 **Faucet limits** | L1 Part 15, L4 Part 4 | faucet.solana.com | **2026-08-19** ✅ Up, and the page does reference **GitHub sign-in and a rate limit** — so L1's wording is right. Exact amount per request isn't stated publicly; it varies. Keep 20+ devnet SOL of your own for students it refuses |

---

## F. Per-lesson smoke test (day of)

Ten minutes on the classroom network, on the day, before students arrive.

- [ ] **L1** — brew / npm / GitHub reachable from this network. Zed downloads. DeepSeek signup reachable
- [ ] **L2** — Supabase signup, GitHub token page, faucet, and all three Colosseum blog posts load *here*. Colosseum is JS-heavy: expect Playwright to struggle and web search to be the fallback
- [ ] **L3** — `npx skills add addyosmani/agent-skills` completes on a clean profile
- [ ] **L4** — your own MCP/CLI wallet funded (keep 20+ devnet SOL for students the faucet refuses). Faucet checked this morning
- [ ] **L5** — every student has an "Active" Supabase project (chase in the class chat the day before)
- [ ] **L6** — **highest risk.** Phantom installs from the Play Store. Students have their seed-phrase paper. Network allows Expo **tunnel mode** (classroom Wi-Fi with client isolation breaks LAN). Your own demo EAS build started *before* class
- [ ] **L7** — your demo APK build started before class. You know which students have a backend
- [ ] **L8** — Loom records. The Colosseum submission form (or its FAQ) opens on the big screen
- [ ] **L9** — NotebookLM upload + slide generation works today. Timing arithmetic done for your group size

---

## G. Verification record

Fill this in each cohort. If the last row is more than a couple of months old, redo section A before teaching.

| Cohort / date | Verified by | Sections done | What changed in the world | Lessons edited |
|---|---|---|---|---|
| 2026-08-20 | Instructor | A4 (scheduled) | Android phone available; MWA build run-through booked. Everything else in this file is closed | none yet |
| 2026-08-19 | Claude, via npm/GitHub/PyPI APIs, a live DeepSeek key, HTTP checks and web sources | **A1-A3, all of B, C, D, E** — only A4 left open | Two course errors found: the L1 context skill didn't exist, and EAS free-tier waits are 90+ min not 10-20. DeepSeek far cheaper than assumed. Official GitHub MCP moved off npm. `@solana-mobile/seed-vault` doesn't exist; Seed Vault is for wallet apps and has a simulator. Colosseum's 2-month build window, 40 prizes and both video lengths confirmed verbatim | L1 (cost + skill command), L2 (Supabase + solana-mcp config), L6 + L7 (EAS timings), README |
| | | | | |

---

## What to do when something has changed

1. **Fix the lesson text**, not just your own notes — the next instructor reads the file, not your memory
2. **Add a line to `wiki/log.md`**: `## [YYYY-MM-DD] update | Solana course: <what changed>`
3. **Update the `updated:` date** in the edited lesson's frontmatter
4. If a claim can no longer be verified from a primary source, **remove the number** rather than softening it. The course's own rule, taught in Lesson 2, is that an unsourced claim gets marked UNVERIFIED or deleted. That applies to the course itself
