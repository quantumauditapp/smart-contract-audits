---
token: Binance Agent
ticker: 4AGENT
network: bsc
risk_score: 51
status: medium
date: 2026-10-25
---

# Binance Agent (4AGENT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-agent-bsc)

---

## Audit Summary

The protocol utilizes an EIP-1167 minimal clone architecture, ensuring the implementation logic is immutable post-deployment. The token features complex tax and bonding mechanisms controlled by multiple external modules. While the core logic is fixed, the system relies heavily on privileged roles that can alter transfer rules, fee structures, and external contract dependencies, introducing significant centralization risks.

> **Final Recommendation:** To mitigate centralization risks, consider implementing a multi-signature wallet or a time-lock mechanism for all privileged functions that modify transfer rules or fee structures. This would provide transparency and prevent immediate, unilateral changes to the token's economic model.

Additionally, perform rigorous testing on the interaction between the token and external modules. Ensure that any address updates in postInitialize are validated against a whitelist or registry to prevent the redirection of token logic to malicious contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture leverages EIP-1167 clones for gas-efficient deployment, ensuring the implementation contract remains immutable. The codebase is modular, separating tax logic, bonding, and migration… |
| **Governance / Economics** | 7/10 | Low | Economic parameters such as fees and liquidity pool settings are entirely managed by privileged modules. The system allows for dynamic fee adjustments via onMigrate and onBondingTrade, which directly… |
| **Upgrades** | 8/10 | Low | The contract uses EIP-1167 minimal clones, which are inherently immutable. There is no upgradeability pattern implemented for the logic contract itself. While the token's behavior can be modified… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `CP-03` — Centralized Control Over Core Dependencies  *(Severity: High · Status: Unresolved)*

The postInitialize function allows a privileged module to change the addresses of contracts that the token relies on for every transfer. This means the controller can redirect token logic to arbitrary contracts at any time.

**Recommendation:** Restrict the ability to change core dependencies to a multi-signature governance contract and implement a time-lock for such updates.


### `CP-07` — Dynamic Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

Multiple privileged modules can modify the transfer fees and tax collection logic. This allows for arbitrary changes to the economic cost of trading the token.

**Recommendation:** Set hard caps on the maximum allowable fees to protect users from sudden, excessive tax increases.


### `CD-01` — Rounding Loss Due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

The _doDispatchFee function performs division before multiplication, which can lead to precision loss and minor discrepancies in fee calculations.

**Recommendation:** Reorder operations to perform multiplication before division to maintain higher precision.


### `CP-05` — Privileged Control Over Transfer Availability  *(Severity: Informational · Status: Unresolved)*

Privileged functions can toggle the 'swapping' state, which directly impacts whether transfers or sales are permitted. This gives the controller the ability to pause or restrict trading at will. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Document the intended use of these switches and ensure they are governed by a transparent process to prevent abuse.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 22.7% of supply. Of that, 10.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.6% in wallets, 2.8% in other contracts. 1,387 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,387 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $39K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $39K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5f6a...ffff`](https://bscscan.com/address/0x5f6a1ce1733fc4834a526798c0e8cf85137effff) |
| **Network** | BNB Chain |
| **Price** | $0.0001708 |
| **24h Volume** | $1.45M |
| **Liquidity** | $39.1K |
| **Volume / Liquidity** | 37.2× |
| **Token Age** | 3h |
| **Top-10 Holders** | 22.7% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 8734 buys / 6988 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd6da6b9cf8a2f3a602c4f9fb0ac58d08ce4a503b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-agent-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
