---
token: Agent ID
ticker: .AI
network: bsc
risk_score: 50
status: medium
date: 2026-10-25
---

# Agent ID (.AI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agent-id-bsc-9ffd)

---

## Audit Summary

The BinanceAgentTaxToken is a complex, tax-enabled token implemented as an EIP-1167 minimal clone. The architecture relies heavily on external modules and privileged roles to manage token logic, fee structures, and liquidity operations. While the code is modular, the high degree of centralization and the ability for privileged addresses to alter core transfer logic and fee parameters introduce significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the token's transfer logic and fee structures are subject to change by privileged modules. We recommend that the project team implement a multi-signature wallet or a time-lock for all privileged functions to mitigate the risk of unauthorized or malicious state changes.

Furthermore, ensure that all external modules interacting with the token are audited and secured, as the token's functionality is fundamentally tied to their correct operation. Any future iterations should consider reducing the number of privileged functions to minimize the trust surface.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a modular architecture with clear separation between tax logic and token state. 7.1 Architecture is well-structured for a tax-token, though 7.2 Code Security is impacted by… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance risks are high due to the extensive control privileged roles have over fees and liquidity. Functions like onMigrate and onBondingTrade allow for dynamic fee… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is an EIP-1167 minimal clone, which is immutable by design. 7.8 Operations are stable, but the inability to upgrade the logic means any discovered… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `CP-03` — Centralized Control Over Core Logic  *(Severity: High · Status: Unresolved)*

The postInitialize function allows a privileged address to change the external contracts that the token relies on for core operations. This means the controller can redirect token logic at any time.

**Recommendation:** Restrict the ability to change core dependencies to a multi-signature wallet or implement a time-lock to provide transparency to users.


### `CP-07` — Dynamic Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

Multiple functions allow privileged addresses to modify transfer fees and tax collection parameters, which can be used to drain value from users or alter token economics unexpectedly.

**Recommendation:** Set hard caps on the maximum fee that can be charged and require a time-lock for any changes to fee structures.


### `CD-01` — Rounding Loss Due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

The _doDispatchFee function performs division before multiplication, which can lead to precision loss and minor discrepancies in fee calculations.

**Recommendation:** Reorder operations to perform multiplication before division to maintain precision.


### `CP-05` — Privileged Control Over Transfer Path  *(Severity: Informational · Status: Unresolved)*

Privileged functions can toggle the 'swapping' state, which directly impacts whether transfers or liquidity operations are permitted, effectively allowing the controller to freeze or manipulate trading. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement clear event logging for all state changes and limit the scope of the swapping switch to prevent arbitrary trading halts.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 49.4% of supply. Of that, 33.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.8% in wallets, 1.5% in other contracts. 310 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

310 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $470K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on four.meme, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 1 pools. Launch: launched on four.meme, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4783...4444`](https://bscscan.com/address/0x478318f7ae11140a30c6cd1940b9f9069b9f4444) |
| **Network** | BNB Chain |
| **Price** | $0.00001746 |
| **24h Volume** | $469.9K |
| **Liquidity** | $12.1K |
| **Volume / Liquidity** | 38.7× |
| **Token Age** | 3h |
| **Top-10 Holders** | 49.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2941 buys / 2390 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa45a639fa090c5b4f911889aac57a6c428e74586)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agent-id-bsc-9ffd)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
