---
title: "Solana Off-line Lesson 4: Solana Fundamentals — Wallets, Transactions, Tokens via MCP"
type: lesson
difficulty: intermediate
tags: [solana, offline, blockchain, wallets, transactions, spl-tokens, devnet, rpc, mcp]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 4
---

# Solana Off-line Lesson 4: Solana Fundamentals — Wallets, Transactions, Tokens via MCP

**Format:** Instructor-led classroom — screen sharing + hands-on practice
**Duration:** ~2 hours

## How This Lesson Works

Same flow: instructor explains → demonstrates → drops prompt in chat → students copy-paste and repeat → wait for all → questions → next section.

**Big idea of this lesson:** you don't write Solana code today. The **Solana MCP** (connected in Lesson 2) already knows how to do everything — you just ask. This is the whole philosophy of the course: *use tools that exist, don't rebuild them.*

---

## Prerequisites

From Lessons 1-3, every student must have:
1. ✅ Zed with DeepSeek connected
2. ✅ Solana MCP connected (Lesson 2) with a funded devnet keypair — **or** the fallback below
3. ✅ Phantom wallet on devnet
4. ✅ SPECIFICATION.md + PLAN.md for the hackathon project

> 🛟 **If the Solana MCP never connected in Lesson 2, you can still do every exercise today.** Paste this once at the start of the lesson and use the CLI wherever the lesson says "MCP":
>
> ```
> My Solana MCP isn't working. Set me up with the Solana CLI
> instead, for DEVNET only:
> 1. Install the Solana CLI for my OS: [Windows / Mac / Linux]
> 2. Configure it for devnet
> 3. Create a fresh keypair for practice (NOT my Phantom wallet),
>    show me the public address, and store it in the default
>    location
> 4. Fund it and show the balance
> 5. Then tell me the CLI equivalent of each of these, so I can
>    follow the lesson: check balance, request an airdrop,
>    transfer SOL, create an SPL token
> Explain every command before running it.
> ```
>
> Everything else in the lesson works the same — you just say "using the Solana CLI" instead of "using the Solana MCP".

---

## Part 1: What Is Solana — in One Page

You don't need a computer science degree. You need this mental model:

| Concept | Plain-Language Meaning | Analogy |
|---------|------------------------|---------|
| **Blockchain** | A public notebook where every entry is permanent and everyone has a copy | A village ledger that can't be erased |
| **Solana** | A blockchain built for speed and cheap fees (fractions of a cent) | The fast highway, not the dirt road |
| **Account** | Everything on Solana is an account: your wallet, a token, a program | Bank accounts, but every file is also an account |
| **SOL** | Solana's native coin — pays for transactions | The fuel + the money |
| **Lamport** | 0.000000001 SOL (SOL has 9 decimals) | Cents to a dollar |
| **Transaction** | A signed instruction bundle sent to the network | A signed check |
| **Signature** | Your private key approving the transaction | Your signature on the check |
| **Devnet** | Solana's free test network — fake SOL, zero risk | Monopoly money |
| **Mainnet** | The real network with real money | Real money — we never touch it in this course |
| **RPC** | A doorway through which apps talk to the blockchain | The bank clerk at the counter |

