---
token: Catcoin
ticker: CATCOIN
network: solana
risk_score: 85
status: critical
date: 2026-06-10
---

# Catcoin (CATCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catcoin-sol)

---

## Audit Summary

The Catcoin (CATCOIN) SPL token mint has no critical or high-severity vulnerabilities identified based on the available on-chain data. Key authorities such as Mint and Freeze authorities are revoked, indicating a fixed supply and immutability of account states. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Based on the available on-chain data, Catcoin (CATCOIN) presents a low technical risk profile, primarily due to the revocation of critical authorities like Mint and Freeze. Holders should be aware that holder concentration data was not available, which could hide significant whale risk. It is recommended to monitor on-chain holder distribution independently if considering a large position. For enhanced security, consider a Premium Deploy option for future token launches, which includes continuous monitoring and deeper analysis of market dynamics.

## Security Analysis

The Catcoin (CATCOIN) SPL token mint has no critical or high-severity vulnerabilities identified based on the available on-chain data. Key authorities such as Mint and Freeze authorities are revoked, indicating a fixed supply and immutability of account states. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

Based on the available on-chain data, Catcoin (CATCOIN) presents a low technical risk profile, primarily due to the revocation of critical authorities like Mint and Freeze. Holders should be aware that holder concentration data was not available, which could hide significant whale risk. It is recommended to monitor on-chain holder distribution independently if considering a large position. For enhanced security, consider a Premium Deploy option for future token launches, which includes continuous monitoring and deeper analysis of market dynamics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The Catcoin (CATCOIN) token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, ensuring that no new tokens can be minted and no holder acc |
| **Governance / Economics** | 6/10 | Low | The token exhibits moderate liquidity with $77,037 USD available on DEXs, and a 24-hour volume of $81,544, resulting in a normal Volume/Liquidity Ratio of 1.06. The DEX pair has been active for 48 day |
| **Upgrades** | 6/10 | Low | The Mint and Freeze authorities for Catcoin (CATCOIN) are both revoked, which means the token's supply and freeze capabilities are immutable. The token uses the spl-token-2022 program but does not hav |

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
| **Contract** | [`5gTPsp...coin`](https://solscan.io/account/5gTPspC2ricuGWiYQ4Ghausg8fsq7uCrGgSVACatcoin) |
| **Network** | Solana |
| **Price** | $0.0008021 |
| **24h Volume** | $327.4K |
| **Liquidity** | $95.6K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 20d |
| **Top-10 Holders** | 23.4% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/6fnwjffn6kdkybwk5pflwqznptmobaswuwvxig3g5d2d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catcoin-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
