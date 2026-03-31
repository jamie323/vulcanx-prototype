# Prototype Update — XP Meeting Feedback Addressed

**From:** Jamie
**Date:** 31 March 2026

---

Team,

Good discussion. I've updated the prototype based on your meeting feedback. Here's what changed and where I stand on the open questions.

---

## What Changed in the Prototype

**1. XP is now quest-based, not per-action.**
Kristof was right — rewarding XP per action invites bots and grinders. The prototype no longer shows "+15 XP per match" anywhere. Every XP source is now gated through daily/weekly/monthly quest boards with caps. A casual player doing 1-2 hours earns similar XP to someone grinding 10 hours. This is visible on every game card, every earn pool, and every page tag.

**2. Tiers expanded from 5 to 10, stretched to 100K XP.**
Neil's suggestion implemented. New tiers: Bronze (0) → Silver (2K) → Gold (5K) → Platinum (10K) → Diamond (20K) → Master (35K) → Grandmaster (55K) → Legend (75K) → Mythic (100K) → hidden Titan tier. Micro-progression within each tier via the XP bar. The full tier table with multipliers is now visible on the Quests page so users always see what's ahead.

**3. Trading XP weighted 2x higher than gaming.**
Trading and LP quests are explicitly marked "Trading weighted 2x" in the prototype. Daily trade quest = 40 XP vs daily game quest = 15 XP. Weekly LP quest = 150 XP vs weekly game quest = 60 XP. This incentivises trading volume (which drives revenue) while still rewarding gameplay. Weighting breakdown is shown on the Quests page.

---

## Answers to Your Open Questions

**Bots & exploitation:** Quest caps + daily limits handle this. We'll also reserve the right in T&Cs to remove exploited XP. Trading bots are less of a concern — they bring volume and liquidity. Game bots are mitigated by capped quest XP, not per-action rewards.

**5,000 PYR weekly pool:** I'm happy with this number. It's distributed proportionally by XP earned that week, with tier multipliers (Platinum 1.3x, Diamond 1.5x, up to Mythic 2.5x). The pool stays fixed — more participants just means smaller individual shares, so it's sustainable.

**Wallet abstraction / Web2 onboarding:** The prototype already has a MyForge Identity flow on the Profile page — create account with email first, link wallet later, optional KYC. Cloud wallet (custodial, PIN+2FA) is built in for easy onboarding. This covers OG Warrior's suggestion without forcing MetaMask on day one.

**Game XP integration:** Game-side XP stays unchanged. It gets weighted/normalised when it pulls into the VX app. No need to touch existing game XP systems or risk breaking land staking dependencies. This is documented in the AI guide context.

**Berserk / game development:** Waiting 2 days on PBT testing. Will confirm direction on Berserk PTR and the HTML games (runner, tower defense) separately. Kristof — enjoy your trip, nothing urgent game-side until I confirm.

---

## What's Next

- Review the updated prototype: **https://jamie323.github.io/vulcanx-prototype**
- Look at the Quests page specifically — tier table, weighting breakdown, quest rewards
- Neil + Dionisis: continue on Stage 2 flows
- Farhan / Vaival: the XP framework in the prototype is now your spec for implementation
- Full handoff doc: **https://github.com/jamie323/vulcanx-prototype/blob/main/DEVELOPER-HANDOFF.md**

5th April target stands. Let's go.

— Jamie
