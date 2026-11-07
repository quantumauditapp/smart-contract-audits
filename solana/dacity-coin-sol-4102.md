---
token: Dacity Coin
ticker: DACITY
network: solana
risk_score: 22
status: low
date: 2026-11-07
---

# Dacity Coin (DACITY) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dacity-coin-sol-4102)

---

## Audit Summary

Dacity Coin is a standard SPL token with both mint and freeze authorities successfully revoked. The primary risks identified are the mutability of token metadata and a high volume-to-liquidity ratio suggesting potential wash trading. Holder concentration data was unavailable from the source.

> **Final Recommendation:** Investors should monitor the token metadata for unexpected changes given its mutable status. Due to the high volume-to-liquidity ratio, users should exercise caution regarding the authenticity of trading volume and account for potential slippage when executing large trades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the SPL… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $12,837 in liquidity, which is fully locked, preventing rug pulls via liquidity withdrawal. However, 7.6 External signals indicate a volume/liquidity ratio of 57.30, which… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL token mints in the EVM sense. The token metadata is currently mutable, allowing for potential changes to the token name or symbol. No other upgradeable… |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 57.30, which exceeds the 20x threshold, indicating a pattern associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting trading volume as a signal of organic demand.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 89% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $871K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EphCWc...BAGS`](https://solscan.io/account/EphCWcWcVcG7fjtGhvk2UjCUqhRcRfpuTbCyn5xoBAGS) |
| **Network** | Solana |
| **Price** | $0.00003762 |
| **24h Volume** | $719.7K |
| **Liquidity** | $15.4K |
| **Volume / Liquidity** | 46.6× |
| **Token Age** | 12h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13879 buys / 8887 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ab2t5dnxajrmkud7t636ey4m4nvv8xwiwts5vvpsxe2s)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dacity-coin-sol-4102)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
