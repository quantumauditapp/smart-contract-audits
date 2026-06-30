---
token: The Black Bull
ticker: ANSEM
network: solana
risk_score: 76
status: critical
date: 2026-06-29
---

# The Black Bull (ANSEM) — Smart Contract Security Analysis | Solana

> **Risk Score: 76/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-black-bull-sol)

---

## Audit Summary

The Black Bull (ANSEM) is an SPL Token-2022 mint on Solana. The mint authority and freeze authority have both been revoked, indicating a fixed supply and no ability to freeze user accounts by the issuer. Holder concentration data was unavailable from RPC, but RugCheck.xyz flagged high ownership by top holders, which could indicate potential for price volatility. No critical or high-severity issues were identified based on the provided facts and deterministic rules.

> **Final Recommendation:** This token presents a relatively secure technical configuration with revoked mint and freeze authorities, indicating a fixed supply and no ability for an issuer to freeze user funds. However, the high Volume/Liquidity ratio suggests potential wash trading, and while direct holder concentration data was unavailable, RugCheck's flags for high ownership by top holders warrant caution regarding potential price volatility from large sell-offs. Investors should be aware of these economic factors (7.4 Economic, 7.6 External).

## Security Analysis

The Black Bull (ANSEM) is an SPL Token-2022 mint on Solana. The mint authority and freeze authority have both been revoked, indicating a fixed supply and no ability to freeze user accounts by the issuer. Holder concentration data was unavailable from RPC, but RugCheck.xyz flagged high ownership by top holders, which could indicate potential for price volatility. No critical or high-severity issues were identified based on the provided facts and deterministic rules.

This token presents a relatively secure technical configuration with revoked mint and freeze authorities, indicating a fixed supply and no ability for an issuer to freeze user funds. However, the high Volume/Liquidity ratio suggests potential wash trading, and while direct holder concentration data was unavailable, RugCheck's flags for high ownership by top holders warrant caution regarding potential price volatility from large sell-offs. Investors should be aware of these economic factors (7.4 Economic, 7.6 External).

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is an SPL Token-2022 mint, leveraging the latest Solana token program features. Both the mint authority and freeze authority have been revoked, which is a positive security indicator as it p |
| **Governance / Economics** | 1/10 | High | The token has substantial liquidity, with $1,222,784 USD available on DEXs. However, the 24-hour volume of $22,628,549 is significantly higher than liquidity, resulting in a Volume/Liquidity Ratio of  |
| **Upgrades** | 6/10 | Medium | The token's mint authority and freeze authority have been revoked, meaning no further tokens can be minted and no accounts can be frozen by an administrative key. It utilizes the spl-token-2022 progra |

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
| **Contract** | [`9cRCn9...pump`](https://solscan.io/account/9cRCn9rGT8V2imeM2BaKs13yhMEais3ruM3rPvTGpump) |
| **Network** | Solana |
| **Price** | $0.095 |
| **24h Volume** | $36.34M |
| **Liquidity** | $1.15M |
| **Volume / Liquidity** | 31.5× |
| **Token Age** | 12d |
| **Top-10 Holders** | 82.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 89728 buys / 75278 sells |

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

## Frequently Asked Questions

### Is The Black Bull a scam?

Based on the available data, The Black Bull (ANSEM) exhibits several characteristics associated with high-risk projects. Its risk score is 55/100, indicating high potential for issues. Key concerns include unlocked liquidity, highly concentrated token ownership (82.4% by top 10 holders), and an unverified contract. While ownership is renounced, these other factors suggest a substantial risk profile that warrants extreme caution.

### Is The Black Bull safe to buy?

Investing in The Black Bull (ANSEM) carries significant risks, making it generally not considered safe based on current data. The primary concerns are the unlocked liquidity, which exposes investors to potential rug pulls, and the heavily concentrated token ownership among the top 10 holders (82.4%). Furthermore, the unverified contract means the code cannot be independently audited for security vulnerabilities, contributing to its 'High Risk' score of 55/100.

### Has The Black Bull been audited?

The Black Bull (ANSEM) contract is currently unverified. This means its source code has not been publicly published and matched to the deployed contract on the blockchain. Without verification, independent security audits are severely hampered, and investors cannot confirm the contract's intended functionality or identify potential vulnerabilities, adding to its overall high-risk profile.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/fnzky6x7entq1er3d225dqyt7ybfka4pskbmqhb8l3cc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-black-bull-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-29*
