---
title: "Solana Off-line Lesson 7: Deployment & APK — Your App Leaves the Laptop"
type: lesson
difficulty: intermediate
tags: [solana, offline, deployment, apk, eas-build, android, vercel, flyio, production]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 7
---

# Solana Off-line Lesson 7: Deployment & APK — Your App Leaves the Laptop

**Format:** Instructor-led classroom — screen sharing + hands-on practice
**Duration:** ~2.5 hours (including a supervised build sprint while the APK compiles)

## How This Lesson Works

Same flow: instructor explains → demonstrates → drops prompt in chat → students copy-paste and repeat → wait for all → questions → next section.

**Today's shape:** we start the APK build early, then spend the wait building your actual product. Deployment is mostly waiting; we refuse to waste it.

---

## Prerequisites

From Lessons 1-6, every student must have:
1. ✅ Zed with DeepSeek connected
2. ✅ Mobile app running in the **EAS development build** on their phone (Lesson 6)
3. ✅ EAS CLI installed and `eas login` working (Lesson 6)
4. ✅ Project on GitHub
5. ✅ An Android phone with "install from unknown sources" allowed

---

## Part 1: What "Deployed" Means for Your Product

Right now your product lives in two fragile places:

| Now | After this lesson |
|-----|-------------------|
| App runs only in your development build (needs your laptop running the dev server) | App is a standalone **APK** — installs on any Android phone, no laptop |
| Backend (if any) runs on your machine | Backend runs 24/7 in the cloud |
| Demo needs you present with your laptop | Demo is one tap on any phone — perfect for hackathon judges |

**What is an APK?** An installer file, like `.exe` for Windows. You send it to a phone, open it — the app installs. No Google Play review, free, instant. This is exactly what hackathon judges and grant reviewers can install in 30 seconds.

**Our deployment targets:**

