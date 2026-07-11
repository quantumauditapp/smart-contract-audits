---
token: Pomni
ticker: POMNI
network: solana
risk_score: 45
status: medium
date: 2026-06-15
---

# Pomni (POMNI) — Smart Contract Security Analysis | Solana

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pomni-sol)

---

## Audit Summary

No critical or high-severity issues were identified based on the available on-chain data and external security signals. The token's mint and freeze authorities are revoked, indicating a fixed supply and unfreezable accounts. However, holder concentration data was unavailable, preventing a full assessment of distribution risk, though RugCheck.xyz noted 'Single holder ownership'.

> **Final Recommendation:** The Pomni token demonstrates a strong security posture regarding its core authorities, with both mint and freeze authorities revoked. This ensures a fixed supply and prevents arbitrary freezing of user funds. However, the absence of detailed holder concentration data means that potential risks from whale holdings cannot be fully assessed. Users should consider the 'Single holder ownership' label from RugCheck.xyz, which suggests a concentrated ownership structure, and understand its implications for market stability before interacting with the token. For enhanced due diligence, a Premium Deploy option could include deeper off-chain analysis of the project team and community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Pomni token is implemented using the spl-token-2022 program. A key security strength is that both the mint authority and freeze authority have been revoked, meaning no new tokens can be created… |
| **Governance / Economics** | 5/10 | Medium | The token has a total DEX liquidity of $25,919 with a 24-hour volume of $22,940, resulting in a normal Volume/Liquidity Ratio of 0.89. The DEX pair is 94 days old, indicating some track record. While… |
| **Upgrades** | 8/10 | Low | The token's core parameters are immutable due to the revocation of both mint and freeze authorities. There are no active Token-2022 extensions like transfer hooks or default frozen accounts that… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DSSXu6...pump`](https://solscan.io/account/DSSXu6XbYDgWnjMVzagcVF9QpVWXY2H9iexAc4mpump) |
| **Network** | Solana |
| **Price** | $0.0001745 |
| **24h Volume** | $407.1K |
| **Liquidity** | $37.5K |
| **Volume / Liquidity** | 10.8× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 30.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 17714 buys / 3573 sells |

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

### Is Pomni a scam?

While Pomni exhibits positive traits like renounced ownership and no mint function, mitigating some direct developer-controlled scam vectors, the unverified contract and unlocked liquidity introduce significant scam potential. The inability to review the code and the risk of liquidity withdrawal mean investors face elevated risks. The medium risk score of 37/100 indicates that caution is strongly advised due to these unaddressed vulnerabilities.

### Is Pomni safe to buy?

Pomni carries considerable risk due to an unverified contract and unlocked liquidity. These factors prevent independent code review and expose the project to a potential rug pull by liquidity providers. Given its medium risk score (37/100) and relatively low liquidity compared to trading volume, which can lead to high volatility and slippage, potential investors should exercise extreme caution and acknowledge the elevated risk of capital loss.

### Has Pomni been audited?

The Pomni contract is listed as unverified, meaning its source code has not been published or confirmed on the blockchain explorer. Consequently, it has not undergone a public, independent audit process based on available on-chain data. Investors cannot independently review its code for security vulnerabilities or malicious functions, which significantly elevates the project's risk profile compared to audited and verified contracts.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/ajjzxic3gxotlkqfnyk4qmgd4k2dbpinpzb7gf5fhx2x)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pomni-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-15*
