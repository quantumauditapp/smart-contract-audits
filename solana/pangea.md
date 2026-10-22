---
token: Pangea
ticker: PANGEA
network: solana
risk_score: 64
status: medium
date: 2026-10-22
---

# Pangea (PANGEA) — Smart Contract Security Analysis | Solana

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pangea-sol)

---

## Audit Summary

The Pangea token (PANGEA) utilizes the Token-2022 program with immutable metadata and a locked liquidity pool. However, the mint authority remains active, allowing for potential supply inflation, and the high volume-to-liquidity ratio suggests significant wash-trading activity. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the mint authority address (HWkHoSCUzS7DorKswzNEfxgJUwCE9zYLF2rNePFsQ8J1) for any activity, as it currently holds the power to dilute the supply. Verify on-chain that this authority is set to null before considering the token supply fixed.

Due to the high volume-to-liquidity ratio, exercise caution regarding potential price manipulation. Use DEX tools to track real-time liquidity movements and avoid relying on 24-hour volume metrics as a proxy for organic demand.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is deployed on the Token-2022 program, ensuring 7.1 Architecture compliance. 7.2 Code Security is maintained via immutable extensions, including non-mutable metadata and balance settings.… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is challenged by a volume/liquidity ratio of 35.14, indicating potential wash trading. 7.6 External market data shows $149,673 in liquidity, with 97% of pool assets permanently… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are restricted by the immutability of the token program extensions. Metadata, transfer fees, and hooks are configured as non-mutable, preventing post-launch changes to branding or… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 6 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is HWkHoSCUzS7DorKswzNEfxgJUwCE9zYLF2rNePFsQ8J1. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 35.14x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for the fee in any swap calculation.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

97.0% of the pool's LP is burned or time-locked. 97.0% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 2.7% is held, unlocked, by 3 address(es) other than the pool's creator. This assessment covers the main pool, which holds 48% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $305K (DexScreener, all pools). 24h trading volume $6.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $305K of DEX liquidity across 10 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`JAFqCQ...Y6ea`](https://solscan.io/account/JAFqCQSpy5YinrsmixWSMaD7jTn4MytJRkyWvYPnY6ea) |
| **Network** | Solana |
| **Price** | $0.00182 |
| **24h Volume** | $5.23M |
| **Liquidity** | $147.5K |
| **Volume / Liquidity** | 35.4× |
| **Token Age** | 10h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13381 buys / 12297 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/6yknbt32e2m9sf9jpbgwetd5qqgpvedndgnn87a9addr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pangea-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
