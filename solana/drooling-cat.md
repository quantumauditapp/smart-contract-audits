---
token: drooling cat
ticker: DROOLING
network: solana
risk_score: 54
status: high
date: 2026-06-18
---

# drooling cat (DROOLING) — Smart Contract Security Analysis | Solana

> **Risk Score: 54/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/drooling-cat-sol)

---

## Audit Summary

This audit of the 'drooling cat' SPL Token Mint found no critical or high-severity issues based on the available on-chain facts and third-party risk data. Key authorities such as Mint and Freeze are revoked, and no adverse flags were reported by a third-party risk registry. Holder distribution data was unavailable, preventing a full assessment of supply concentration.

> **Final Recommendation:** Verify on-chain that the Mint Authority and Freeze Authority remain revoked to ensure supply immutability and prevent account freezing. Monitor DEX liquidity and trading volume for any significant changes that could impact market stability. If holder concentration data becomes available, review it to assess potential risks from large holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority are revoked, indicating that no new tokens can be minted and no existing accounts can be… |
| **Governance / Economics** | 2/10 | High | DEX liquidity for the token is $147,143, which is sufficient for moderate trading. The 24-hour volume is $581,153, resulting in a Volume/Liquidity Ratio of 3.95, which is considered normal and does… |
| **Upgrades** | 5/10 | Medium | The token's core authorities, Mint Authority and Freeze Authority, are both revoked, meaning these critical controls cannot be changed or re-enabled. The token uses the spl-token-2022 program but… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`B6f27E...pump`](https://solscan.io/account/B6f27ETGcjgGNB1fqULJbXVmw9FnL8HgBp7R83hmpump) |
| **Network** | Solana |
| **Price** | $0.0002027 |
| **24h Volume** | $125.0K |
| **Liquidity** | $60.7K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 20d |
| **Top-10 Holders** | 32.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5818 buys / 5367 sells |

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
