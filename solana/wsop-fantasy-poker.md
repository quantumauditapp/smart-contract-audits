---
token: WSOP Fantasy Poker
ticker: WSOLP
network: solana
risk_score: 34
status: medium
date: 2026-06-21
---

# WSOP Fantasy Poker (WSOLP) — Smart Contract Security Analysis | Solana

> **Risk Score: 34/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wsop-fantasy-poker-sol)

---

## Audit Summary

The WSOP Fantasy Poker (WSOLP) token mint exhibits a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, indicating a fixed supply and no ability to freeze user funds. No critical or high-severity findings were identified. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Based on the available data, the WSOP Fantasy Poker (WSOLP) token mint appears to be configured securely with revoked mint and freeze authorities. Users should be aware that holder concentration data was unavailable, so a full assessment of distribution risk could not be made. It is recommended to monitor the token's liquidity and trading volume for stability. For a Premium Deploy, consider integrating additional real-time monitoring for liquidity pool changes and holder movements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture & 7.2 Code Security: The WSOP Fantasy Poker (WSOLP) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, which is a strong security positiv |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic: The token has a total DEX liquidity of $34,001 USD, with a 24-hour volume of $25,153 USD, resulting in a normal Volume/Liquidity Ratio of 0.74. The DEX pair is 13 days old, indicating it |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The mint authority and freeze authority are both revoked, meaning the token's supply and freeze capabilities cannot be altered. The token uses the spl-token-2022 program, but no transfer |

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
| **Contract** | [`GvUCjm...pump`](https://solscan.io/account/GvUCjmWSXA5hrTh9smmNA1AU55YCtP9mDLQcrKA1pump) |
| **Network** | Solana |
| **Price** | $0.0005483 |
| **24h Volume** | $40.5K |
| **Liquidity** | $54.6K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 4d |
| **Top-10 Holders** | 29.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 226 buys / 220 sells |

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

### Is WSOP Fantasy Poker a scam?

The data presents a mixed picture. While ownership is renounced and no mint function exists, the contract is unverified, and liquidity is not locked. These factors introduce significant red flags typically associated with potential scams or high-risk projects. Investors should proceed with extreme caution and conduct thorough independent research before making any investment decisions.

### Is WSOP Fantasy Poker safe to buy?

WSOP Fantasy Poker (WSOLP) is categorized as a high-risk asset (47/100). The unverified contract and unlocked liquidity are major safety concerns, exposing investors to potential vulnerabilities and rug pull risks. The concentration of tokens among top holders also adds to market manipulation potential. It is not considered safe without further verification and improved security measures.

### Has WSOP Fantasy Poker been audited?

The provided information indicates that the WSOP Fantasy Poker (WSOLP) contract is not verified. This means the deployed code has not been publicly confirmed and matched against a known codebase, which is a prerequisite for a formal security audit. Without contract verification, a comprehensive security audit cannot be reliably conducted or confirmed.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/h5gzcmccxdzexzneddgfepjnpyayuyhh6t4cyxt5pdfz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wsop-fantasy-poker-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-21*