| Piece | Where it goes | Tool |
|-------|---------------|------|
| Android app | APK file → any phone | **EAS Build** (Expo's cloud build service) |
| Backend (**only if** your product needs one) | Cloud server | **fly.io** — usage-based, not free. Budget a few dollars a month |
| Web landing page (optional) | Public URL | **Vercel** or GitHub Pages |

**Chat drop:** Neighbor check: what's the difference between running in Expo Go and installing an APK? Which one would a hackathon judge prefer and why?

---

## Part 2: Build the APK with EAS Build

You already used EAS in Lesson 6 for the **development** build. Today we run the same machine with a different profile:

| Profile | Produces | Needs your laptop? | For whom |
|---------|----------|--------------------|----------|
| `development` (Lesson 6) | Dev client APK | Yes — connects to your dev server | You, while building |
| `preview` (today) | **Standalone APK** | No — the code is baked in | Judges, users, your mum |

In Zed:

```
Build a standalone APK for my Expo app in the "mobile" folder.

I already have the EAS CLI installed and I'm logged in, and
eas.json exists from the development build in Lesson 6.

Steps:
1. Check eas.json has a "preview" profile that produces an
   installable APK (buildType apk, distribution internal).
   Show me the change before making it
2. Make sure anything the app needs at runtime is available in
   the build — my Supabase keys are in .env, which is NOT
   bundled. Tell me how Expo handles this (EXPO_PUBLIC_ vars /
   EAS environment variables) and set it up correctly
3. Run: eas build -p android --profile preview
4. Give me the link to watch it, and tell me the expected wait

Explain each step before running it.
```

**Start the build now, then go straight to Part 3.** On Expo's free tier you get 15 Android builds a month, one at a time, on a low-priority queue — Expo documents waits of **90+ minutes** at peak, with a 45-minute build timeout. That is exactly why Part 3 exists.

> ⚠️ **Step 2 is the one that bites.** In the dev build, your laptop supplies the environment; in a standalone APK it doesn't. A student whose app "worked yesterday" and shows a blank screen after install has almost always skipped this. Don't let AI skip it either.

**Chat drop:** Paste the prompt → start the build → note the link → move to Part 3. Download the APK when it finishes; Part 6 installs it.

---

## Part 3: Build Sprint — Your Product, Supervised (40 minutes)

The build is compiling. This is the only block of *supervised* product time in the whole course — use it on **Phase 4**, your core features.

Round the room first: each student says which Phase 4 task they're doing right now. The instructor walks between desks; this is where the questions that never get asked in a group finally get asked.

In Zed:

```
Read TEAM.md, SPECIFICATION.md and PLAN.md.

I have about 40 minutes. Pick the highest-value unfinished
Phase 4 task that can realistically be completed in that time —
if the starred one is too big, split it and do the first slice.

Then work it the normal way: build, test on my phone, commit,
mark it done in PLAN.md. Tell me at the halfway point whether
we'll finish, and cut scope rather than leaving it broken.

End with: what's done, what's next, and what I should do
tonight.
```

**Instructor:** don't fill this time with theory. Sit with the two or three students whose Phase 4 is emptiest — they are the ones who will otherwise have nothing to demo in Lesson 8.

**Chat drop:** Paste the prompt. Work. When someone's build link goes green, they check the APK and come back to building.

---

## Part 4: Deploy the Backend (if Your Product Needs One)

Does your product have a backend (a server for the database logic, bot, or API)? If you're not sure — ask AI:

```
Read SPECIFICATION.md and PLAN.md. Does my product need a backend
server, or is it mobile + SupaBase only? Explain in 3 sentences.
If it needs one, say exactly what it does that SupaBase can't.
```

**Most products in this course do not need a backend.** Supabase already gives you a database, authentication and an API. If AI says you need a server, make it justify the answer — a backend you don't need costs money and adds a thing that can break during your demo.

**If a backend really is needed**, deploy it to fly.io. Note that fly.io is **not free**: it bills by usage and asks for a card. A tiny always-on machine runs a few dollars a month. In Zed:

```
Deploy my backend to fly.io.

Stack: [Node.js / Python / whatever AI chose]
Database: SupaBase (already exists — no new DB needed)

Steps:
1. Install flyctl if not installed
2. fly auth login — guide me through it
3. fly launch — configure a minimal app, no database
4. Transfer my .env secrets with fly secrets set KEY=value
   (I'll paste values when you ask)
5. fly deploy
6. Give me the public URL and test one endpoint

Explain each step. If you need my input — tell me what to press.
```

**If no backend is needed** — congratulations, simpler architecture. Skip to Part 4, and let AI add a one-page web landing for your app instead:

```
My product is mobile-only. Create a simple one-page landing site
for it (name, one-line pitch, screenshot placeholder, link to the
APK) and deploy it to Vercel or GitHub Pages. Give me the URL.
```

**Chat drop:** Paste the backend prompt (or the landing page prompt). Get your public URL.

---

## Part 5: Secrets, Environment, and the Production Checklist

Deployment is where secrets leak. Run the security pass — in Zed:

```
Run the security-and-hardening skill on my project.

Check specifically:
1. No real secrets in any committed file (search for keys, .env
   content, private key material)
2. .env is in .gitignore
3. Backend reads secrets from fly secrets / environment, not files
4. SupaBase: anon key only in the app; service_role nowhere in client code
5. The APK doesn't bundle anything secret (EAS env vars if needed)

Fix anything you find, then commit with a clear message.
```

**Chat drop:** Paste the prompt. Review AI's findings — even "nothing found" is a result worth reporting.

---

## Part 6: Install the APK on Your Phone

The moment of truth:

1. Transfer the APK to your phone (send it to yourself in Telegram, or via USB)
2. Open the file on the phone
3. Android asks to allow installs from unknown sources → allow (for your file manager/Telegram)
4. The app installs — find its icon
5. Open it **without the laptop** → connect wallet → sign a transaction

If it crashes:

```
The APK installed, but the app crashes on launch / a feature
doesn't work. Here's what happens: [describe].
Get the logs if possible and fix it. Rebuild if needed.
```

**Chat drop:** Install → open → connect wallet → sign a self-transfer → screenshot. Post the screenshot in the group chat: your product, standalone, on real hardware.

---

## Part 7: Update the Plan and Ship

In Zed:

```
Read TEAM.md and PLAN.md.

1. Mark Phase 5 (packaging & deployment) tasks as done, plus any
   Phase 4 tasks finished in today's build sprint
2. Do NOT touch Phase 6 — that's the hackathon submission, and
   it's next lesson's work
3. Update README.md: add the APK download/build instructions and
   the public URLs
4. Commit everything with clear messages
5. Push to GitHub (my explicit request)
6. 5-line report: what's deployed, where, what Phase 4 tasks
   remain, and what I should finish before Lesson 8
```

**Chat drop:** Paste the prompt. Open your GitHub — your repo now documents a deployable product.

---

## Homework

1. Send the APK to 2 friends (not classmates) — can they install and use it without your help? Collect their exact feedback, **word for word**. Lesson 8 turns these quotes into submission material, and paraphrases are worthless there
2. Ask AI to add an app icon and splash screen (expo assets) — your app should look like a product, not a template
3. If you deployed a landing page — add a real screenshot of your app to it
4. **Product Build Track — last full week.** Finish the ⭐ Phase 4 feature end to end. After Lesson 8 the work turns to pitching, not building
5. Push all changes
6. Group chat: post your landing URL or a photo of the app icon on your home screen

---

## Troubleshooting

### EAS Build Fails

```
EAS Build failed with: [paste error]. Diagnose it. Check eas.json,
the preview profile, and app.json config. Fix and rebuild.
```

### APK Won't Install ("App not installed")

```
The APK won't install — "App not installed" error. Diagnose:
is it signed? Does it clash with the development build already on
my phone (same package name, different signature)? Guide me
through fixing it — e.g. uninstall the dev build first, or give
the preview build its own package name so both can coexist.
```

### App Crashes on Launch After Install

```
The APK installs but crashes on launch. How do I see the crash
logs (adb logcat or otherwise)? Walk me through getting the error
and fixing it.
```

### fly.io Deploy Fails

```
fly deploy failed with: [paste error]. Diagnose and fix. Check
the Dockerfile/Procfile matches my stack and that secrets are set.
```

### Google Play Warning About Unknown Sources

That's expected for APKs outside the store. For the hackathon and grants, direct APK install is fine. Publishing to Google Play is a later step — ask AI to explain it when you're ready.

---

## Related Materials

- [lesson-06](lesson-06.md) — Previous lesson: Solana Mobile app
- [lesson-08](lesson-08.md) — Next lesson: hackathon submission
- *lesson-08-production-deployment* — Online English Lesson 8 (source material)
- *off-line-lesson-03* — Original off-line deployment lesson (fly.io path)

## Result

After this lesson, each student has:
- A real APK built with EAS Build, installed and working on their phone — no laptop needed
- Either a backend on fly.io **or** a documented decision that they don't need one (plus a landing page on Vercel/GitHub Pages)
- Secrets verified: .env gitignored, production secrets in platform vaults
- A security pass with findings fixed
- README documenting build and deployment
- PLAN.md Phase 5 complete, Phase 4 advanced by a supervised sprint
- The product ready to be packaged (Phase 6, next lesson)
