---
token: bibi.ai
ticker: BIBI
network: bsc
risk_score: 53
status: medium
date: 2026-10-25
---

# bibi.ai (BIBI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bibiai-bsc-4056)

---

## Audit Summary

The BinanceAgentTaxToken is a complex, modular token implementation deployed via EIP-1167 minimal clones. The architecture relies heavily on external modules and privileged roles to manage tax logic, liquidity, and state transitions. While the code structure is modular, the high degree of centralization and the ability for privileged modules to alter core transfer logic and fee structures present significant risks to token holders.

> **Final Recommendation:** Token holders should be aware that the contract's behavior, including transfer fees and liquidity mechanics, can be modified at any time by the designated module addresses. We recommend that the protocol implement a timelock on all privileged functions to provide transparency and allow users to exit before significant logic changes occur.

Furthermore, the protocol should consider moving toward a more decentralized governance model to reduce the risk associated with the current centralized control of the token's economic parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a modular architecture to handle complex tax and bonding logic. It correctly implements standard ERC-20 interfaces and uses OpenZeppelin-style initialization patterns. However… |
| **Governance / Economics** | 7/10 | Low | Economic parameters are entirely controlled by privileged modules, allowing for arbitrary changes to fees and transfer rules. 7.4 Economic: Fees and tax collection are dynamic and mutable. 7.5… |
| **Upgrades** | 8/10 | Low | The contract is deployed as an EIP-1167 minimal clone, meaning the implementation logic is immutable once deployed. 7.7 Upgrades: No proxy upgrade mechanism exists. 7.8 Operations: Operational… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `CP-03` — Centralized Control Over Core Logic  *(Severity: High · Status: Unresolved)*

The 'postInitialize' function allows a privileged module to change the addresses of external contracts that the token relies on for every transfer. This means the controller can redirect token logic to arbitrary contracts.

**Recommendation:** Implement a multi-signature wallet or a timelock for the 'postInitialize' function to prevent unilateral changes to core dependencies.


### `CP-07` — Mutable Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The transfer fees are not fixed and can be adjusted by various privileged modules. This allows the controller to increase fees to potentially prohibitive levels.

**Recommendation:** Set a hard cap on the maximum allowable fee percentage to protect users from sudden, extreme fee increases.


### `CD-01` — Rounding Loss in Fee Calculation  *(Severity: Low · Status: Unresolved)*

The '_doDispatchFee' function performs division before multiplication, which can lead to precision loss and minor discrepancies in fee collection.

**Recommendation:** Reorder operations to perform multiplication before division to maintain higher precision.


### `CP-05` — Privileged Control Over Transfer Availability  *(Severity: Informational · Status: Unresolved)*

Functions like '_addLiquidityWithQuoteWrapped' and others act as switches that can enable or disable specific transfer paths. A privileged controller can effectively halt trading or liquidity operations at will. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Restrict the use of these switches to emergency scenarios only and document the conditions under which they may be used.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.4% of supply. Of that, 25.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.1% in wallets, 2.8% in other contracts. 372 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

372 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $590K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $18K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x967b...ffff`](https://bscscan.com/address/0x967b26d369571a8c5a035aaac1f4b1594287ffff) |
| **Network** | BNB Chain |
| **Price** | $0.00003672 |
| **24h Volume** | $590.0K |
| **Liquidity** | $17.8K |
| **Volume / Liquidity** | 33.2× |
| **Token Age** | 3h |
| **Top-10 Holders** | 42.4% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 3219 buys / 3479 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc9a6133563b66ac41ed7b8c766ea3c0af1c42b88)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bibiai-bsc-4056)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
