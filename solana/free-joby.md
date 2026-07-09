---
token: Free Joby
ticker: JOBY
network: solana
risk_score: 21
status: medium
date: 2026-07-09
---

# Free Joby (JOBY) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/free-joby-sol)

---

## Audit Summary

The Free Joby (Joby) token mint is configured with revoked mint and freeze authorities, indicating a fixed supply and no ability to freeze user funds. No Token-2022 extensions like transfer hooks or permanent delegates are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk. Overall, the token exhibits a low-risk profile based on available on-chain facts and external security signals.

> **Final Recommendation:** The Free Joby (Joby) token appears to be well-configured from a security perspective, with critical authorities revoked and no concerning Token-2022 extensions active. The liquidity and trading volume are reasonable for a token of its age. However, the absence of holder concentration data means that potential risks from concentrated ownership cannot be assessed. Investors should consider this data gap when evaluating the token's market stability. For a Premium Deploy, ensure comprehensive monitoring of liquidity and holder distribution post-launch.

## Security Analysis

The Free Joby (Joby) token mint is configured with revoked mint and freeze authorities, indicating a fixed supply and no ability to freeze user funds. No Token-2022 extensions like transfer hooks or permanent delegates are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk. Overall, the token exhibits a low-risk profile based on available on-chain facts and external security signals.

The Free Joby (Joby) token appears to be well-configured from a security perspective, with critical authorities revoked and no concerning Token-2022 extensions active. The liquidity and trading volume are reasonable for a token of its age. However, the absence of holder concentration data means that potential risks from concentrated ownership cannot be assessed. Investors should consider this data gap when evaluating the token's market stability. For a Premium Deploy, ensure comprehensive monitoring of liquidity and holder distribution post-launch.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture & 7.3 Access Control: The Free Joby (Joby) token is an SPL Token-2022 mint. Both the mint authority and freeze authority are revoked (Mint Authority: revoked (None), Freeze Authority: |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic: The token exhibits healthy trading metrics with $166,373 in liquidity (Liquidity (USD): $166,373) and a 24-hour volume of $272,553 (24h Volume (USD): $272,553), resulting in a normal vol |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The mint authority and freeze authority are both revoked (Mint Authority: revoked (None), Freeze Authority: revoked (None)), meaning the token's core parameters (supply, freeze capabilit |

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
| **Contract** | [`4SnKwn...pump`](https://solscan.io/account/4SnKwnz6DyagftnFqdxsvWvehrcbEDhxmmXNQk2Jpump) |
| **Network** | Solana |
| **Price** | $0.00339 |
| **24h Volume** | $272.6K |
| **Liquidity** | $166.4K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 27d |
| **Top-10 Holders** | 16.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11806 buys / 8180 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/brbvi3yr1rrkorbk5xcag1e5urldyjgrmjixvzd6gffc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/free-joby-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-09*
