# Vulcan X Super-App — Developer Handoff Guide

**Prototype:** `vulcanx-prototype-v4.html` (single HTML file, ~4,800 lines)
**Deadline:** 5th April — no excuses. AI is there to help.
**Oversight:** Neswulf will stay on top of this.

---

## What This Is

A fully interactive wireframe prototype for the new Vulcan X unified platform — the "GameFi super-app" that brings VulcanX exchange, Agora NFT marketplace, MyForge, Elysium chain tools, gaming, social, and a gamified XP/tier system under one roof. Every page, every interaction, every flow is mapped out. Your job is to bring it to life.

---

## The 9 Pages

| Page | What It Does |
|------|-------------|
| **Discover (Home)** | Two states: disconnected (hero + value prop) and connected (personalised dashboard with XP, streak, quests, prices, games, competitions, activity feed) |
| **Trade** | Full exchange UI — market data bar, interactive chart, vertical order book, Spot buy/sell panel (Market/Limit/Stop Market), all-markets table |
| **Play (Games)** | Game catalogue with hero carousel, game cards, stats, launcher modals, article previews |
| **Earn** | Staking pools (PYR, Lava Pool, V-Drip, ELY/USDT LP) with APY, TVL, user positions, XP rewards |
| **NFTs (Agora)** | 3 tabs: Marketplace (collections, listings), My Collection (portfolio, list/delist), Create (mint form with live preview) |
| **Social** | Activity feed, competitions, friends list, XP leaderboard with weekly PYR reward pool |
| **Elysium Chain** | Block explorer, bridge, DEX swap, cloud wallet, Fortuna wallet, faucet — 6 tool panels |
| **Quests** | Daily/weekly/seasonal chapter quests with progress bars, secret quests, XP summary |
| **Profile** | User identity, XP breakdown, badges, NFT showcase, season progress, shareable profile card |

---

## Key Features Built Into the Prototype

### Gamification Layer (XP & Tiers)
- **5-tier system:** Bronze (0) → Silver (2K) → Gold (8K) → Diamond (17K) → Mythic (30K)
- XP earned from every action: trading, gaming, staking, quests, bridging, minting
- Persistent XP strip under nav (shows progress bar)
- Weekly PYR reward pool (5,000 PYR) distributed to top XP earners every Tuesday
- Tier multipliers on rewards (Gold = 1.5x, Diamond = 2x)
- Achievement popups with floating XP animations on key actions
- Daily Forge Strike — 7-day streak visualisation with escalating bonuses (+50 XP at 7d, +150 at 14d, +500 at 30d)

### Onboarding Tour
- 5-step guided walkthrough that auto-triggers after wallet connection
- Spotlight cutouts with backdrop dimming, smooth transitions between steps
- Steps: Welcome → XP Progress → Daily Streak → Quick Dashboard → AI Guide
- Skip option at every step

### AI Guide (Proof of Concept)
- Context-aware AI assistant in a left-side drawer
- OpenAI GPT-4o-mini integration with SSE streaming (bring your own API key, session-only)
- Fallback mock responses per page when no API key
- Dynamic context assembly: injects current page, wallet state, XP, quests, prices into every prompt
- Suggested prompt chips that change per page
- Full system prompt with Vulcan X knowledge base

### Live Activity Toasts
- Periodic ecosystem event notifications (NFT sales, tier milestones, price breaks, tournaments)
- 12 rotating events, random 12-20s interval
- Stacked bottom-left, max 3 visible, auto-dismiss

### Chat Sidebar
- Global + page-contextual + party channels
- Per-page message sets with emoji reactions and typing indicators
- Context tab label updates on every page change

### Interactive Trade Chart
- Canvas-rendered with procedural price data
- 5 timeframes (1H/4H/1D/1W/1M) with animated transitions
- Crosshair + tooltip on hover showing price and time
- Gradient fill, price labels, end-of-line pulse dot

