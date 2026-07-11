---
token: drooling cat
ticker: DROOLING
network: solana
risk_score: 35
status: medium
date: 2026-06-18
---

# drooling cat (DROOLING) — Smart Contract Security Analysis | Solana

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/drooling-cat-sol)

---

## Audit Summary

This audit of the drooling cat (drooling) SPL token mint found no critical or high-severity issues based on the available on-chain data and external security signals. The mint authority and freeze authority are both revoked, indicating a fixed supply and immutability of account states. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Based on the available data, the drooling cat token appears to have a robust security posture regarding its mint and freeze authorities, which are both revoked. However, the absence of holder concentration data means that potential risks related to whale concentration cannot be assessed. Users should be aware of the high volume-to-liquidity ratio, which, while not triggering a wash trading flag, suggests active trading relative to available liquidity. For a more comprehensive understanding, it is recommended to monitor holder distribution once data becomes available.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The drooling cat token is an SPL Token-2022 mint with a supply of 999,685,315.534856 tokens (6 decimals). Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be… |
| **Governance / Economics** | 7/10 | Low | The token exhibits a liquidity of $146,291 USD on DEXs, with a 24-hour trading volume of $813,518 USD. The volume-to-liquidity ratio is 5.56, which is noted as high (>5) in the fact block, but does… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority for the drooling cat token have both been revoked, meaning the token's supply is fixed and no accounts can be frozen by an external authority. The token is an… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`B6f27E...pump`](https://solscan.io/account/B6f27ETGcjgGNB1fqULJbXVmw9FnL8HgBp7R83hmpump) |
| **Network** | Solana |
| **Price** | $0.0007941 |
| **24h Volume** | $1.10M |
| **Liquidity** | $88.3K |
| **Volume / Liquidity** | 12.5× |
| **Token Age** | 20d |
| **Top-10 Holders** | 24.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5818 buys / 5367 sells |

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

### Is drooling cat a scam?

Based solely on the provided data, a definitive 'scam' label cannot be assigned. The token benefits from renounced ownership and no mint function, which reduce common developer-initiated risks. However, the contract remains unverified, and liquidity is not locked, posing significant vulnerabilities that could be exploited. These factors contribute to its 'Medium Risk' score of 32/100, suggesting a cautious approach is warranted rather than an outright dismissal or endorsement.

### Is drooling cat safe to buy?

The drooling cat token carries a Medium Risk score of 32/100, indicating it is not inherently safe to buy without understanding specific risks. The most critical concerns are the unlocked liquidity, which exposes holders to potential rug pulls if liquidity providers withdraw funds, and the unverified contract, which prevents clear public scrutiny of its code. While ownership is renounced, these unmitigated financial and technical vulnerabilities necessitate extreme caution for potential buyers.

### Has drooling cat been audited?

The contract for drooling cat has not been verified. This means the source code publicly available for review cannot be definitively confirmed as matching the deployed on-chain code. Consequently, while an audit might theoretically exist, without contract verification, its findings cannot be reliably confirmed against the operational token contract. This lack of transparency is a significant concern for security assessment.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/2mqyy3lfjcnauyfufynlgtlcxmb6m2shxqgv2mhx7mpy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/drooling-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-18*
