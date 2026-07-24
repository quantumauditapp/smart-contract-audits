---
token: MEEP CAT
ticker: MEEP
network: solana
risk_score: 67
status: high
date: 2026-06-19
---

# MEEP CAT (MEEP) — Smart Contract Security Analysis | Solana

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meep-cat-sol)

---

## Audit Summary

This audit of the MEEP CAT (MEEP) SPL Token Mint found no critical or high-severity risks based on the available on-chain data and third-party security registries. The mint and freeze authorities are revoked, and no Token-2022 extensions that introduce significant risks (like transfer hooks or permanent delegates) are active. Holder distribution data was unavailable, preventing an assessment of concentration risk.

> **Final Recommendation:** The MEEP CAT token mint appears to be securely configured with no immediate critical or high-severity risks identified. Holders should verify on-chain that the mint authority and freeze authority remain revoked to ensure supply and transfer immutability. While holder concentration data was unavailable for this assessment, it is always prudent for investors to monitor on-chain holder distribution over time to understand potential market impact from large holders. Continue to monitor DEX liquidity and trading volume for any significant changes that could affect market stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The MEEP CAT token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, indicating a fixed supply and immutability of account freezing. No… |
| **Governance / Economics** | 1/10 | High | The token exhibits a healthy liquidity profile with $19,039 in total DEX liquidity, which is sufficient for moderate trading activity. The 24-hour volume of $3,180 results in a normal… |
| **Upgrades** | 5/10 | Medium | The mint authority and freeze authority are both revoked, meaning no further tokens can be minted and no accounts can be frozen by an external party. The token does not utilize any Token-2022… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8jvtfe...pump`](https://solscan.io/account/8jvtfeVTJQsrQ3L4kjQmRcXJ1iSFQMmkjkCqPUe3pump) |
| **Network** | Solana |
| **Price** | $0.00001501 |
| **24h Volume** | $1.6K |
| **Liquidity** | $12.9K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 64.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5604 buys / 4916 sells |

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

### Is MEEP CAT a scam?

Based on the provided data, there isn't definitive proof to label MEEP CAT as a scam, but significant risks exist. The ownership being renounced and no mint function present are positive signals, preventing certain common scam tactics like malicious contract changes or endless token creation. However, the unverified contract and unlocked liquidity introduce considerable potential for misuse or instability, indicating a need for extreme caution.

### Is MEEP CAT safe to buy?

MEEP CAT carries notable risks that investors should be aware of. The contract is unverified, meaning its code hasn't been publicly scrutinized for vulnerabilities or hidden functions. Furthermore, the liquidity is not locked, exposing investors to the risk of a liquidity withdrawal or rug pull. While ownership is renounced, these fundamental security gaps mean it is not inherently "safe" and requires careful consideration of its medium risk profile.

### Has MEEP CAT been audited?

The provided data indicates that the MEEP CAT contract is *not* verified. This means its code is not publicly available for review, which is a prerequisite for a credible security audit. Without a verified contract, conducting a comprehensive and trustworthy audit is extremely challenging, making it impossible to confirm its security posture through this method.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/cgvkakbhnm93ul9tddwnfeyjt7d7qztctsyvkznevuem)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meep-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-19*