### Search
- Global search dropdown with real-time filtering
- Sections: Quick Actions, Tokens, Games, Collections

### Responsive / Mobile
- Full mobile layout at ≤840px with bottom nav bar (5 items)
- Drawers transform from side panels to bottom sheets
- All grids collapse to single column
- Touch-friendly tap targets

---

## The Three Hard Integration Challenges

### 1. VulcanX Exchange Integration
**Current state:** VulcanX is live at vulcanx.exchange — centralised exchange with TradingView charts, WebSocket order book, Market/Limit/Stop Market orders, all pairs against USDC.

**What needs to happen:**
- Replace the prototype's canvas chart with TradingView widget (already used on vulcanx.exchange)
- Wire up real WebSocket order book feed
- Connect the Spot buy/sell panel to the exchange's order matching engine
- Pull real market data for the top bar (last price, 24h change, volume, high, low)
- Real pairs list from the exchange API (currently: V, PYR, BTC, ETH, ELY, BNB, XRP, POL, WN — all /USDC)
- Auth flow — VulcanX currently uses email/password login; the new app uses wallet connect. Need to bridge these or unify auth
- Fee structure display: VulcanX shares revenue with users — this USP needs to be prominently surfaced
- **Revenue share info**: Make sure the "Your Exchange, Your Rules" messaging and fee-sharing mechanics are visible without being buried. The prototype's Earn page and the weekly PYR drop are designed for this — the Discover connected dashboard shows estimated PYR share. The key is making revenue share feel native to the XP/tier system, not a separate bolt-on

**Key files on vulcanx.exchange to study:** `/exchange` (spot trading), `/market-data` (markets overview), `/buy-crypto`, `/settings/my-journey` (gamification)

### 2. Agora NFT Marketplace Integration
**Current state:** Agora is the existing NFT marketplace running on Vulcan Forged infrastructure.

**What needs to happen:**
- NFT listing/buying/selling flow wired to Agora's smart contracts
- Collection data from Agora API (Vulcanites, VulcanVerse Land, Berserk Cards, community collections)
- Mint flow connected to Elysium chain (the prototype has a full mint form with name, description, chain, supply, royalties, properties)
- "My Collection" tab needs to pull user's actual NFT holdings across chains
- Floor prices, volume data, trending collections from Agora backend
- Royalty enforcement (prototype shows 2-10% range)
- Image/media hosting for NFT assets
- The Create tab should maintain the live preview experience from the prototype

### 3. MyForge / Profile / Identity Integration
**Current state:** MyForge is currently centralised on vulcanforged.com — user profiles, game accounts, assets, all tied to VF accounts.

**What needs to happen:**
- Unify wallet-based identity with existing VF account system
- Profile data: XP history, game stats, NFT ownership, trade volume, badges — currently scattered across multiple backends
- XP calculation engine — the prototype defines XP rewards per action but needs a real backend to track and calculate
- Tier system needs persistent storage and real-time updates
- Badges/achievements system needs event triggers from all services (trading, gaming, staking, bridging, minting)
- Friends list and social graph — currently no unified social layer
- Leaderboard with real ranked data
- Quest completion tracking across multiple services (did they actually make a trade? play a game? stake tokens?)
- Daily Forge Strike streak needs a reliable daily check-in mechanism
- "Share Profile" card generation (the prototype triggers an achievement; real version should generate an image)

---

## Everything Else (Self-Explanatory But Listed for Completeness)

### Elysium Chain Tools
- **Block Explorer**: search by block/tx/address, display block table (prototype has mock data)
- **Bridge**: from/to chain selector, asset picker, amount input — wire to existing bridge contracts
- **DEX Swap**: token pair swap UI — wire to Elysium DEX contracts
- **Cloud Wallet**: custodial wallet overview
- **Fortuna Wallet**: portfolio viewer
- **Faucet**: test LAVA claim (existing faucet endpoint)

