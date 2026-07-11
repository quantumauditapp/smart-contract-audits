---
token: UFC Freedom 250
ticker: UFC250
network: solana
risk_score: 66
status: high
date: 2026-06-10
---

# UFC Freedom 250 (UFC250) — Smart Contract Security Analysis | Solana

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ufc-freedom-250-sol)

---

## Audit Summary

This audit of the UFC Freedom 250 (UFC250) SPL token mint identifies significant risks primarily due to very low liquidity and the nascent age of its DEX trading pair. While core mint authorities are appropriately revoked and metadata is immutable, the token's market stability is highly uncertain. Holder concentration data was unavailable for analysis.

> **Final Recommendation:** Potential holders should exercise extreme caution due to the very low liquidity ($7,871) and the extremely young age of the DEX pair (3 days). These factors indicate high volatility and difficulty in exiting positions without significant loss. It is recommended to wait for the token to establish a more substantial liquidity pool and a longer trading history before considering any significant investment. Verify the token's market stability and growth over a longer period.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The UFC Freedom 250 token is implemented using the spl-token-2022 program. Critically, both the Mint Authority and Freeze Authority have been revoked, preventing the creation of new tokens or the… |
| **Governance / Economics** | 2/10 | High | The token exhibits high economic risk due to its market characteristics. Total DEX liquidity stands at a very low $7,871, indicating that even small trades could experience severe slippage. The… |
| **Upgrades** | 6/10 | Medium | The UFC Freedom 250 token mint has a strong security posture regarding potential post-launch modifications. Both the Mint Authority and Freeze Authority have been permanently revoked, ensuring that… |

## Security Findings

_🟠 1 High · 🟡 1 Medium_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $7,871. Slippage will be severe; large positions cannot be exited without significant loss. (Fact: Liquidity (USD): $7,871)

**Recommendation:** Account for the severe slippage in any swap calculation and consider the difficulty of exiting large positions. Avoid significant investments until liquidity materially improves.


### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 3 days ago. Insufficient track record to assess team or holder behaviour. (Fact: Pair Age (days): 3)

**Recommendation:** Exercise caution due to the lack of historical data. Monitor the token's performance, team activity, and community engagement over a longer period before making investment decisions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CWBiRH...pump`](https://solscan.io/account/CWBiRHPu2jQYjybiDtb7FnCFr9XWmmPXzGsPirC3pump) |
| **Network** | Solana |
| **Price** | $0.00009756 |
| **24h Volume** | $92.8K |
| **Liquidity** | $21.7K |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 61.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3180 buys / 1696 sells |

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