**The two kinds of accounts you'll meet:**
- **Wallet accounts** (you, a classmate) — hold SOL and tokens
- **Data/program accounts** (a token's registry, a smart contract) — hold data or code

**Chat drop:** Quiz your neighbor: "What's the difference between SOL and a lamport? What does RPC mean in one sentence?"

---

## Part 2: Wallets, Keys, and the Golden Rules

In Lesson 2, the Solana MCP got its **own devnet keypair** — separate from your Phantom wallet. That's on purpose:

| Key | Where it lives | What it's for |
|-----|---------------|---------------|
| **Phantom keys** | Inside Phantom (encrypted) | Your personal wallet — you sign manually |
| **MCP keypair** | Zed's MCP config | AI's practice wallet — AI signs for you |

**The golden rules:**

| Rule | Why |
|------|-----|
| Seed phrase / private key NEVER in code, chat, or GitHub | Anyone with it owns your money |
| Devnet keys = practice. Mainnet keys = money. | Never reuse practice keys for real money |
| In apps: users sign with their wallet (never type keys into an app) | This is what Mobile Wallet Adapter does in Lesson 6 |

**Chat drop:** Discussion: which of these can you post publicly — public key, private key, seed phrase, transaction signature? (Answer: public key and transaction signature.)

---

## Part 3: SPL Tokens — Money You Can Create

**SPL** is Solana's token standard — a recipe for making your own currency. USDC on Solana is an SPL token. A game's points? An SPL token. Our hackathon apps will very likely use them.

| Token term | Meaning |
|-----------|---------|
| **Mint** | The "token factory" account — defines name, symbol, decimals |
| **Token account** | A wallet's holding of a specific token |
| **Supply** | How many tokens exist |

**And here's the good news:** the Solana MCP has a `DEPLOY_TOKEN` tool. Creating a token is one sentence away. We'll do it in Part 6.

**Chat drop:** Ask AI: `What is an SPL token? Explain "mint", "token account", and "supply" with an everyday analogy. Keep it under 10 lines.`

---

## Part 4: Practice 1 — Check Balance and Get Funds (via MCP)

In Lesson 2, AI funded the MCP keypair. Let's verify — and top up if needed. In Zed:

```
Using the Solana MCP:

1. Check the balance of the MCP wallet (BALANCE tool) and show me
   the wallet address
2. If the balance is below 0.5 SOL, request devnet funds
   (REQUEST_FUNDS tool). Public devnet airdrops are heavily
   rate-limited, so if it fails: don't retry in a loop — tell me,
   and give me the faucet.solana.com link with my address ready
   to paste. Then confirm the new balance
3. Show me the address on the devnet explorer
   (explorer.solana.com or solscan.io) — give me the link
```

**You just did this:** checked a real blockchain account and made sure it has money — by asking in plain English.

**Chat drop:** Paste the prompt → screenshot the balance → open the explorer link.

---

## Part 5: Practice 2 — Send SOL to a Classmate (via MCP)

Exchange **MCP wallet addresses** with your neighbor. In Zed:

```
Using the Solana MCP TRANSFER tool:

Send 0.25 SOL from my MCP wallet to my classmate's address:
[CLASSMATE'S ADDRESS]

Before sending, show me what you're about to do and ask for my
confirmation. After sending: show the transaction signature,
the explorer link, and the new balance of both wallets.
```

**You just sent money on a blockchain** — with one paragraph of English. Open the explorer link: there's your transaction, permanent and public.

**Chat drop:** Paste the prompt (with your neighbor's address) → confirm → open the explorer link → show your neighbor. Confirm they received it.

---

## Part 6: Practice 3 — Create Your Own SPL Token (via MCP)

Time to become a token creator. In Zed:

```
Using the Solana MCP DEPLOY_TOKEN tool:

Create a new SPL token on DEVNET.

1. Name: [YOUR NAME]COIN, symbol: e.g. [ABC]
2. Deploy it from my MCP wallet
3. Show me the mint address
4. Tell me how to see it on the devnet explorer (give me the link)
5. If the tool can also mint an initial supply to my wallet — do
   that too and show the balance
```

**You now own a token.** This exact flow — create token, mint, transfer — powers countless hackathon projects (points, rewards, collectibles).

**Chat drop:** Paste the prompt → find your mint address in the explorer → post your token's name in the group chat.

---

## Part 7: Where Does This Fit Your Hackathon Project?

Open your SPECIFICATION.md. In Zed:

```
Read SPECIFICATION.md and PLAN.md.

For the Solana integration parts: list exactly which on-chain
actions my product needs (transfers? an SPL token? reading
balances? something else?).

For each, say whether the Solana MCP tools can do it, or whether
it will need app-side code later (Lesson 6 — Mobile Wallet
Adapter). Then write the result into PLAN.md as the "on-chain
core" note at the top of Phase 3, and flag any Phase 4 feature
that secretly needs on-chain work I haven't planned for.

Don't change product code yet — just update the plan and explain
in 5 lines what the on-chain core of my product is.
```

**Chat drop:** Paste the prompt. Read AI's explanation. This is your product's blockchain core, now concrete instead of theoretical.

---

## Homework

1. Ask AI (via Solana MCP) to send the 0.25 SOL back to your neighbor — settle the debt exactly, and check both balances afterwards
2. Ask AI: what's the transaction fee for a simple SOL transfer, and how do I see it? (Open your transfer in the explorer and find the fee field.) Compare it to a bank transfer fee
3. Explore your wallet on the explorer: how many transactions do you have now?
4. Look at the Solana MCP tool list — which tool do you wish you had for YOUR product? (Don't worry if it's missing — app code in Lesson 6 covers that)
5. Group chat: one sentence on how your hackathon product uses the blockchain

---

## Troubleshooting

### Solana MCP Says "Not Enough SOL"

```
The MCP says insufficient funds. Use REQUEST_FUNDS or guide me to
the devnet faucet with my MCP wallet address, then retry.
```

### Transfer Fails / Timeout

```
The transfer failed with: [paste error]. Diagnose it. If it's a
network/rate issue, retry once. If it's a balance issue, top up
first.
```

### DEPLOY_TOKEN Failed

```
DEPLOY_TOKEN failed with: [paste error]. Diagnose it. Check the
wallet balance (token creation needs a bit of SOL for rent) and
retry with a valid name/symbol.
```

### MCP Tools Don't Appear in Zed

```
The Solana MCP tools aren't available. Tell me to open Zed's
settings with Cmd/Ctrl+, then check the solana-mcp entry there,
restart the MCP connection, and verify with the BALANCE tool.
If it still fails, switch me to the Solana CLI fallback instead —
don't keep debugging past 10 minutes.
```

### I Want to See the Raw Transaction

Ask AI: `Show me the last transaction of my MCP wallet on the explorer and explain each field in simple terms.`

---

## Related Materials

- [lesson-03](lesson-03.md) — Previous lesson: Product Owner + AI team
- [lesson-05](lesson-05.md) — Next lesson: database (SupaBase, MCP already connected)
- [lesson-06](lesson-06.md) — Later: same actions inside your own mobile app
- *lesson-04-blockchain-web3* — Crypto course blockchain lesson (similar method, different chain)
- *near-offline-lesson-05* — NEAR course equivalent (MCP + blockchain practice)

## Result

After this lesson, each student has:
- A working mental model of Solana: accounts, SOL/lamports, transactions, SPL tokens, devnet, RPC
- Three blockchain operations done **via MCP, in plain English**: balance check + funding, a real transfer to a classmate, and their own SPL token deployed on devnet
- A transaction on the devnet explorer with their MCP wallet's signature
- Their own token mint visible on the explorer
- The security golden rules internalized
- PLAN.md updated with the concrete on-chain core of their product (top of Phase 3)
- Zero code written by hand — tools did the work (MCP, or the Solana CLI if MCP was down)
