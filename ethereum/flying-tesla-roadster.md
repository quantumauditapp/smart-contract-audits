---
token: Flying Tesla Roadster
ticker: FTR
network: ethereum
risk_score: 31
status: low
date: 2026-10-16
---

# Flying Tesla Roadster (FTR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 31/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flying-tesla-roadster-eth)

---

## Audit Summary

This audit covers an ERC-20 token contract. The contract's ownership has been renounced, which means no single entity can call owner-restricted functions like `recoverStuckToken`. The audit identified two findings: a High-severity issue related to misleading return values in core transfer functions and a Low-severity issue concerning potential rounding loss in a liquidity provision function.

> **Final Recommendation:** It is crucial to address the High-severity finding regarding misleading return values in the `transfer` and `transferFrom` functions. These functions should accurately reflect the success or failure of the underlying operations to prevent external systems from making incorrect assumptions. Additionally, the `provideLiquidity` function should be reviewed to reorder arithmetic operations, performing multiplication before division, to mitigate potential rounding losses and ensure precise calculations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract implements the ERC-20 standard, providing essential token functionalities (7.1 Architecture). Ownership has been renounced, making owner-restricted functions like `renounceOwnership` and… |
| **Governance / Economics** | 9/10 | Low | The contract exhibits a strong security posture regarding governance and economic control due to the renounced ownership (7.5 Governance). This means no single address can exert privileged control… |
| **Upgrades** | 10/10 | Low | The contract is not implemented as a proxy and does not include any upgrade mechanisms (7.7 Upgrades). This design choice eliminates risks associated with upgradeability, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — TeamFinance |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 6 Informational_

### `CD-02` — Misleading Return Values in Core Transfer Functions  *(Severity: High · Status: Unresolved)*

Several critical functions, including `transfer` and `transferFrom`, are designed to return a `true` value regardless of whether the underlying transfer operation actually succeeded or failed. This means that external systems or users relying on the return value to confirm a successful token transfer might be misled, potentially leading to incorrect assumptions about transaction outcomes. The `_transfer` function, which is called by `transfer` and `transferFrom`, also does not return a boolean, but `transfer` and `transferFrom` explicitly return `true`.

**Recommendation:** The return logic for `transfer`, `transferFrom`, and other affected functions should be revised. These functions should accurately reflect the success or failure of the operation by returning `true` only upon successful completion and `false` or reverting on failure. This ensures that external callers can reliably determine the outcome of their transactions.


### `CD-01` — Potential for Small Value Loss in Liquidity Provision  *(Severity: Low · Status: Unresolved)*

The `provideLiquidity` function might cause a very small amount of tokens to be lost due to how calculations are performed. When the contract divides a number before multiplying it, tiny fractions can be rounded down and lost, which could slightly reduce the amount of tokens received by the user or held by the contract in certain scenarios.

**Recommendation:** To prevent this minor loss, the calculation in `provideLiquidity` should be reordered to perform multiplication before division. This ensures that intermediate results retain higher precision, minimizing rounding errors.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 8.6% of supply. Of that, 4.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.4% in wallets, 0.0% in other contracts. 490 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

490 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked, lock term not visible  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is held by TeamFinance, but the lock's end date is not published in the data we can read — its duration is unverified. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $233K (DexScreener, all pools). 24h trading volume $2.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $233K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb319...9000`](https://etherscan.io/address/0xb3198fd8d281c8536adf2fe00fe2f985fe619000) |
| **Network** | Ethereum |
| **Price** | $0.005586 |
| **24h Volume** | $2.03M |
| **Liquidity** | $233.0K |
| **Volume / Liquidity** | 8.7× |
| **Token Age** | 16h |
| **Top-10 Holders** | 8.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1670 buys / 666 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xaaf40568a70305979408fe38e913f883034b0f4d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flying-tesla-roadster-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
