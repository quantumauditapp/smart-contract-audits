---
token: Official Bridge Currency
ticker: OBC
network: solana
risk_score: 72
status: critical
date: 2026-06-10
---

# Official Bridge Currency (OBC) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/official-bridge-currency-sol)

---

## Audit Summary

The Official Bridge Currency (OBC) token mint has revoked both mint and freeze authorities, indicating a fixed supply and no ability to freeze user funds. However, the token suffers from very low liquidity, with only $4,442 available on DEXs, making large trades highly susceptible to slippage. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Prospective holders should be aware of the extremely low liquidity ($4,442) for OBC, which will lead to high slippage for any significant trade. While the mint and freeze authorities are revoked, providing security against supply dilution and account freezing, the lack of holder concentration data means whale risk cannot be assessed. It is recommended to proceed with extreme caution due to the liquidity constraints.

## Security Analysis

The Official Bridge Currency (OBC) token mint has revoked both mint and freeze authorities, indicating a fixed supply and no ability to freeze user funds. However, the token suffers from very low liquidity, with only $4,442 available on DEXs, making large trades highly susceptible to slippage. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

Prospective holders should be aware of the extremely low liquidity ($4,442) for OBC, which will lead to high slippage for any significant trade. While the mint and freeze authorities are revoked, providing security against supply dilution and account freezing, the lack of holder concentration data means whale risk cannot be assessed. It is recommended to proceed with extreme caution due to the liquidity constraints.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The Official Bridge Currency (OBC) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be frozen ( |
| **Governance / Economics** | 6/10 | High | The token exhibits very low liquidity, with only $4,442 USD available on DEXs, posing a significant risk for slippage and large position exits (7.4 Economic). The 24-hour volume to liquidity ratio is  |
| **Upgrades** | 6/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and freeze capabilities cannot be altered post-launch (7.7 Upgrades). The token does not utilize any Token-2022 ext |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $4,442. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the severe slippage in any swap calculation and consider the difficulty of exiting large positions.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2NECWd...ydk1`](https://solscan.io/account/2NECWdgEjSTLv2yRFmSJtiNdwyVj7sNNUcqjWGc5ydk1) |
| **Network** | Solana |
| **Price** | $0.002121 |
| **24h Volume** | $332.5K |
| **Liquidity** | $69.0K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 5d |
| **Top-10 Holders** | 44.7% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/drkhakh4eb7ncrs5odcowbvjcrasuazbtxvedezaaxkm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/official-bridge-currency-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
