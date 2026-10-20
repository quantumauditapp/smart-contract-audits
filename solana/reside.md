---
token: Reside
ticker: RESI
network: solana
risk_score: 15
status: low
date: 2026-10-01
---

# Reside (RESI) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/reside-sol)

---

## Audit Summary

The Reside (RESI) SPL Token Mint exhibits a low overall risk profile. Both the mint and freeze authorities have been revoked, ensuring a fixed supply and non-custodial operations. The primary identified risk is the mutability of token metadata, allowing for potential changes to its name, symbol, or image. Holder distribution data was unavailable, preventing an assessment of concentration risk.

> **Final Recommendation:** Before interacting with the token, verify the current metadata (name, symbol, image) on-chain to ensure it aligns with expectations. Monitor for any changes to this metadata post-acquisition. Due to the unavailability of holder distribution data, consider the potential for concentrated holdings and associated market volatility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Reside (RESI) token is implemented using the `spl-token-2022` program. Both the Mint Authority and Freeze Authority have been revoked, indicating that no new tokens can be minted and no holder… |
| **Governance / Economics** | 9/10 | Low | The token has a total DEX liquidity of $36,625, with a 24-hour trading volume of $256,403, resulting in a Volume/Liquidity Ratio of 7.00. This indicates active trading relative to the available… |
| **Upgrades** | 10/10 | Low | The token's core functionalities are immutable due to the revocation of both Mint and Freeze Authorities. As an `spl-token-2022` token, it supports various extensions, but none that allow for… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The `metadata_mutable` flag is true, meaning the token's name, symbol, or image can be changed post-launch. This could lead to confusion or misrepresentation if the branding is altered unexpectedly.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding. Monitor for any changes to the token's metadata after acquisition.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 90% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $291K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $41K of DEX liquidity across 7 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`reside...5q1y`](https://solscan.io/account/resideK2Ejv9apu1op2VBv89poumxCDCs8nzBxQ5q1y) |
| **Network** | Solana |
| **Price** | $0.0001251 |
| **24h Volume** | $264.8K |
| **Liquidity** | $37.2K |
| **Volume / Liquidity** | 7.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2444 buys / 2186 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/atwk3wi3u2u87n6c7gndmiphkqgwjrm2c1qlxr3z8dbj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/reside-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
