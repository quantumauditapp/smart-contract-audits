---
token: World Cup Coin
ticker: WORLDCUP
network: solana
risk_score: 85
status: critical
date: 2026-06-10
---

# World Cup Coin (WORLDCUP) — Smart Contract Security Analysis | Solana

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-cup-coin-sol)

---

## Audit Summary

The World Cup Coin (WORLDCUP) token mint exhibits a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, indicating a fixed supply and no ability to freeze user funds. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Based on the available on-chain data, World Cup Coin (WORLDCUP) presents a low-risk profile regarding its token mint configuration. The revocation of both mint and freeze authorities is a strong positive indicator, ensuring a fixed supply and preventing arbitrary freezing of user funds. Holders should be aware that holder concentration data was not available, so a full assessment of distribution risk could not be performed.

For a Premium Deploy option, consider integrating real-time holder distribution monitoring to provide continuous insights into whale activity and potential market impact. Additionally, if future Token-2022 extensions are considered, ensure thorough review and community communication.

## Security Analysis

The World Cup Coin (WORLDCUP) token mint exhibits a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, indicating a fixed supply and no ability to freeze user funds. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

Based on the available on-chain data, World Cup Coin (WORLDCUP) presents a low-risk profile regarding its token mint configuration. The revocation of both mint and freeze authorities is a strong positive indicator, ensuring a fixed supply and preventing arbitrary freezing of user funds. Holders should be aware that holder concentration data was not available, so a full assessment of distribution risk could not be performed.

For a Premium Deploy option, consider integrating real-time holder distribution monitoring to provide continuous insights into whale activity and potential market impact. Additionally, if future Token-2022 extensions are considered, ensure thorough review and community communication.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The World Cup Coin (WORLDCUP) token is an SPL Token-2022 mint. Crucially, both the mint authority and freeze authority have been revoked, ensuring no new tokens can be created and no existing tokens c |
| **Governance / Economics** | 6/10 | Low | The token exhibits healthy trading metrics with a liquidity of $332,489 and a 24-hour volume of $437,617. The volume/liquidity ratio is 1.32, which is considered normal and does not suggest wash tradi |
| **Upgrades** | 6/10 | Low | The token's mint and freeze authorities are permanently revoked, meaning the core parameters of supply and transfer control cannot be altered. The token utilizes the spl-token-2022 program but does no |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`33eum8...pump`](https://solscan.io/account/33eum82LaAhtv5YkUq1BdwEviSErH5CnFxqVNLT5pump) |
| **Network** | Solana |
| **Price** | $0.002513 |
| **24h Volume** | $669.0K |
| **Liquidity** | $159.1K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 2d |
| **Top-10 Holders** | 24.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/8uycgrrxzc3xky8pbjdskubaup4mpbxoj1ezj7a5g9wy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-cup-coin-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
