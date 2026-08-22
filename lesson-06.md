---
title: "Solana Off-line Lesson 6: Solana Mobile — Android App, Mobile Wallet Adapter & Seed Vault"
type: lesson
difficulty: intermediate
tags: [solana, offline, mobile, react-native, expo, mwa, seed-vault, sms, android, grants]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 6
---

# Solana Off-line Lesson 6: Solana Mobile — Android App, Mobile Wallet Adapter & Seed Vault

**Format:** Instructor-led classroom — screen sharing + hands-on practice
**Duration:** ~3 hours (a cloud build runs in the middle — plan the schedule around it)

## How This Lesson Works

Same flow: instructor explains → demonstrates → drops prompt in chat → students copy-paste and repeat → wait for all → questions → next section.

**One difference today:** in Part 5 we start a cloud build that takes 10-20 minutes. Everyone starts it at the same time, then we use the wait for Part 6. Don't let students idle through it.

---

## Prerequisites

From Lessons 1-5, every student must have:
1. ✅ Zed with DeepSeek connected
2. ✅ Phantom browser wallet on devnet with SOL (Lesson 1) — **and the seed phrase on paper**
3. ✅ Project with SPECIFICATION.md, PLAN.md, and the Phase 2 data module (Lesson 5)
4. ✅ An **Android phone** with "install from unknown sources" allowed, and the **Phantom app** from the Play Store
5. ✅ A free **Expo account** — sign up at [expo.dev](https://expo.dev) before class
6. ✅ Phone and laptop on the same Wi-Fi network

> 📵 **No Android phone?** Two options, in order of preference: (1) borrow one for the two lessons that need it — the app installs and uninstalls in a minute; (2) use an Android emulator (Android Studio), accepting that Phantom-in-emulator is fiddly and slower. Tell the instructor **before** this lesson, not during it — an emulator setup is a 40-minute detour that can't happen mid-class.

---

## Part 0: Build Track Checkpoint (5 minutes)

Same as Lesson 5: one sentence each — *"I finished N Phase 4 tasks; the next one is X."* Today's app is the container your Phase 4 features go into, so an empty Phase 4 means an empty demo in Lesson 8.

---

## Part 1: Why Mobile Is the Future of Crypto

Solana is betting big on phones. The **Seeker** phone ships with crypto built in. The Solana Mobile team says it directly: *"We believe that in the future, most people will experience crypto on mobile."* That's why they fund mobile builders.

**The three reasons this lesson is the heart of our course:**

1. **The grants demand it.** The #1 and #2 Solana Mobile grant criteria are *Mobile-First Implementation* and *Solana Mobile Stack Use*. This lesson delivers both.
2. **The hackathon rewards it.** Frontier's winning teams included several mobile-first products. A phone demo in your pitch video stands out.
3. **It's where users are.** Over 100K+ power users hold Solana phones. Desktop crypto is niche; phone crypto is everyone.

**The Solana Mobile Stack (SMS) — three parts:**

| Part | What It Is | Analogy |
|------|-----------|---------|
| **Mobile Wallet Adapter (MWA)** | A protocol that lets your app ask the user's wallet (Phantom, Solflare…) to sign transactions — no keys ever enter your app | Your app hands the check to the user, they sign it in their wallet app |
| **Seed Vault** | Hardware-protected key storage inside Solana phones (Saga/Seeker) | A bank vault built into the phone itself |
| **dApp Store** | The app store on Solana phones | Google Play, but crypto-native |

**Chat drop:** Ask AI: `Explain Mobile Wallet Adapter in one paragraph with an analogy. Why is it safer than an app asking for my seed phrase?`

---

## Part 2: How MWA Actually Works (30-Second Version)

When your app wants to send 1 SOL:

```
Your app ──"please sign this transaction"──▶ Wallet app (Phantom)
                                              │ user taps Approve
Your app ◀──signed transaction───────────────┘
Your app ──broadcast to devnet RPC──────────▶ Blockchain ✅
```

Your app **never sees the private key**. The wallet signs inside its own secure environment. This is the pattern every serious mobile dApp uses — and what the grants explicitly require.

**Chat drop:** Neighbor check: "Where does the private key live in the MWA flow — in our app, or in the wallet?" (Answer: in the wallet.)

---

## Part 3: Put Phantom on Your Phone — and Fund It

Your app will ask a **wallet app on the phone** to sign transactions. Right now your devnet SOL lives in a *browser extension* on your laptop. The phone knows nothing about it. Fix that first — everything later in this lesson depends on it.

1. Install **Phantom** from the Google Play Store on your Android phone
2. Choose **"I already have a wallet"** → enter the **seed phrase from your paper** (Lesson 1)
3. Set a phone password / biometric unlock
4. **Settings → Developer Settings → Testnet Mode ON** — the yellow "Devnet" badge must appear, exactly like in the browser
5. Check the balance: you should see the same devnet SOL as in your browser extension. Same seed phrase = same wallet = same money

> 🔐 **This is the one legitimate place a seed phrase is ever typed:** restoring your own wallet inside the official Phantom app, downloaded from the Play Store. Nowhere else. Not into your own app, not into the AI panel, not into a website that says it will "verify" your wallet. If your app ever asks a user for a seed phrase, you have built the wrong thing — and that's precisely what Mobile Wallet Adapter exists to prevent.

**If the phone shows 0 SOL:** your paper phrase restored a different wallet, or the app is still on mainnet. Check the Devnet badge first. If the balance is genuinely empty, open [faucet.solana.com](https://faucet.solana.com) and airdrop to the address the *phone* shows — or ask a classmate to send you 0.5 devnet SOL. You need **at least 0.1 SOL on the phone** for Part 7.

**Chat drop:**
- Play Store → Phantom → "I already have a wallet" → seed phrase from paper
- Settings → Developer Settings → Testnet Mode ON → yellow Devnet badge
- Confirm the phone shows your devnet SOL. Need ≥ 0.1 SOL to continue

---

## Part 4: Create the Mobile App Skeleton

We build the app as a **React Native + Expo** project — the friendliest path for AI-assisted development, with a smooth route to the APK (Lesson 7).

In Zed (your project folder), paste:

```
I'm building a mobile app for my hackathon project. Read
SPECIFICATION.md and PLAN.md first.

Create a React Native + Expo app in a subfolder called "mobile":

1. Scaffold with create-expo-app (blank TypeScript template)
2. Set up a minimal 2-screen structure:
   - Home screen: app name, wallet connection status, and a
     placeholder for the main feature
   - Wallet screen: connect/disconnect + show wallet address
3. Simple dark theme, clean design
4. Run it and tell me how to open it in Expo Go on my phone

Use the incremental-implementation skill: one slice, test, commit.
Mark the Phase 3 skeleton tasks done in PLAN.md.
```

**Chat drop:** Paste the prompt. Install **Expo Go** from the Play Store, scan the QR code. You have an app on your phone — written by AI.

> Expo Go is a preview shell. It's perfect for this skeleton and useless for the next step — which is exactly what Part 5 is about.

---

## Part 5: Leave Expo Go — Build a Development Build

**Read this before you try anything:** Mobile Wallet Adapter **cannot work in Expo Go. Ever.** Not "sometimes", not "with the right settings".

Expo Go is a single pre-built app on the Play Store containing a fixed set of native code. MWA needs its own native Android code — code that has to be *compiled into an app*. Expo Go can't grow new native code, so it can't host MWA. This surprises almost everyone, including AI assistants, which will happily suggest workarounds that don't exist.

The answer is a **development build**: your own private version of Expo Go, compiled in Expo's cloud with your app's native modules inside. You build it once today and keep using it for the rest of the course.

| | Expo Go | Development build | Production APK (Lesson 7) |
|---|---|---|---|
| Where it comes from | Play Store | EAS cloud build — see the timing warning below | EAS cloud build |
| Native modules like MWA | ❌ Never | ✅ Yes | ✅ Yes |
| Live reload from your laptop | ✅ | ✅ | ❌ Standalone |
| What it's for | Today's Part 4 skeleton | All development from now on | Judges, users, your phone |

In Zed:

```
My Expo app needs native modules (Mobile Wallet Adapter), so
Expo Go won't work. Set me up with an EAS development build.

1. Install the EAS CLI (npm install -g eas-cli)
2. Walk me through: eas login (I have a free expo.dev account)
3. Run: eas build:configure — explain the eas.json it creates
4. Make sure eas.json has a "development" profile that produces
   an installable Android APK with the dev client, and that
   expo-dev-client is installed
5. Start the build: eas build -p android --profile development
6. Give me the link to watch the build and tell me the current
   queue position if you can see it

Explain each step before running it. Show me any config file
changes before you make them.
```

> ⏱️ **Plan for a long wait.** Expo's free tier gives you 15 Android builds a month on a **low-priority queue with 1 concurrent build** — Expo's own docs say waits can reach **90+ minutes** at busy times, with a 45-minute build timeout on top. A 15-minute build is a good day, not the rule. This is why the instructor starts a build before class and why Part 6 is designed to fill the wait.

**Everyone starts the build now.** While it runs, do Part 6 — read it, understand the flow, and have the prompt ready. Then:

7. When the build finishes, open the link on your **phone** and install the APK (allow "unknown sources" if asked)
8. Back in Zed: `npx expo start --dev-client`
9. Scan the QR code with your new dev-build app — not with Expo Go

From now on, "open my app" always means the dev build.

**Chat drop:**
- Paste the prompt above → start the build → note the link
- While it builds: read Part 6
- Build done → install the APK on the phone → `npx expo start --dev-client` → scan

> 🛟 **Build failed or queue too long?** The free EAS tier queues behind paying customers; Expo documents waits of 90+ minutes at peak. Don't stall the class: pair up with a classmate whose build succeeded and work on their laptop for Parts 6-7, then run your own build as homework. The instructor should also start one build *before* class as a live demo, so the flow can be shown even if every student's build is queued.

---

## Part 6: Connect the Wallet with Mobile Wallet Adapter

Now the crypto part. In Zed:

```
Add Mobile Wallet Adapter to my Expo app.

1. Research the current recommended packages:
   - @solana-mobile/mobile-wallet-adapter-protocol and the web3js
     helpers, and/or react-native-dapp — pick the most maintained
     option for Expo
2. Install them. I am already running an EAS development build,
   not Expo Go — if a package needs a rebuild after installing,
   say so clearly and tell me when to rerun eas build
3. Add a "Connect Wallet" button:
   - authorize a session with the wallet (Phantom on my phone)
   - show the connected public key on screen
4. Add a "Disconnect" button

Handle the case where no wallet app is installed (show a friendly
message with a link to Phantom).

Test on my phone using the development build. Explain each step
so I understand what's happening.
```

**Chat drop:** Paste the prompt. Tap **Connect Wallet** on your phone → Phantom opens → authorize → your public key appears in the app. First MWA flow, done. 🎉

---

## Part 7: Sign a Real Devnet Transaction from Your Phone

Now the money shot. In Zed:

```
Add transaction signing to my Expo app via Mobile Wallet Adapter.

Feature: on the Wallet screen, add a "Sign & Send 0.01 SOL" button.

What it does:
1. Build a devnet transaction: transfer 0.01 SOL from the connected
   wallet to my own address (a self-transfer — safe practice).
   The connected wallet is Phantom on my phone, on devnet, funded
   in Part 3 — if the balance is too low, say so instead of
   sending a transaction that will fail
2. Request signature via MWA (user approves in Phantom)
3. Broadcast to devnet RPC (https://api.devnet.solana.com)
4. Show the transaction signature on screen + a link to view it
   on the devnet explorer

Add basic error handling: user rejects → friendly message;
network error → retry hint.

Test it end to end with my phone. Explain the flow.
```

**Chat drop:** Paste the prompt. Tap the button → approve in Phantom → see the signature → open the explorer link on your phone. **Your phone just signed a blockchain transaction inside your own app.** Screenshot it — you'll use it in the hackathon pitch.

---

## Part 7b: Wire In Your Database (10 minutes)

In Lesson 5 you built a data-access module with a passing test script and no screen to show it on. Now there's a screen. In Zed:

```
Read PLAN.md (Phase 2 = data layer, Phase 3 = mobile app).

My data-access module from Lesson 5 currently only runs from a
test script. Wire it into the Expo app:

1. Move/adapt the module so the app can import it, and make the
   SUPABASE_URL and SUPABASE_ANON_KEY reach the app the Expo way
   (app config / EXPO_PUBLIC_ env vars) — explain what changed
   and why .env alone isn't enough in Expo
2. On the Home screen, show one real piece of data from the
   database, and let me change it and save it
3. Link the row to the connected wallet address where that makes
   sense for my product
4. Test on my phone, commit, and mark the tasks done in PLAN.md
```

**Chat drop:** Paste the prompt. Change something in the app, then refresh the Supabase Table Editor in the browser — your phone just wrote to a database.

---

## Part 8: Seed Vault — The Final Layer

**Seed Vault** is the piece you mention when the grant judge asks "did you use the full Solana Mobile Stack?" It's a hardware-backed key storage on Solana phones: apps can request keys that live in the phone's secure element, sign transactions, and never handle raw key material.

In Zed:

```
Research Seed Vault for my project:
- What is Seed Vault exactly, and which devices support it
  (Saga, Seeker)?
- What is the current SDK package for integrating it
  (historically @solana-mobile/seed-vault)?
- What can my app do with it that MWA alone cannot?
- Can I integrate or prepare for it without owning a Solana phone?

Then:
1. If a devnet-safe integration is possible now — add it behind a
   feature flag ("Seeker mode") and explain what I'd see on a real
   Seeker phone
2. If not — add the integration points and document in README.md
   how the app will use Seed Vault on Solana phones
3. Add a short "Solana Mobile Stack" section to README.md listing:
   Mobile Wallet Adapter (integrated), Seed Vault (status), dApp
   Store (planned)

Save everything and commit.
```

> Honest note for the instructor: full Seed Vault testing requires a Solana phone. For the grant application, what matters is that the app *integrates the Stack* and the plan is credible. This prompt builds exactly that.

**Chat drop:** Paste the prompt. Read the README section AI wrote. Ask AI: `Write 2 sentences I can put in a grant application about my Seed Vault integration.`

---

## Part 9: Update the Plan

In Zed:

```
Read TEAM.md and PLAN.md.

Mark all Phase 3 (mobile app + Solana Mobile Stack) tasks done
that we completed today, and any Phase 2 tasks the wiring
finished. For the remaining ones, adjust the plan.

Then look at Phase 4 (my core product features): now that the app
exists, re-order those tasks so the ⭐ demo feature is next, and
tell me which single one I should finish before Lesson 7.

Then run the code-review-and-quality skill on the mobile/ folder
and fix important findings.

End with a 5-line report.
```

**Chat drop:** Paste the prompt. Read the report. Push everything to GitHub when AI asks.

---

## Homework

1. Show the app to one real person (family/friend). Write down their first reaction — verbatim. (User validation starts now — Lesson 8 needs it.)
2. **Product Build Track — the big one.** Build the ⭐ Phase 4 feature into the app: `Read TEAM.md, SPECIFICATION.md and PLAN.md. Build the starred Phase 4 feature into the mobile app, one thin slice at a time, testing on my phone and committing each slice.` This is the feature your pitch video will show
3. Compare: signing on your phone today vs the MCP transfers in Lesson 4 — who holds the key in each case, and what would a normal user think of each?
4. Commit and push everything
5. Group chat: post a screenshot of your app on your phone

---

## Troubleshooting

### The App Can't Connect to My Laptop

```
My Expo dev server and my phone can't see each other (tunnel/LAN
issues). Here's what happens: [describe]. Guide me through fixing
it — check we're on the same Wi-Fi, then try tunnel mode
(npx expo start --dev-client --tunnel) if the network blocks it.
```

Classroom Wi-Fi with client isolation is the usual culprit — tunnel mode goes around it.

### "MWA Doesn't Work" — Check This First

Are you running the **development build** from Part 5, or still Expo Go? Nine times out of ten this is the whole problem, and no error message says so plainly. The dev build has *your app's* icon and name; Expo Go has the Expo logo. If you're in Expo Go, go back to Part 5.

If you're genuinely in the dev build and a *newly installed* package fails, the build is stale — native modules only appear after a rebuild:

```
I installed [package] and it errors at runtime in my development
build: [paste error]. Do I need to rebuild the dev client? If so,
give me the exact command and tell me how long it takes.
```

### EAS Build Is Queued Forever

Free-tier builds wait behind paid ones. Options, in order: (1) keep working on someone else's finished build and run yours later; (2) build locally instead — `npx expo run:android` with Android Studio installed, which is faster but a heavier setup; (3) run it as homework tonight. Ask AI: `Compare eas build vs npx expo run:android for me — what do I need installed for the local option on [my OS]?`

### Phantom Doesn't Open When I Tap Connect

- Is Phantom installed on the phone? (Not just the browser extension — the phone app)
- Is the phone's Phantom on devnet? (Settings → Developer Settings → Testnet Mode)
- Ask AI: `Phantom doesn't open on authorize. Diagnose the MWA flow and check my configuration.`

### User Rejects the Transaction — App Crashes

```
When the user rejects a signature request, my app crashes/errors.
Add proper rejection handling with a friendly message.
```

### "No Wallet Found" on the Phone

That's expected behavior — the friendly message should show. Install Phantom from the Play Store (Part 3), switch it to devnet, and retry.

### The Phone Wallet Has 0 SOL

The browser extension and the phone app only share money if they were restored from the **same seed phrase**. Check the address on the phone against the one in your browser — if they differ, you created a new wallet instead of restoring. Either restore properly from your paper phrase, or just fund the new phone address from the faucet and use that one from now on (write down which is which).

---

## Related Materials

- [lesson-05](lesson-05.md) — Previous lesson: database
- [lesson-07](lesson-07.md) — Next lesson: deployment & APK
- [lesson-09](lesson-09.md) — Final: grant application (uses today's SMS integration)
- *lesson-08-production-deployment* — Online English Lesson 8 (APK source material)
- *near-offline-lesson-03* — NEAR course equivalent (agent deployment lesson)

## Result

After this lesson, each student has:
- Phantom installed and funded on their own Android phone, on devnet
- An EAS **development build** on the phone — the tool they'll develop with for the rest of the course
- A React Native + Expo mobile app for their hackathon product
- Mobile Wallet Adapter integrated: connect, disconnect, show address
- The Lesson 5 database wired into a real screen
- A real devnet transaction signed from their phone inside their own app
- Seed Vault researched, integration points added, status documented honestly (full testing needs a Solana phone)
- README documenting the Solana Mobile Stack integration
- Grant criterion #1 (mobile-first) demonstrably met, and criterion #2 (Solana Mobile Stack) met for Mobile Wallet Adapter with a credible, documented plan for Seed Vault — which is what grant reviewers actually expect from a team without a Seeker device
- First real user feedback collected
- Everything committed and pushed
