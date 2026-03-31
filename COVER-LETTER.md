# Vulcan X — New Platform Build: Cover Letter

**From:** Jamie Thomson, CEO
**To:** Dev Team
**Date:** 31 March 2026
**Deadline:** 5th April 2026 — live.

---

Team,

Here's the full brief for the Vulcan X platform revamp. Everything you need is in two places:

**Live prototype:** https://jamie323.github.io/vulcanx-prototype/
**Developer handoff doc:** https://github.com/jamie323/vulcanx-prototype/blob/main/DEVELOPER-HANDOFF.md

Click "Get Started" or "Connect Wallet" to see the full connected experience. Click through all 9 pages using the bar at the bottom. The onboarding tour will walk you through the key features automatically.

---

## What We're Building

One unified platform that replaces the current scattered setup (VulcanX exchange on one site, Agora on another, MyForge somewhere else, games linking out everywhere). The user connects their wallet once and everything is there — trading, games, NFTs, staking, chain tools, social, quests — all under one roof with a gamified XP system tying it all together.

The prototype has every page, every interaction, every flow mapped out. It's not a Figma mockup — it's a working interactive HTML demo with real animations, real data shapes, and a real AI assistant (plug in an OpenAI key and try it).

---

## What's Easy

Most pages are straightforward UI work — the prototype shows exactly what goes where:

- **Discover/Home** — dashboard widgets, price strips, quick actions
- **Games** — catalogue with cards, launcher modals, stats, **Sow & Seed** (land plots with growth/harvest), **Berserk Booster Packs** (4 tiers), **Leaderboards** (per-game + global XP)
- **Social** — activity feed, leaderboard, friends, competitions, **Referral system** (tiered fee sharing, invite links), **Governance polls** (active/closed proposals, voting power)
- **Quests** — daily/weekly/seasonal quest cards with progress bars
- **Profile** — user stats, badges, NFT showcase, **Cloud Wallet** (multi-token balances, PIN+2FA, deposit/withdraw), **MyForge Identity** (linked accounts, identity score, onboarding checklist)
- **Elysium tools** — block explorer, bridge, swap, wallets, faucet (existing tools, new UI)
- **Earn** — 6 tabs: Overview, **V-Drip** (lock PYR, Relic boosts), **Land Staking** (sow/level up), **ELY Bank** (3 fixed-term plans), **LP Farming**, **Reward History**
- **Trade** — 3 tabs: Spot (existing exchange), **Liquidity** (add/remove LP, pool positions), **Elysium Swap** (instant swaps with routing/slippage)
- **NFTs** — 6 tabs: Marketplace, **Auctions** (4 auction types, auto-bid), My Collection, **Cedalion Renting** (3 subscription tiers), **Activity** (event log), Create

These are all standard frontend work. The prototype gives you the exact layout, data structure, and interactions.

---

## What's Hard (The Three Big Ones)

### 1. VulcanX Exchange
The current exchange at vulcanx.exchange needs to be integrated into the Trade page. This means TradingView charts, WebSocket order book, the full order matching engine, and real market data. The auth model needs bridging — VulcanX uses email/password, the new app is wallet-first.

**Critical:** VulcanX's biggest USP is revenue sharing. Every fee goes back to users. This can't be buried in a settings page — it needs to be visible in the Earn section, the weekly PYR drop on the Discover dashboard, and the tier system. The prototype already scaffolds this, but the real revenue data needs to flow through.

### 2. Agora NFT Marketplace
The NFTs page now has 6 full tabs — marketplace, auctions (timed/open/fixed/batch with auto-bid), collection management, Cedalion NFT renting (3 subscription tiers), activity log, and minting. These need to wire to Agora's smart contracts and APIs. Collection data, floor prices, user holdings across chains, auction engine, rental subscription logic, and the mint-to-list flow all need real backends.

### 3. MyForge / Identity + Cloud Wallet
The hardest one. Currently everything is centralised on vulcanforged.com. We need to unify wallet-based identity with existing VF accounts, build a real XP tracking engine that listens to events from all services (trades, games, stakes, bridges, mints, quests), and make the tier system, badges, and leaderboard work with real data. The prototype now includes a full cloud wallet (multi-token balances, deposit/withdraw, PIN+2FA security, whitelist) and MyForge identity system (linked accounts, identity score out of 100, onboarding checklist with rewards).

The handoff doc has detailed breakdowns of each challenge.

---

## The Gamification Layer

This is what makes it different from every other exchange/platform. The XP and tier system (Bronze → Mythic) ties everything together:

- Every action earns XP
- Tiers unlock multipliers on weekly PYR rewards
- Daily Forge Strike keeps people coming back
- Quests create structured engagement paths
- The leaderboard creates competition
- The weekly PYR drop creates a recurring reason to participate

This isn't a nice-to-have. It's the core product differentiator. Build it properly.

---

## What I Expect

1. Open the prototype, click through every page, understand every interaction
2. Read the handoff doc end to end
3. Start with the easy pages to get momentum
4. Tackle the three hard integrations in parallel
5. Use AI to help — Claude, Copilot, whatever. No excuses about complexity
6. Neswulf will be checking in regularly
7. **Live by 5th April**

The prototype is the spec. If something isn't clear, ask. If something needs to change for technical reasons, flag it and propose an alternative — don't just skip it.

Let's go.

— Jamie
