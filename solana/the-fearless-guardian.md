---
token: The Fearless Guardian
ticker: GUARDIAN
network: solana
risk_score: 96
status: critical
date: 2026-06-18
---

# The Fearless Guardian (GUARDIAN) — Smart Contract Security Analysis | Solana

> **Risk Score: 96/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-fearless-guardian-sol)

---

## Audit Summary

This SPL Token-2022 mint, "The Fearless Guardian (GUARDIAN)", has revoked mint and freeze authorities, indicating a fixed supply and immutable account states. However, it suffers from very low DEX liquidity ($5,187), posing a significant risk of high slippage for any trades. Holder distribution data was unavailable, preventing a full assessment of whale risk.

> **Final Recommendation:** Prospective holders should exercise extreme caution due to the very low liquidity, which makes large positions difficult to exit without substantial price impact. Before any significant interaction, verify the current DEX liquidity on-chain to ensure it has improved. Monitor the token's trading volume and liquidity over time to assess market depth and stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is an SPL Token-2022 mint with a fixed supply of 999,740,438.348484 tokens and 6 decimals. Both the mint authority and freeze authority have been revoked, indicating a fixed supply and… |
| **Governance / Economics** | 1/10 | High | The token exhibits very low liquidity, with only $5,187 available on DEXs, which can lead to severe slippage for trades. Holder concentration data was unavailable, preventing an assessment of supply… |
| **Upgrades** | 4/10 | Medium | The mint authority and freeze authority are both revoked, meaning the token's supply and account freezing capabilities are immutable. The token is an SPL Token-2022, but no upgradable extensions like… |

## Security Findings

_🟠 1 High_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $5,187. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the low liquidity in any swap calculation and consider the difficulty of exiting large positions. Verify current liquidity before trading.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7YMkZZ...pump`](https://solscan.io/account/7YMkZZwdcwUbXKjYpr5gFAVoB6aF4f9iLWK6pUcppump) |
| **Network** | Solana |
| **Price** | $0.00000291 |
| **24h Volume** | $80 |
| **Liquidity** | $4.9K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 6d |
| **Top-10 Holders** | 93.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4236 buys / 3658 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is The Fearless Guardian a scam?

Based on available data, we cannot definitively label The Fearless Guardian (GUARDIAN) as a scam, but it exhibits several high-risk characteristics. The contract is unverified, meaning its code is not transparent for review. Crucially, the liquidity is not locked, creating a significant potential for a "rug pull" where funds could be withdrawn. This combination warrants extreme caution, reflected in its 47/100 high-risk score.

### Is The Fearless Guardian safe to buy?

The Fearless Guardian is currently not considered safe for investment due to several prominent risk factors. The contract's unverified status prevents any independent security review, fostering a lack of transparency. Most critically, the liquidity pool is not locked, which presents a high risk of a liquidity withdrawal, commonly known as a "rug pull." These significant unmitigated risks contribute to its high-risk score of 47/100.

### Has The Fearless Guardian been audited?

Based on the provided data, The Fearless Guardian's contract has not been verified. This means the underlying code is not publicly available or confirmed to match the deployed version, preventing any independent security audit by third parties. Without verification, a comprehensive security audit is impossible, leaving investors in the dark about potential vulnerabilities or malicious functions.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/g3nj1jdjqhsb4exhcfspxtxynnbkkzakhsm5zdsk6tnw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-fearless-guardian-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-18*
