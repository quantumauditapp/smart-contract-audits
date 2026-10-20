---
token: TapeFour
ticker: TAPEFOUR
network: bsc
risk_score: 51
status: medium
date: 2026-10-20
---

# TapeFour (TAPEFOUR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tapefour-bsc)

---

## Audit Summary

The protocol implements a highly modular token architecture using EIP-1167 clones. While the core logic is immutable, the token relies heavily on external modules for transfer rules, fee management, and liquidity operations. The centralization of control in privileged modules presents significant trust requirements for token holders.

> **Final Recommendation:** Users should exercise caution regarding the high degree of centralization inherent in the module-based design. Ensure that the addresses controlling the tokenModule and taxVault are transparent and governed by secure, multi-signature wallets or time-locked contracts to mitigate the risk of arbitrary fee or transfer rule changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes EIP-1167 minimal clones, ensuring the implementation logic cannot be altered post-deployment. 7.1 Architecture is robust for gas efficiency but relies on complex external… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic parameters are entirely managed by external modules, allowing for dynamic fee adjustments and liquidity pool manipulation. 7.5 Governance is implicit, relying on the integrity of the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported due to the EIP-1167 clone pattern, which fixes the implementation logic permanently. 7.8 Operations are stable, as the contract state is managed through internal… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.8% (≈ permanent lock) |
| **LP Locked** | 99.8% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `CP-03` — Privileged Module Can Redirect Token Logic  *(Severity: High · Status: Unresolved)*

The postInitialize function allows the tokenModule to change the addresses of critical dependencies such as the quote, shareHolderManager, and tokenHelper. Because transfers depend on these contracts, the controller of the tokenModule can effectively redirect or break token functionality.

**Recommendation:** Implement a time-lock mechanism for changing critical dependency addresses to allow users to exit if they disagree with the changes.


### `CP-07` — Dynamic Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

Functions like onMigrate and onBondingTrade allow privileged modules to modify fee parameters (e.g., feeBurn, feeLiquidity). This allows the protocol to change the economic impact on users without prior notice.

**Recommendation:** Define hard caps on fee percentages within the contract to prevent excessive taxation by privileged modules.


### `CD-01` — Rounding Loss from Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

In the _doDispatchFee function, performing division before multiplication can lead to precision loss, resulting in slightly inaccurate fee calculations.

**Recommendation:** Reorder arithmetic operations to perform multiplication before division, ensuring higher precision.


### `CP-05` — Privileged Control Over Transfer Path  *(Severity: Informational · Status: Unresolved)*

The 'swapping' state variable, which can be toggled by internal functions like _swapForQuoteWrapped, acts as a switch for transfer operations. Privileged modules can influence this state, potentially blocking transfers or sales. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Restrict the ability to toggle transfer-blocking switches to a decentralized governance process rather than a single module address.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.0% of supply. Of that, 3.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.5% in wallets, 85.3% in other contracts. 913 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

913 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.8% of the pool's LP is burned or time-locked. 99.8% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.2% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $52K (DexScreener, all pools). 24h trading volume $711K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $52K of DEX liquidity across 3 pools. Launch: 4 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe6df...ffff`](https://bscscan.com/address/0xe6df1162a3243e3064e43f187ea14808ddfdffff) |
| **Network** | BNB Chain |
| **Price** | $0.0008218 |
| **24h Volume** | $710.8K |
| **Liquidity** | $51.8K |
| **Volume / Liquidity** | 13.7× |
| **Token Age** | 4d |
| **Top-10 Holders** | 91.0% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 3095 buys / 2599 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x341e11081ce453ecd8f9c52d79b3fdcadf201c3c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tapefour-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