### Earn / Staking
- 4 pool types in prototype: PYR Staking (single-sided), Lava Pool (LP), V-Drip (revenue share), ELY/USDT Pool
- Each needs: deposit/withdraw flow, real APY calculation, TVL from contracts, user position tracking
- V-Drip is the key VulcanX revenue share mechanism — already live at vdrip.vulcanforged.com

### Social / Leaderboard
- Activity feed: aggregate events from all services (trades, games, NFT sales, tier changes)
- Competitions: tournament brackets, trading volume sprints, XP races
- Friends: add/remove, online status, party invites
- Leaderboard: ranked by XP, shows estimated PYR reward share

### Quests
- Daily quests: reset timer, completion detection from backend events
- Weekly quests: same but weekly reset
- Seasonal chapters: multi-step quest chains with lore, gated progression
- Secret quests: hidden triggers (e.g., bridge + swap on same day = +100 XP)

---

## Design System

### Colours (CSS variables, all defined in `:root`)
- Background: 5 levels from `--bg-primary` (#0a0b0f) to `--bg-hover` (#1e2130)
- Accent: `--accent` (#ff9d2e) — forge orange, used for all CTAs and highlights
- Semantic: green (#00c48c), red (#ff4d6a), blue (#4da2ff), purple (#a855f7)
- Elysium: `--elysium-purple` (#7c3aed)
- XP tiers: bronze (#cd7f32), silver (#c0c0c0), gold (#ffd700), diamond (#b9f2ff), mythic (#ff6ec7)

### Typography
- Font: Archivo (Google Fonts), weights 400-900
- Fallback: -apple-system, BlinkMacSystemFont, Inter, sans-serif

### Spacing & Radius
- Border radius: 8px (small), 12px (default), 16px (large)
- Nav height: 64px
- Banner height: 36px
- Chat width: 320px

### Responsive Breakpoints
- ≤1180px: simplified layout, chat doesn't shift page
- ≤840px: mobile mode — bottom nav, drawers become bottom sheets, single-column grids
- ≤560px: extra-small tweaks (banner font, achievement width)

---

## Animations to Preserve

These make the app feel alive — don't skip them:

1. **Achievement popups** — scale-in with trophy icon, auto-dismiss after 5s
2. **Floating XP numbers** — rise and fade on wallet button after key actions
3. **Daily Forge Strike flames** — staggered pop-in animation per day
4. **Chat typing indicator** — bouncing dots
5. **Toast slide-in** — spring cubic-bezier from left
6. **Card hover lifts** — subtle translateY(-2px) with shadow increase
7. **Chart timeframe transitions** — smooth interpolation between data sets
8. **Tour spotlight transitions** — clip-path morph between targets
9. **Onboarding tour** — the whole 5-step flow with backdrop cutouts
10. **XP bar transitions** — smooth width changes on progress updates

---

## Tech Recommendations

The prototype is a single HTML file. For production:

- **Framework**: Next.js or similar (SSR for SEO on public pages, SPA for logged-in experience)
- **State**: Wallet connection via wagmi/viem, global state for XP/tier/user data
- **Real-time**: WebSockets for order book, price feeds, activity feed, chat
- **Charts**: TradingView widget (already used on vulcanx.exchange)
- **Auth**: Wallet connect (primary) with VulcanX account linking for exchange features
- **XP Backend**: Event-driven — every qualifying action emits an event, XP service aggregates and calculates tier
- **AI Guide**: OpenAI API with context injection — the prototype's system prompt and context assembly function are production-ready patterns

---

## File Location

```
/Users/jamiethomson/VulcanForged/wireframes/vulcanx-prototype-v4.html
```

Open it with `python3 -m http.server 8090` from that directory, then hit `localhost:8090/vulcanx-prototype-v4.html`.

Click "Connect Wallet" or "Get Started" to see the full connected experience. The onboarding tour will auto-start. Click through all 9 pages via the bottom prototype bar.

---

**Jamie / Neswulf will be checking in. 5th April. Get it done.**
