# EnerQi ($ENQI) Whitepaper

**Version 1.0 — March 2026**

> _Bridging 3,000 years of Chinese metaphysics with Web3 infrastructure._

***

## Table of Contents

1. [Abstract](ENQI_Whitepaper_v1.md#1-abstract)
2. [The Problem](ENQI_Whitepaper_v1.md#2-the-problem)
3. [The Solution — EnerQi Platform](ENQI_Whitepaper_v1.md#3-the-solution--enerqi-platform)
4. [BaZi Engine — Technical Architecture](ENQI_Whitepaper_v1.md#4-bazi-engine--technical-architecture)
5. [Feature Overview](ENQI_Whitepaper_v1.md#5-feature-overview)
6. [$ENQI Token](ENQI_Whitepaper_v1.md#6-enqi-token)
7. [Access & Tier System](ENQI_Whitepaper_v1.md#7-access--tier-system)
8. [On-Chain Mechanics](ENQI_Whitepaper_v1.md#8-on-chain-mechanics)
9. [Multi-Channel Architecture](ENQI_Whitepaper_v1.md#9-multi-channel-architecture)
10. [AI Shi Fu — Intelligent Advisory Layer](ENQI_Whitepaper_v1.md#10-ai-shi-fu--intelligent-advisory-layer)
11. [Security & Privacy](ENQI_Whitepaper_v1.md#11-security--privacy)
12. [Roadmap](ENQI_Whitepaper_v1.md#12-roadmap)
13. [Appendix A — BaZi Engine Audit Report (100/100)](ENQI_Whitepaper_v1.md#13-appendix-a--bazi-engine-audit-report)

***

## 1. Abstract

EnerQi is a Web3-native metaphysics platform that brings the ancient Chinese science of Four Pillars of Destiny (BaZi, 八字) onto the blockchain. Built on the Shido Network, EnerQi combines a production-grade classical BaZi calculation engine — independently audited at **100/100** against classical Zi Ping standards — with decentralized identity, on-chain staking, token-gated access, and an AI-powered advisory system.

The $ENQI utility token (ERC-20, Shido Network) powers the entire ecosystem: staking for tiered feature access, pay-per-use unlocks, subscription plans, the Wishing Well lottery, and the Sacred Offering deflationary burn mechanic.

EnerQi is the most technically accurate and feature-rich metaphysics dApp in existence. Every calculation is traceable to classical source texts. Every score is reproducible. Every payment is verified on-chain.

***

## 2. The Problem

### 2.1 — Inaccurate Engines

The overwhelming majority of BaZi applications — web, mobile, and desktop — contain fundamental calculation errors that produce incorrect readings:

* **Missing True Solar Time correction.** A birth at 23:30 in Kuala Lumpur (UTC+8) is not the same solar hour as 23:30 in Beijing (also UTC+8 but different longitude). Most apps ignore this, placing users in the wrong hour pillar.
* **No Tiao Hou (Climate Regulation).** The classical system for overriding Wang Shuai strength based on seasonal temperature/moisture needs. Without it, a Fire Day Master born in Winter gets the same favorable elements as one born in Summer — fundamentally wrong.
* **Incomplete Hidden Stem coverage.** Approximately 60% of chart interactions come from hidden stems inside Earthly Branches. Apps that skip hidden stem Ten Gods are missing the majority of the reading.
* **Wrong year boundary.** Many apps use January 1st or Lunar New Year as the BaZi year boundary. The correct boundary is Li Chun (立春, \~Feb 3–5), the solar year start. Every late-January / early-February birth gets the wrong year pillar.

### 2.2 — Centralized & Unverifiable

Existing metaphysics platforms are centralized SaaS applications. Users cannot verify whether the engine is using classical formulas or producing arbitrary results. There is no audit trail, no open methodology, and no way to hold the platform accountable for calculation accuracy.

### 2.3 — No Aligned Incentive Model

Traditional metaphysics apps monetize via ads, one-time purchases, or opaque subscription models with no token-aligned incentive structure. There is no mechanism for the community to participate in governance, no deflationary pressure on a utility token, and no on-chain proof of engagement.

***

## 3. The Solution — EnerQi Platform

EnerQi addresses all three problems through three integrated pillars:

### Pillar 1: Audited Classical Engine

The BaZi Engine is a self-contained calculation module that implements classical Zi Ping methodology with zero shortcuts. It has been independently audited against the 10,000-Year Calendar, Joey Yap's published standards, and San Ming Tong Hui classical texts — scoring **100/100** across 6 feature groups (see [Appendix A](ENQI_Whitepaper_v1.md#13-appendix-a--bazi-engine-audit-report)).

### Pillar 2: Decentralized Identity & Access

Users authenticate via WalletConnect on Shido Network. Birth chart data is stored with privacy commitments (birthdate is never stored in raw form). Access to advanced features is gated by $ENQI staking tiers and on-chain subscription payments — every transaction is verifiable on ShidoScan.

### Pillar 3: $ENQI Utility Token

The $ENQI token powers staking tiers, pay-per-use feature unlocks, subscription plans, the Wishing Well lottery system, and the Sacred Offering burn mechanic. Token utility creates sustainable demand, while the burn mechanism introduces permanent deflationary pressure.

***

## 4. BaZi Engine — Technical Architecture

The BaZi Engine is a pure JavaScript module (`BaZiEngine.js`) that performs all classical calculations client-side in the dApp and server-side via Node.js for the Telegram bot and API. It is the **single source of truth** — the same engine powers every channel.

### 4.1 — Core Calculation Pipeline

```
Birth DateTime + Location
        │
        ▼
┌─ True Solar Time Correction ─┐
│  IANA timezone lookup         │
│  Historical DST awareness     │
│  Equation of Time             │
│  Longitude meridian offset    │
└───────────────────────────────┘
        │
        ▼
┌─ Four Pillar Derivation ──────┐
│  Year:  Li Chun boundary      │
│  Month: 24 Solar Terms        │
│  Day:   60 Jia Zi epoch       │
│  Hour:  Wu Shu Dun formula    │
│  + Split Rat Hour handling    │
└───────────────────────────────┘
        │
        ▼
┌─ Element Balance (Wang Shuai) ┐
│  Seasonal vigor weights       │
│  Position weights (M=1.5x)    │
│  Hidden stem 7:2:1 ratio      │
│  Stem He transformation       │
│  Three Harmony transformation │
│  5-tier strength assignment   │
│  Tiao Hou climate override    │
└───────────────────────────────┘
        │
        ▼
┌─ Interpretation Layer ────────┐
│  Ten Gods (all hidden stems)  │
│  Ge Ju (Structure Detection)  │
│  Shen Sha (25+ stars)         │
│  Kong Wang (Void detection)   │
│  Na Yin (Sound Element)       │
│  Fan Yin / Fu Yin detection   │
│  Interactions & Penalties     │
└───────────────────────────────┘
        │
        ▼
┌─ Timing Layer ────────────────┐
│  Da Yun (10-year luck)        │
│  Liu Nian (annual luck)       │
│  Liu Yue (monthly luck)       │
│  Xiao Yun (childhood luck)    │
│  Daily scoring                │
└───────────────────────────────┘
```

### 4.2 — Audit Score

The engine has been independently audited against classical Ming Li standards:

| Feature Group       | Score         | Notes                                                                          |
| ------------------- | ------------- | ------------------------------------------------------------------------------ |
| Lookup Tables       | 25 / 25       | All stems, branches, hidden stems, clashes, combinations, punishments verified |
| Pillar Calculation  | 25 / 25       | Li Chun boundary, solar terms, True Solar Time — all correct                   |
| Ten Gods Logic      | 20 / 20       | Exact derivation for all 10 gods; hidden stem Ten Gods at all levels           |
| Da Yun / Liu Nian   | 15 / 15       | Forward/reverse logic, Fan Yin, Fu Yin — all correct                           |
| Day Master Strength | 10 / 10       | Month weighted 1.5x; 5-tier system; full Tiao Hou                              |
| Domain Scoring      | 5 / 5         | Single source of truth; strength-sensitive formulas                            |
| **TOTAL**           | **100 / 100** |                                                                                |

The complete audit report is in [Appendix A](ENQI_Whitepaper_v1.md#13-appendix-a--bazi-engine-audit-report).

### 4.3 — Methodological Choices

These are documented in the engine source code and locked:

1. **Solar Year Boundary:** Li Chun (立春), not January 1st and not Lunar New Year.
2. **Yin Stem 12 Qi Direction:** Yang stems cycle forward, Yin stems cycle reverse (San Ming Tong Hui orthodox).
3. **Zi Hidden Stems:** Single-stem model \[癸] per Yuan Hai Zi Ping (渊海子平).
4. **Neutral Elements:** Elements not in favElements and not in unfavElements score 0 — no bonus, no penalty.
5. **Tiao Hou Priority:** Climate regulation overrides Wang Shuai strength calculation when seasonal needs are extreme.

***

## 5. Feature Overview

### 5.1 — Four Pillars Analysis

Full natal chart with Year, Month, Day, and Hour pillars. Each pillar displays: Heavenly Stem, Earthly Branch, Hidden Stems with Ten Gods, 12 Growth Phase, Na Yin element, and Shen Sha stars. Life palace aspects mapped to age ranges (Social Fate 0–17, Career 18–35, Self & Spouse 36–50, Children & Legacy 51+).

### 5.2 — Day Master Strength (Wang Shuai)

5-tier system (Very Strong / Strong / Balanced / Weak / Very Weak) with ±0.05 buffer zones for borderline charts. Seasonal vigor weights (Wang 3.0 → Si 0.25), position weights (Month = 1.5x), hidden stem 7:2:1 ratio, Stem He and Three Harmony dynamic transformation, and complete Tiao Hou for all 20 DM/season combinations.

### 5.3 — Structure Detection (Ge Ju)

Identifies all 10 standard structures from Month Branch hidden stems. Hua Qi (Transformation Structure) detection when the Day Master forms a Stem He with seasonal support. Follow Chart and Vibrant Chart with micro-root override. Classical Tou Chu Duo Ge (secondary/tertiary stem stealing structure via Year/Hour).

### 5.4 — Da Yun & Liu Nian Cycles

10-year luck pillars with favorability scoring, Ten Gods, 12 Qi Growth Phase, Shen Sha stars, and full natal interaction analysis (Clashes, Harmonies, Harms, Destructions, Penalty completions, Stem Unions). Fan Yin / Fu Yin detected at Da Yun and Liu Nian levels. Each Da Yun cycle expands into 10 individual Liu Nian (annual) pillars.

### 5.5 — Monthly Luck (Liu Yue)

12 monthly pillars for the current BaZi year with element scoring, Ten Gods, Growth Phases, and natal interactions per month.

### 5.6 — Symbolic Stars (Shen Sha)

25+ classical stars including: Nobleman (贵人), Peach Blossom (桃花), Traveling Horse (驿马), Academic Star (文昌), Goat Blade (羊刃), Elegant Seal (华盖), General Star (将星), Lu Shen (禄神), Red Matchmaker (红鸾), Heavenly Joy (天喜), Tai Ji Noble (太极贵人), Heavenly Virtue (天德), Monthly Virtue (月德), Robbery Sha (劫煞), Blood Knife (血刃), Yin Sha (阴煞), Heavenly Kitchen (天厨), Heaven Net / Earth Net (天罗地网), and more.

### 5.7 — Daily & Annual Scoring

**Daily:** Personal energy score based on day pillar element alignment with favorable/unfavorable elements, natal branch interactions, stem combos, and Three Harmony completions.

**Annual:** Four domain scores — Career, Wealth, Relationships, Health — computed with strength-sensitive classical formulas. Career uses Officer element differentiation by DM strength. Wealth uses the 5-tier Cai Duo Shen Ruo graduated formula. Relationships include Spouse Palace Harmony/Clash and Peach Blossom activation. Da Yun penalty capped at 30% for Relationships (Spouse Palace dominates).

### 5.8 — Auspicious Date Selection (Ze Ri)

5-layer classical scoring system:

* **Layer 1 (35%):** Personal Yong Shen element alignment
* **Layer 2 (30%):** 12 Day Officers (建除十二神) with event-type activity matching
* **Layer 3 (25%):** 28 Lunar Mansions (Xiu) with activity matching
* **Layer 4 (10%):** Monthly Qi alignment
* **Layer 5 (7%):** XKDG hexagram nature overlay

Personal Clash override (Sui Po / Ri Po) applies a -40 penalty. San Sha, Sui Sha, and Yue Sha afflictions apply additional penalties capped at -50.

### 5.9 — Compatibility Engine

21-vector pairwise analysis covering: Stem Union, Spouse Palace Harmony/Clash, Three Harmony, Element Generation/Control, Strength Balance, Na Yin Year Pillar compatibility, Favorable Element overlap, Career Star activation, Children Palace, Ancestral Roots, Resource Star cross-check, and Yin/Yang polarity. Six domain sub-scores: Romance, Business, Friendship, Longevity, Family, Career.

N-person group compatibility with pairwise matrix, role archetypes (Visionary, Leader, Anchor, Executor, Sage), weak link / strong bond identification, group Three Harmony detection, and generating cycle analysis.

### 5.10 — Feng Shui (Xuan Kong)

Ming Gua calculation with Li Chun correction (pre/post-2000 formula). Annual Flying Stars with Lo Shu grid distribution. Xuan Kong Fei Xing (XKFX) property charts using the Shen Zhu Reng (沈竹礽) classical system — period determination, facing/sitting palace identification, and water/mountain star flight direction based on period-facing polarity match.

### 5.11 — AI Shi Fu

AI-powered metaphysics advisor backed by the BaZi Engine. Uses tool-augmented generation — the AI calls the actual BaZi Engine functions (not hallucinating). Provides personalized interpretations of natal charts, timing advice, compatibility analysis, and date selection guidance. Accessible via dApp and Telegram bot. Chat limits tiered by staking level and subscription plan.

### 5.12 — Wishing Well (许愿井)

On-chain wishing feature where users submit wishes with $ENQI entries. Wishes float in an animated display. Periodic draws select winners from the pool. Entry verification is on-chain via transaction hash.

### 5.13 — Sacred Offering (圣祭)

Deflationary burn mechanic. Users burn $ENQI tokens as offerings. The participant with the highest cumulative burn in each cycle wins a reward. Burns are permanent and reduce total supply. The mechanism combines metaphysical ritual with token economics — creating sustained deflationary pressure.

***

## 6. $ENQI Token

### 6.1 — Overview

| Parameter      | Value                         |
| -------------- | ----------------------------- |
| Token Name     | EnerQi                        |
| Symbol         | ENQI                          |
| Standard       | ERC-20                        |
| Network        | Shido Network (Chain ID 9008) |
| Decimals       | 18                            |
| Initial Supply | 888,888,888 ENQI              |
| Deflationary   | Yes (Sacred Offering burn)    |

The number 888,888,888 is intentional — 8 (八) is the most auspicious number in Chinese metaphysics, representing prosperity and infinite abundance. The triple-eight pattern maximizes this symbolism.

### 6.2 — Distribution

| Allocation               | Percentage | Tokens      | Purpose                                  |
| ------------------------ | ---------- | ----------- | ---------------------------------------- |
| Liquidity Pool           | 30%        | 266,666,666 | DEX trading liquidity on Shido Network   |
| Treasury                 | 20%        | 177,777,777 | Platform development, operations, runway |
| Staking Reserve          | 15%        | 133,333,333 | Staking rewards for tier access          |
| Marketing & Partnerships | 15%        | 133,333,333 | Partnerships, listings, growth campaigns |
| Ecosystem & Community    | 15%        | 133,333,333 | Community rewards, airdrops, incentives  |
| DAO                      | 5%         | 44,444,444  | Future governance and community voting   |

### 6.3 — Token Utility

$ENQI has five distinct utility functions within the EnerQi ecosystem:

**1. Staking for Tier Access** Users stake $ENQI to unlock progressive feature tiers. Higher staking tiers grant access to advanced features (Compatibility, Feng Shui, AI Shi Fu extended limits) and increased partner profile slots.

**2. Pay-Per-Use** Individual features can be unlocked with a one-time $ENQI payment, verified on-chain. Users who don't want to commit to staking can pay per feature.

**3. Subscription Plans** Time-based subscription tiers purchasable with $ENQI. Each subscription unlocks a bundle of features for a set duration (e.g., 30 days) with configurable daily AI chat limits.

**4. Wishing Well Entries** $ENQI is used to submit wishes and enter draws in the Wishing Well system.

**5. Sacred Offering (Burn)** $ENQI is permanently burned in the Sacred Offering ritual. This is a true deflationary mechanism — burned tokens are removed from total supply, not recycled. The burn creates permanent scarcity.

### 6.4 — Deflationary Mechanics

The Sacred Offering burn is the primary deflationary mechanism. Each offering cycle removes $ENQI from circulation permanently. As adoption grows, burn volume increases, creating a supply reduction curve that rewards long-term holders.

Secondary deflationary pressure comes from staking lockups — tokens staked for tier access are removed from circulating supply for the duration of the stake.

***

## 7. Access & Tier System

### 7.1 — Staking Tiers

Access to EnerQi features is gated by the amount of $ENQI staked via the Shido Network staking contract. The tier system is admin-configurable and currently operates as follows:

| Tier | Label    | Features                                                 | Daily AI Chats | Partner Profiles |
| ---- | -------- | -------------------------------------------------------- | -------------- | ---------------- |
| 0    | Free     | Basic natal chart, daily score                           | —              | 2                |
| 1    | Explorer | + Annual forecast, Monthly luck, Interactions, Health    | 10             | 5                |
| 2    | Master   | + Compatibility, Feng Shui, Ze Ri, AI Shi Fu, Hidden tab | 20+            | 10               |

### 7.2 — Feature Gates

Every feature in the platform is controlled by a configurable feature gate stored in the database. Each gate specifies:

* **Feature ID** — unique identifier
* **Min Tier** — minimum staking tier required
* **Unlock Method** — `free`, `staking`, `pay-per-use`, or `subscription`
* **Price** — for pay-per-use/subscription features
* **Currency** — ENQI or WSHIDO

Administrators can modify gates in real-time without code deployment.

### 7.3 — Subscription Tiers

In addition to staking, users can purchase time-limited subscription plans with $ENQI. Each subscription tier unlocks a specific set of features for a defined duration (typically 30 days). Subscriptions are recorded on-chain via transaction hash verification.

***

## 8. On-Chain Mechanics

### 8.1 — Payment Verification

All payments ($ENQI or native SHIDO) are verified on-chain before feature access is granted:

1. User submits a transaction via WalletConnect
2. Transaction is confirmed on Shido Network
3. Backend fetches the transaction receipt from the RPC node
4. Transfer event logs are decoded to verify: recipient = treasury wallet, amount ≥ expected price (5% slippage tolerance)
5. Payment record is stored with the verified transaction hash

No payment is accepted without on-chain confirmation. This eliminates fake payment exploits.

### 8.2 — Sacred Offering (Burn)

The Sacred Offering operates in timed cycles:

1. Users approve and burn $ENQI tokens via the EnerQi contract
2. Burns are recorded with on-chain transaction verification
3. Each user's cumulative burn amount is tracked per cycle
4. At cycle end, the highest total burner wins a reward
5. All burned tokens are permanently removed from total supply

The BaZi day score is factored into the offering system — connecting metaphysical timing to on-chain activity.

### 8.3 — Wishing Well

Users submit wishes with $ENQI entry fees. Entries are verified on-chain. A countdown timer tracks each draw cycle. Winners are selected at draw time. The system features an animated wish display where submitted wishes float across the screen.

### 8.4 — Wallet Signature Verification

All authenticated API requests require a wallet signature. The backend verifies `ecrecover` against the claimed wallet address. This prevents impersonation — only the wallet owner can access their profile, make payments, or submit offerings.

***

## 9. Multi-Channel Architecture

EnerQi operates across three integrated channels, all powered by the same BaZi Engine:

### 9.1 — dApp (React + WalletConnect)

The primary interface. Built with React, connected to Shido Network via Reown AppKit (WalletConnect). Features include:

* Full natal chart with interactive tabs (Pillars, Interactions, Cycles, Daily, Annual, Health, Match, Auspicious, Feng Shui, Hidden)
* AI Shi Fu chat interface
* Wishing Well and Sacred Offering pages
* Admin panel for feature gates, tier config, subscriptions, and announcements

### 9.2 — Telegram Bot

A full-featured Telegram bot providing:

* `/mytoday` — personal daily score with day pillar and advice
* `/myforecast` — annual forecast with domain scores
* `/myluckydates` — date selection for upcoming events
* `/match` — pairwise chart comparison
* AI Shi Fu chat via natural language messages
* Automated daily broadcasts at user-configured times and timezone offsets
* Group support with admin-only command gating

### 9.3 — REST API

A secured API layer for partner integrations:

* `POST /api/bazi/analyze` — full BaZi engine analysis
* API key authentication (`X-Api-Key` header) for external partners
* Internal secret authentication for bot and AI Shi Fu
* Rate limiting and tier-based access controls

All three channels produce **identical results** for the same input — guaranteed by the single-source-of-truth architecture.

***

## 10. AI Shi Fu — Intelligent Advisory Layer

AI Shi Fu (AI 师父, "AI Master") is an AI-powered metaphysics advisor that provides personalized BaZi interpretations. Unlike generic chatbots, AI Shi Fu is **tool-augmented** — it calls the actual BaZi Engine functions to retrieve accurate data before generating responses.

### 10.1 — How It Works

1. User asks a question (e.g., "Is this a good month for me to start a business?")
2. AI Shi Fu calls BaZi Engine tools: `getDailyScore()`, `getYearScore()`, `calcLiuYue()`, `getAuspiciousDates()`
3. Engine returns exact scores, Ten Gods, interactions, and favorable dates
4. AI Shi Fu interprets the data in natural language with classical references

The AI never guesses or hallucinations numerical results — all data comes from the verified engine.

### 10.2 — Chat Limits

AI Shi Fu usage is tiered:

* **Free tier:** No access
* **Staking Tier 1:** 10 chats per day
* **Staking Tier 2:** 20 chats per day
* **VIP wallets:** 50 chats per day
* **Subscription plans:** Configurable per plan

***

## 11. Security & Privacy

### 11.1 — Birthdate Privacy

Birth datetime — the most sensitive input in BaZi — is **never stored in raw form**. The database stores only:

* `birthdate_commitment` — a cryptographic commitment hash
* `birthdate_salt_hint` — a partial salt for user recovery
* Derived outputs (pillars, elements, scores) — which cannot be reverse-engineered to the exact birth time

### 11.2 — Wallet Signature Verification

Every authenticated request requires a valid EIP-191 signature from the user's wallet. The backend recovers the signer address and compares it against the claimed wallet. This is enforced on all payment, profile, and offering endpoints.

### 11.3 — On-Chain Transaction Verification

All payments are verified by fetching the transaction receipt from the Shido RPC node and decoding Transfer event logs. The backend confirms:

* Transaction is confirmed (receipt.status === 1)
* Recipient is the treasury wallet
* Amount matches expected price (5% slippage tolerance)
* Token contract address matches the ENQI contract

### 11.4 — Admin Security

Admin actions are gated by wallet address verification. All admin operations are recorded in an audit log table (`admin_log`) with: admin wallet, action, target, old value, new value, and timestamp.

### 11.5 — API Security

External API access requires a registered API key (`X-Api-Key` header). Keys are stored as SHA-256 hashes in the database — the raw key is never stored. Internal services use a separate `X-Internal-Secret` header.

***

## 12. Roadmap

| Phase                     | Timeline    | Milestones                                                                     |
| ------------------------- | ----------- | ------------------------------------------------------------------------------ |
| Phase 1 — Foundation      | ✅ Complete  | BaZi Engine, dApp, Telegram Bot, $ENQI token launch on Shido Network           |
| Phase 2 — Monetization    | ✅ Complete  | Staking tiers, pay-per-use, subscription system, on-chain payment verification |
| Phase 3 — AI & Engagement | ✅ Complete  | AI Shi Fu, Wishing Well, Sacred Offering, daily broadcast system               |
| Phase 4 — Expansion       | In Progress | Partner API, multi-language support, mobile-optimized experience               |
| Phase 5 — Governance      | Planned     | DAO activation, community voting on feature priorities, governance proposals   |
| Phase 6 — Cross-Chain     | Planned     | Bridge to additional EVM chains, cross-chain staking                           |

***

## 13. Appendix A — BaZi Engine Audit Report

### Audit Metadata

| Field             | Value                                                                                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------- |
| Audit Date        | March 2026                                                                                              |
| Engine            | BaZiEngine.js — EnerQi Metaphysics dApp                                                                 |
| Files Audited     | 7 (BaZiEngine, MetaphysicsConstants, baziTools, baziHelpers, baziAnalyze, botScore, annualDomainScores) |
| Methodology       | Classical Zi Ping / Joey Yap / San Ming Tong Hui                                                        |
| Final Score       | **100 / 100**                                                                                           |
| School Variations | 1 (locked trade-off, does not affect accuracy)                                                          |

***

### A.1 — Lookup Table Verification

**1.1 — Heavenly Stems (Tian Gan): PASS** All 10 stems in correct order with correct element and polarity.

**1.2 — Earthly Branches (Di Zhi): PASS** All 12 branches correct with correct element, polarity, and season assignment.

**1.3 — Hidden Stems (Cang Gan): PASS (1 School Variation)**

| Branch | Engine         | Classical Spec | Verdict    |
| ------ | -------------- | -------------- | ---------- |
| Zi     | Gui            | Gui            | PASS       |
| Chou   | Ji, Gui, Xin   | Ji, Gui, Xin   | PASS       |
| Yin    | Jia, Bing, Wu  | Jia, Bing, Wu  | PASS       |
| Mao    | Yi             | Yi             | PASS       |
| Chen   | Wu, Yi, Gui    | Wu, Yi, Gui    | PASS       |
| Si     | Bing, Wu, Geng | Bing, Geng, Wu | SCHOOL VAR |
| Wu     | Ding, Ji       | Ding, Ji       | PASS       |
| Wei    | Ji, Ding, Yi   | Ji, Ding, Yi   | PASS       |
| Shen   | Geng, Ren, Wu  | Geng, Ren, Wu  | PASS       |
| You    | Xin            | Xin            | PASS       |
| Xu     | Wu, Xin, Ding  | Wu, Xin, Ding  | PASS       |
| Hai    | Ren, Jia       | Ren, Jia       | PASS       |

**Si School Variation:** Engine uses Joey Yap ordering \[Bing, Wu, Geng]. San Ming Tong Hui uses \[Bing, Geng, Wu]. Weight difference: 0.143 units between Metal and Earth per Si branch. Both orderings are published in authoritative texts. This is a locked trade-off between schools, not an error.

**1.4 — 60 Jia Zi Cycle: PASS** Spot-checks: Position 1 = Jia-Zi, Position 10 = Gui-You, Position 30 = Gui-Si, Position 60 = Gui-Hai.

**1.5 — Six Clashes: PASS** All 6 pairs: Zi-Wu, Chou-Wei, Yin-Shen, Mao-You, Chen-Xu, Si-Hai.

**1.6 — Six Combinations: PASS** All 6 bidirectional mappings: Zi-Chou, Yin-Hai, Mao-Xu, Chen-You, Si-Shen, Wu-Wei.

**1.7 — Three Harmony: PASS** All 4 sets: Shen-Zi-Chen (Water), Hai-Mao-Wei (Wood), Yin-Wu-Xu (Fire), Si-You-Chou (Metal).

**1.8 — Stem Combinations: PASS** All 5 pairs: Jia-Ji (Earth), Yi-Geng (Metal), Bing-Xin (Water), Ding-Ren (Wood), Wu-Gui (Fire).

**1.9 — Punishments: PASS** Self-Penalty: Chen, Wu, You, Hai. Unkind (Wu Li Zhi Xing): Zi-Mao. Ungrateful (Wu En Zhi Xing): Yin-Si-Shen. Bullying (Shi Shi Zhi Xing): Chou-Xu-Wei.

**1.10 — Harms: PASS** All 6 pairs: Zi-Wei, Chou-Wu, Yin-Si, Mao-Chen, Shen-Hai, You-Xu.

**1.11 — Destructions: PASS** All 6 pairs with bidirectional lookups.

***

### A.2 — Ten Gods Logic

**2.1 — Derivation Rules: PASS**

| Relationship       | Same Polarity                | Opposite Polarity           |
| ------------------ | ---------------------------- | --------------------------- |
| Same element as DM | Friend (Bi Jian)             | Rob Wealth (Jie Cai)        |
| DM produces this   | Eating God (Shi Shen)        | Hurt Officer (Shang Guan)   |
| This produces DM   | Indirect Resource (Pian Yin) | Direct Resource (Zheng Yin) |
| This controls DM   | 7-Killings (Qi Sha)          | Direct Officer (Zheng Guan) |
| DM controls this   | Indirect Wealth (Pian Cai)   | Direct Wealth (Zheng Cai)   |

Verified: DM = Jia (Wood, Yang), target = Geng (Metal, Yang) correctly yields 7-Killings.

**2.2 — Hidden Stem Ten Gods: PASS** All hidden stems in each branch mapped to Ten Gods. Coverage at natal, Da Yun, and Liu Nian levels.

***

### A.3 — Pillar Calculation

**3.1 — Year Pillar: PASS** Li Chun boundary correctly used. Jan 20, 2000 birth receives the 1999 year pillar.

**3.2 — Month Pillar: PASS** 24 Solar Terms for boundaries. Wu Hu Dun formula for month stem derivation.

**3.3 — Day Pillar: PASS** 60-day Jia Zi cycle from known epoch. Reference: 1984-02-02 = Jia-Zi.

**3.4 — Hour Pillar: PASS** Standard 2-hour assignments. Wu Shu Dun formula. Split Rat Hour implemented.

**3.5 — True Solar Time: PASS** IANA timezone lookup, historical DST-aware offset, Equation of Time correction, longitude-meridian difference. Production-quality implementation.

***

### A.4 — Da Yun Luck Pillars

**4.1 — Forward / Reverse Logic: PASS** Male + Yang = Forward, Male + Yin = Reverse, Female + Yang = Reverse, Female + Yin = Forward.

**4.2 — Start Age Calculation: PASS** Days to solar term ÷ 3.

**4.3 — Pillar Sequencing: PASS** Correctly sequenced through the 60 Jia Zi cycle with Ten Gods, Growth Phases, and natal interactions.

**4.4 — Fan Yin / Fu Yin: PASS** Fu Yin: same stem + same branch. Fan Yin: same stem + clashing branch (30 apart in 60 Jiazi). Detected at natal, Da Yun, and Liu Nian levels.

***

### A.5 — Day Master Strength

**PASS**

* **Seasonal Vigor:** Wang = 3.0, Xiang = 2.0, Xiu = 0.75, Qiu = 0.5, Si = 0.25
* **Position Weights:** Year = 0.5, Month = 1.5, Day = 1.0, Hour = 0.75
* **Hidden Stem Weights:** 7:2:1 ratio (1.0, 0.286, 0.143)
* **5-Tier System** with ±0.05 buffer zones
* **Stem He & Three Harmony Transformation** with seasonal support checks
* **Complete Tiao Hou** for all 5 DM elements × 4 seasons with strength-sensitive prescriptions

***

### A.6 — Domain Scoring

**PASS**

* Domains: Career, Wealth, Relationships, Health, Overall
* Personal favorable/unfavorable elements (post-Tiao Hou)
* No double-counting
* All four natal pillars checked for annual interactions
* Clashes, Harms, Harmonies, Peach Blossom, Spouse Palace — all applied as modifiers
* Strength-sensitive formulas (Career Officer, Wealth Cai Duo Shen Ruo, 30% Da Yun cap for Relationships)
* Single source of truth across dApp, Telegram bot, and AI Shi Fu

***

### A.7 — Final Score

| Feature Group       | Score         |
| ------------------- | ------------- |
| Lookup Tables       | 25 / 25       |
| Pillar Calculation  | 25 / 25       |
| Ten Gods Logic      | 20 / 20       |
| Da Yun / Liu Nian   | 15 / 15       |
| Day Master Strength | 10 / 10       |
| Domain Scoring      | 5 / 5         |
| **TOTAL**           | **100 / 100** |

**AUDIT COMPLETE. Score: 100/100. School variations: 1 (locked trade-off).**

***

_© 2026 EnerQi. All rights reserved._ _Built on Shido Network. Powered by classical Zi Ping BaZi methodology._
