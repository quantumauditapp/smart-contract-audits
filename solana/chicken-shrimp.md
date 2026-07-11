---
token: chicken shrimp
ticker: CS
network: solana
risk_score: 36
status: medium
date: 2026-06-21
---

# chicken shrimp (CS) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chicken-shrimp-sol)

---

## Audit Summary

This Solana SPL Token Mint, "chicken shrimp (CS)", exhibits a robust security posture based on available on-chain facts. Both mint and freeze authorities are revoked, ensuring a fixed supply and preventing account freezing. No high-risk Token-2022 extensions like Transfer Hooks or permanent delegates are active, and metadata is immutable. Holder concentration data was unavailable for analysis, which limits the assessment of market manipulation risks.

> **Final Recommendation:** Holders should periodically verify the on-chain status of the mint and freeze authorities to confirm they remain revoked. While current liquidity is moderate, monitor DEX liquidity and trading volume for any significant changes that could impact trade execution. If holder distribution data becomes available in the future, review it to assess potential market manipulation risks from concentrated holdings.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, indicating a fixed supply and immutability of account freezing. No Transfer… |
| **Governance / Economics** | 6/10 | Medium | The token currently has a liquidity of $26,407 with a 24-hour trading volume of $46,253. The volume-to-liquidity ratio is 1.75, which is within normal parameters and does not suggest wash trading.… |
| **Upgrades** | 8/10 | Low | The token's mint and freeze authorities are both revoked, meaning no further tokens can be minted and no accounts can be frozen. The token utilizes the Token-2022 program but does not have a Transfer… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9qwxah...pump`](https://solscan.io/account/9qwxahBxcgKyn5X7kZvkN7qxKZg6pkVD8Lo4URtopump) |
| **Network** | Solana |
| **Price** | $0.0003573 |
| **24h Volume** | $407.5K |
| **Liquidity** | $50.2K |
| **Volume / Liquidity** | 8.1× |
| **Token Age** | 3d |
| **Top-10 Holders** | 28.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16276 buys / 10700 sells |

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

### Is chicken shrimp a scam?

Based on the provided data, CS exhibits high-risk characteristics, notably an unverified contract and unlocked liquidity, which are common traits in fraudulent schemes. While ownership is renounced and there's no mint function, these do not fully mitigate the 'rug pull' risk or the lack of transparency from the unverified code. The project is tagged with a High Risk score of 47/100, suggesting significant speculative danger rather than outright confirming it as a scam without further investigation.

### Is chicken shrimp safe to buy?

No, chicken shrimp is not considered safe to buy based on the available security data. Key risk factors include an unverified contract, meaning its code cannot be transparently reviewed for exploits or malicious functions. Additionally, the liquidity is not locked, exposing investors to a potential 'rug pull' where liquidity can be withdrawn, crashing the token's value. The High Risk score of 47/100 underscores these significant vulnerabilities, indicating substantial speculative risk.

### Has chicken shrimp been audited?

The chicken shrimp contract is explicitly noted as 'Contract verified: False.' This means the source code has not been published or confirmed on the blockchain. Without a verified contract, conducting a reliable and transparent security audit is extremely challenging, if not impossible, for independent parties. Therefore, there is no public assurance of a formal audit or code review, leaving investors reliant on unverified claims or facing significant transparency issues.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/c3hajo5hfxwcgsoxzeqsqzbtfhcdxujb4qna4aqpq6xg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chicken-shrimp-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-21*
