---
title: "Solana Lesson 5: Database — SupaBase for Your Product"
type: lesson
difficulty: intermediate
tags: [solana, database, supabase, mcp, backend, rls, crud]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 5
---

# Solana Lesson 5: Database — SupaBase for Your Product

**Format:** Instructor-led, in the room or online — screen sharing + hands-on practice
**Duration:** ~2 hours

## How This Lesson Works

Same flow: instructor explains → demonstrates → drops prompt in chat → students copy-paste and repeat → wait for all → questions → next section.

---

## Prerequisites

From Lessons 1-4, every student must have:
1. ✅ Zed with DeepSeek connected
2. ✅ SPECIFICATION.md + PLAN.md with the seven phases (today we do **Phase 2 — Data layer**)
3. ✅ Lesson 4 done: balance, transfer and SPL token exercised via the Solana MCP (or the CLI fallback)
4. ✅ A Supabase project created in Lesson 2, status "Active"
5. ✅ GitHub working

---

## Part 0: Build Track Checkpoint (5 minutes)

Before we touch the database — where is **your product**?

Around the room, one sentence each: *"I finished N Phase 4 tasks; the next one is X."*

If the answer is zero, that's information, not shame — but fix it this week. In Zed:

```
Read PLAN.md. I haven't started Phase 4 yet. Pick the smallest
Phase 4 task that produces something I can see working, and
do just that one now: build it, test it, commit it, mark it done.
Then tell me the next one and how long it should take me.
```

**Instructor:** note who is at zero for a second week running. Those students need a different Phase 4 scope, not more homework.

---

## Part 1: Why a Blockchain App Still Needs a Database

You might wonder: "doesn't the blockchain store everything?" Good question — and the answer makes you smarter than many developers:

| Store on the blockchain | Store in a database |
|-------------------------|---------------------|
| Money movements, tokens, signatures — things needing trust and permanence | Everything else: user profiles, settings, drafts, cached leaderboards |
| Costs fees (even tiny ones) and time | Free and instant |
| Permanent, public | Private, editable, deletable |

**The right design:** blockchain for the *valuable, trust-critical* part; database for the *fast, private, editable* part. Example: a betting app stores the **stakes and payouts on-chain**, but stores your avatar, nickname, and notification preferences in a database.

**Our database of choice: SupaBase** — free tier, instant setup, built-in authentication, and plain SQL behind a friendly dashboard. AI knows it deeply.

**And here's the trick for this lesson:** we connect SupaBase to Zed through **MCP** — a plug that gives AI real tools to work with the database. AI creates tables, applies migrations, and runs queries itself. You just watch and confirm.

**Chat drop:** Discuss with your neighbor: in YOUR product (from SPECIFICATION.md), what belongs on-chain and what belongs in a database? Write 2+2 examples.

---

## Part 2: Find Your App Keys

In Lesson 2 you did two things: created a **Supabase project** and connected the **Supabase MCP** to Zed. So AI is already your database admin, and the project is already provisioned. All that's missing are the keys the **app itself** needs.

