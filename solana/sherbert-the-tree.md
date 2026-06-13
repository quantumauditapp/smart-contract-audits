---
token: Sherbert The Tree
ticker: SHERBERT
network: solana
risk_score: 60
status: high
date: 2026-06-13
---

# Sherbert The Tree (SHERBERT) — Smart Contract Security Analysis | Solana

> **Risk Score: 60/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sherbert-the-tree-sol)

---

## Audit Summary

This audit of the Sherbert The Tree (SHERBERT) SPL Token Mint found no critical or high-severity issues based on the provided deterministic rules. The mint and freeze authorities are revoked, indicating a fixed supply and no ability to freeze user accounts. However, holder concentration data was unavailable, preventing a full assessment of distribution risk. The extremely low RugCheck score of 1/100 suggests potential off-chain risks not covered by the on-chain technical analysis.

> **Final Recommendation:** Based on the on-chain technical analysis and deterministic rules, the Sherbert The Tree (SHERBERT) token mint presents a secure configuration with revoked mint and freeze authorities. However, the unavailability of holder concentration data means that distribution risk cannot be fully assessed. Furthermore, the extremely low RugCheck score of 1/100 signals significant potential off-chain risks that are not captured by this technical audit. Users should proceed with extreme caution, conduct thorough due diligence on the project's team and community, and understand the implications of the low RugCheck score before engaging with this token. A Premium Deploy option is not applicable for SPL token mint audits.

## Security Analysis

This audit of the Sherbert The Tree (SHERBERT) SPL Token Mint found no critical or high-severity issues based on the provided deterministic rules. The mint and freeze authorities are revoked, indicating a fixed supply and no ability to freeze user accounts. However, holder concentration data was unavailable, preventing a full assessment of distribution risk. The extremely low RugCheck score of 1/100 suggests potential off-chain risks not covered by the on-chain technical analysis.

Based on the on-chain technical analysis and deterministic rules, the Sherbert The Tree (SHERBERT) token mint presents a secure configuration with revoked mint and freeze authorities. However, the unavailability of holder concentration data means that distribution risk cannot be fully assessed. Furthermore, the extremely low RugCheck score of 1/100 signals significant potential off-chain risks that are not captured by this technical audit. Users should proceed with extreme caution, conduct thorough due diligence on the project's team and community, and understand the implications of the low RugCheck score before engaging with this token. A Premium Deploy option is not applicable for SPL token mint audits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.8 Operations: The token is configured under the spl-token-2022 program. Both the mint authority and freeze authority are revoked (None), ensu |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic, 7.5 Governance: The token exhibits moderate liquidity with $16,309 USD available on DEXs. The 24-hour volume is $42,088, resulting in a normal Volume/Liquidity Ratio of 2.58. The DEX pai |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: The token mint has a robust configuration with both mint and freeze authorities revoked, meaning its core supply and account control parameters are immutable. GoPlus data confirms that m |

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
| **Contract** | [`5HoWa7...pump`](https://solscan.io/account/5HoWa7E5ZJBMPzrvu1WXKjicpqQTXkaTKMVC9Je8pump) |
| **Network** | Solana |
| **Price** | $0.00004856 |
| **24h Volume** | $42.1K |
| **Liquidity** | $16.1K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 11d |
| **Top-10 Holders** | 38.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 622 buys / 525 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cfxyeieng4c4s1k2hd8tkdcaewrr95hgh5dra9qjk3nt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sherbert-the-tree-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-13*
