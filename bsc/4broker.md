---
token: 4Broker
ticker: 4BROKER
network: bsc
risk_score: 49
status: medium
date: 2026-10-29
---

# 4Broker (4BROKER) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/4broker-bsc)

---

## Audit Summary

The BinanceAgentTaxToken is a complex, modular token implementation deployed as an EIP-1167 minimal clone. It relies heavily on external modules for core logic, including fee management, liquidity operations, and transfer rules. While the architecture is modular, the high degree of centralization and the ability for privileged modules to alter fundamental transfer behavior and redirect logic creates significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the token's behavior is subject to change by the controlling modules. We recommend that the project team implement a multi-signature wallet or a decentralized governance contract to manage the privileged module addresses to mitigate the risk of a single point of failure.

Furthermore, ensure that all external modules are audited and that their source code is verified. The reliance on external contracts for core logic requires that these modules be treated as part of the token's critical infrastructure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a robust modular architecture for handling complex tax and liquidity logic. 7.1 Architecture: EIP-1167 clone pattern ensures immutable logic. 7.2 Code Security: Standard… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic: The token features dynamic fee structures and automated liquidity management. 7.5 Governance: Control is entirely delegated to external modules, meaning the 'governance' is effectively… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The implementation is immutable due to the EIP-1167 clone pattern. 7.8 Operations: While the token logic cannot be upgraded, the behavior of the token can be significantly altered by… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `CP-03` — Centralized Control Over Core Logic  *(Severity: High · Status: Unresolved)*

The postInitialize function allows a privileged 'tokenmodule' to change the addresses of core contracts that the token depends on for every transfer. This means the controller can redirect token logic to arbitrary contracts.

**Recommendation:** Restrict the ability to change core dependencies to a time-locked governance contract or a multi-signature wallet.


### `CP-07` — Dynamic Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

Multiple privileged modules (migratemodule, shareholdermanager, taxvault, vault) have the authority to change transfer fees. This allows for the potential to set fees to excessive levels.

**Recommendation:** Set hard caps on the maximum fee that can be charged to protect users from sudden, extreme fee increases.


### `CD-01` — Rounding Loss in Fee Calculation  *(Severity: Low · Status: Unresolved)*

The _doDispatchFee function performs division before multiplication, which can lead to precision loss and minor inaccuracies in fee distribution.

**Recommendation:** Reorder operations to perform multiplication before division to maintain higher precision.


### `CP-05` — Privileged Control Over Transfer Availability  *(Severity: Informational · Status: Unresolved)*

Privileged functions like _addLiquidityWithQuoteWrapped can toggle the 'swapping' state, which acts as a switch for whether certain transfers or sales are permitted. This gives the controller the power to halt trading or liquidity operations. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement clear, transparent rules for when these switches can be toggled to prevent arbitrary trading halts.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 60.1% of supply. Of that, 3.7% burned, 42.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.0% in wallets, 4.8% in other contracts. 1,146 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,146 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $156K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $11K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7436...ffff`](https://bscscan.com/address/0x74361e7d05b6801c3b7d7f1cce9aa0d557d5ffff) |
| **Network** | BNB Chain |
| **Price** | $0.00001475 |
| **24h Volume** | $156.4K |
| **Liquidity** | $11.0K |
| **Volume / Liquidity** | 14.3× |
| **Token Age** | 19h |
| **Top-10 Holders** | 60.1% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 3121 buys / 2496 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb35d5d6f721a25c3956e4509a65c931c19c29a3c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/4broker-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