1. Open [supabase.com](https://supabase.com) → your project → **Project Settings → API**:
   - **Project URL** (`https://xxxx.supabase.co`)
   - **anon public key** — safe for apps (protected by Row Level Security)

**Three keys, three homes — learn this table once and you'll never leak a secret:**

| Key | Power | Where it lives | Ever in the app? |
|-----|-------|----------------|------------------|
| **Access token** (`sbp_…`) | Full admin — creates and drops tables | Zed's settings.json only | ❌ Never |
| **anon public key** (`eyJ…`) | Limited, guarded by Row Level Security | `.env` in your project | ✅ Yes, that's its job |
| **service_role key** | Full admin, bypasses RLS | Nowhere, for this course | ❌ Never, not even server-side yet |

**First, verify AI can actually reach the database.** In Zed:

```
Using the Supabase MCP, list my Supabase projects and the tables
in the project I created in Lesson 2. Then tell me whether you
are connected in read-only or write mode — I need write mode
today to create tables.
```

If it answers read-only, or the tools aren't there at all, use the fallback below and keep going. Do not spend the lesson debugging.

> 🛟 **Fallback without the MCP.** Everything today also works through the dashboard: AI writes the SQL, you paste it into **Supabase → SQL Editor → Run**. Add this line to every prompt in this lesson: *"My Supabase MCP isn't available — give me SQL to paste into the SQL Editor instead, and tell me what to check in the Table Editor afterwards."* You lose the automation, not the lesson.

**Chat drop:**
- SupaBase dashboard → Project Settings → API → copy Project URL and anon key
- In Zed: verify the MCP sees your project and is in write mode
- ⚠️ The access token (admin power) stays in Zed's settings — never in the app

---

## Part 3: Store the App Keys Safely

In Zed, from your project folder:

```
Set up secure config for my SupaBase credentials. I will paste
the actual values in myself — use placeholders.

1. Make sure .env exists and is listed in .gitignore
2. Add these two variable names to .env with empty values:
   SUPABASE_URL=
   SUPABASE_ANON_KEY=
3. Create .env.example with the same names, also empty, and
   commit that one
4. Show me .gitignore's contents so I can see .env is excluded
5. Tell me exactly which lines to fill in and where the values
   come from in the Supabase dashboard
```

> ⚠️ **Type the values into `.env` yourself.** The prompt above tells AI to *create the file and the variable names*; you paste the actual URL and key into the file by hand in Zed. Same rule as Lessons 1 and 2 — secrets don't travel through the chat.

**Chat drop:** Paste the prompt. Then type your real values into `.env` yourself. Verify `.env` is gitignored (`git status` must not list it).

---

## Part 4: AI Designs and Creates the Schema via MCP

Now the magic: AI reads your spec and creates the whole database — through MCP, no manual dashboard clicking. In Zed:

```
Read SPECIFICATION.md and PLAN.md (Phase 2 = the data layer).

Use the Supabase MCP tools to build my database:

1. Design the schema: list the tables we need (users, plus whatever
   the product needs — profiles, items, leaderboards, posts…)
   with columns, types, primary keys, and relationships
2. Show me the design as a short summary BEFORE creating anything
   — I'll confirm
3. Which tables should store a Solana wallet address (to link
   database rows to on-chain accounts)?
4. Then apply it via MCP (migrations / SQL)
5. Enable Row Level Security (RLS) on every table and create basic
   policies: users can read public data, and can write only their
   own rows
6. Show me the final list of tables and confirm

Save the schema description to DATABASE.md in the project root.
```

Confirm the design when AI asks, then let it apply everything.

**Chat drop:** Paste the prompt → review the schema design → confirm → check the result in the SupaBase dashboard (Table Editor) — your tables exist.

---

## Part 5: Connect the App to SupaBase

**Important — there is no app screen yet.** The Expo mobile app gets built in Lesson 6. That is deliberate: today we build the data layer as a **standalone module with a test script**, so it is already proven working when the UI arrives. Lesson 6 then wires it into a real screen in about ten minutes.

Your `.env` already holds the anon key from Part 3. In Zed:

```
Connect my project code to SupaBase.

1. Install the SupaBase client library for my stack
   (@supabase/supabase-js — the app becomes React Native + Expo
   in Lesson 6, and this library works there too)
2. Create a small data-access module (e.g. src/db.ts) that reads
   SUPABASE_URL and SUPABASE_ANON_KEY from .env and exports
   simple functions — one per operation my product needs
3. Write a test script I can run from the terminal that calls
   those functions: create a row, read it back, update it,
   delete it. Print the results
4. Run it and show me the output
5. Do NOT build any UI today — Lesson 6 wires this into the app

Use the incremental-implementation skill: one slice, test, commit.
Mark the Phase 2 tasks done in PLAN.md.
```

**Chat drop:** Paste the prompt. Run the test script — see real rows appear in the Supabase Table Editor. Commit.

---

## Part 6: Verify with the Team — via MCP

Back to our standing team from Lesson 3. In Zed:

```
Read TEAM.md.

Run the test-engineer verification:
- Use Supabase MCP tools to check the tables match DATABASE.md
- Test the feature end to end (add, read, update data)

Then run the security-auditor review:
- Are RLS policies actually enabled? (check via MCP)
- Are keys only in .env and Zed settings?
- Could a user read or modify someone else's rows?
- Any access token leaked into the client code?

Report findings and fix anything important.
```

**Chat drop:** Paste the prompt. If the auditor finds issues — let AI fix them via MCP, then re-verify.

---

## Homework

1. Finish the remaining **Phase 2** tasks in PLAN.md — every data operation your product needs should have a function and a passing test
2. Look at the SupaBase Auth section — ask AI: `Explain how SupaBase Auth works and whether my product needs user login. What's the simplest login option for a mobile app?`
3. Push all changes to GitHub (verify `.env` stays out; the access token lives only in Zed settings)
4. **Product Build Track:** two more **Phase 4** tasks. Lesson 6 opens with the checkpoint again
5. In the group chat: one line — "My database now stores [X]"

---

## Troubleshooting

### MCP Doesn't Connect / Tools Don't Appear in Zed

```
The Supabase MCP server doesn't appear / errors in Zed. Tell me
to open settings with Cmd/Ctrl+, then show me the correct
context_servers entry for a command-based MCP server (use
YOUR_TOKEN_HERE as a placeholder — I'll type the real token in),
and how to restart the MCP connection. If it's still broken after
10 minutes, switch me to the SQL Editor fallback.
```

### I Never Created the SupaBase Project in Lesson 2

Do it now, by hand — it takes four minutes: [supabase.com](https://supabase.com) → Sign up → **New project** → name + nearest region + database password (save it) → wait for "Active". Then continue from Part 2. If creation fails or hangs, ask AI: `SupaBase project creation failed. Here's what I see: [describe]. Guide me through fixing it (region, password rules, browser issues).`

### RLS Blocks Everything

```
My app can't read or write data — errors mention RLS. Diagnose my
policies (via MCP), explain what's blocking, and fix the policies
so public reads work and writes are limited to the owner.
```

### Connection Errors in the App

```
My app shows a connection error to SupaBase: [paste error].
Check the URL and anon key are loaded correctly from .env and
that the client is initialized once. Fix it.
```

### I Regenerated My Access Token

If you revoked/replaced the token: update the MCP config in Zed's settings (ask AI to do it) — that's the only place the old token lives.

### Schema Needs to Change

```
My product changed: I need [new table / new column / remove X].
Use Supabase MCP to write and apply the migration, and update
DATABASE.md.
```

---

## Related Materials

- [lesson-04](lesson-04.md) — Previous lesson: Solana fundamentals
- [lesson-06](lesson-06.md) — Next lesson: Solana Mobile (Android app + MWA)
- *lesson-06-database* — Online English Lesson 6 (source material)
- *off-line-lesson-03* — Original off-line course database lesson (SupaBase path)
- *near-offline-lesson-05* — NEAR course MCP lesson (same Zed MCP pattern, different server)

## Result

After this lesson, each student has:
- A clear mental model: what goes on-chain vs in a database
- SupaBase connected to Zed via the official Supabase MCP (access token in Zed settings only)
- Tables derived from SPECIFICATION.md — designed and created by AI through MCP (or by SQL they pasted themselves)
- Row Level Security enabled with sensible policies
- App keys in `.env` (gitignored), access token safely outside the project — and the three-keys table understood
- A data-access module plus a passing test script — Phase 2 complete, ready for the UI in Lesson 6
- A security review pass by the AI auditor (via MCP)
- DATABASE.md documenting the schema
- Everything committed and pushed
