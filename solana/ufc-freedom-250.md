---
token: UFC Freedom 250
ticker: UFC250
network: solana
risk_score: 82
status: critical
date: 2026-06-10
---

# UFC Freedom 250 (UFC250) — Smart Contract Security Analysis | Solana

> **Risk Score: 82/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ufc-freedom-250-sol)

---

## Audit Summary

This SPL Token-2022 mint exhibits strong security configurations with both Mint and Freeze authorities permanently revoked, ensuring a fixed supply and unfreezable accounts. No transfer hooks or default frozen account states are active, and metadata is immutable. However, critical market data such as holder concentration and DEX liquidity were unavailable, preventing a comprehensive economic risk assessment. A third-party registry flagged low liquidity.

> **Final Recommendation:** Prospective holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the immutability of supply and account states. Due to the absence of DEX market data and holder distribution information, it is crucial to monitor the token's market activity closely for the establishment of liquidity and to assess holder concentration once data becomes available. Exercise caution, as a third-party registry has indicated low liquidity, which could impact trade execution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | This is an SPL Token-2022 mint. Both the Mint Authority and Freeze Authority are revoked (None), indicating a fixed supply and that no accounts can be frozen post-issuance. The token has a supply of… |
| **Governance / Economics** | 1/10 | High | Holder concentration data is unavailable, preventing an assessment of supply distribution. Similarly, no DEX pair data is available, meaning liquidity and trading volume cannot be determined. A… |
| **Upgrades** | 5/10 | Medium | The Mint Authority and Freeze Authority are both revoked, meaning the token's supply cannot be altered and no accounts can be frozen. The token program is spl-token-2022, and no Transfer Hook is… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CWBiRH...pump`](https://solscan.io/account/CWBiRHPu2jQYjybiDtb7FnCFr9XWmmPXzGsPirC3pump) |
| **Network** | Solana |
| **Price** | $0.00000208 |
| **24h Volume** | $0 |
| **Liquidity** | $3.4K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 98.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3180 buys / 1696 sells |

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

### Is UFC Freedom 250 a scam?

The data indicates UFC Freedom 250 exhibits several characteristics commonly associated with high-risk or potentially fraudulent projects. Its Critical Risk score of 75/100, unverified contract, unrenounced ownership, and unlocked liquidity are significant red flags. While we cannot definitively label it a 'scam' without intent, these technical findings strongly suggest extreme caution is warranted due to the inherent vulnerabilities and potential for malicious actions.

### Is UFC Freedom 250 safe to buy?

UFC Freedom 250 presents substantial safety concerns for potential buyers. The lack of contract verification means its code cannot be publicly audited for vulnerabilities or malicious functions. Unrenounced ownership allows the deployer to retain control, potentially altering the contract or affecting holder funds. Most critically, unlocked liquidity enables the team to remove funds, risking a complete loss for investors. These factors contribute to its critical risk score.

### Has UFC Freedom 250 been audited?

No, UFC Freedom 250 has not been audited. Its contract remains unverified, meaning the deployed code has not been publicly matched with source code. This lack of transparency is a prerequisite for any credible security audit, which examines smart contract code for vulnerabilities and potential exploits. Without verification, an audit is not possible, leaving the contract's integrity unknown.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/56garmqsyeky6oynuygocuizvcvddqsibube1q7eylfh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ufc-freedom-250-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
