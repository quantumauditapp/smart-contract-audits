---
token: Lity protocol
ticker: LITY
network: bsc
risk_score: 54
status: medium
date: 2026-10-11
---

# Lity protocol (LITY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lity-protocol-bsc)

---

## Audit Summary

The ERC20Template contract functions as an upgradeable ERC-20 token, utilizing a Beacon proxy pattern. Key functionalities include standard ERC-20 operations, along with capabilities for pausing transfers, minting new tokens, and managing transfer fees. Ownership of the implementation contract is renounced, rendering several privileged functions dormant. The audit identified a medium-severity issue related to a tautology in initialization and a potential for rounding loss, alongside two medium/low severity findings concerning the historical ability of the owner to modify fees and transfer limits, which are now inactive due to renounced ownership.

> **Final Recommendation:** It is recommended to thoroughly document the ownership status of the Beacon proxy controller to ensure transparency regarding upgrade capabilities. For the identified code quality issues, consider refactoring the `initialize` function to remove the tautology and review the `_isReflectionEligible` and `_update` functions to mitigate potential rounding losses by performing multiplication before division where applicable. While the renounced ownership of the implementation contract provides immutability for its current logic, understanding the full upgrade path via the Beacon is crucial for long-term security and trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements a standard ERC-20 token with additional features such as pausing, minting, and reflection mechanics. The code includes robust array management for fee receivers and adheres to… |
| **Governance / Economics** | 8/10 | Low | The economic model includes configurable transfer fees and potential for minting, which could historically be controlled by the owner (7.4 Economic). However, the renounced ownership of the… |
| **Upgrades** | 2/10 | High | The contract is deployed as a Beacon proxy, meaning its logic can be upgraded by changing the implementation address stored in the associated Beacon contract (7.7 Upgrades). While the implementation… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 2 Medium · 🟢 2 Low · ⚪ 5 Informational_

### `CD-02` — Tautology in Initialization Function  *(Severity: Medium · Status: Unresolved)*

The `initialize` function contains a tautological condition, meaning a logical expression that is always true. This indicates redundant code that does not affect the contract's logic but can be a sign of oversight or unnecessary complexity. While not a direct vulnerability, it can make the code harder to read and maintain.

**Recommendation:** Review the `initialize` function to identify and remove the tautological condition. Simplifying the logic will improve code clarity and maintainability without altering the intended functionality.


### `CP-07` — Privileged Address Could Change Transfer Fees  *(Severity: Medium · Status: Unresolved)*

Historically, the contract owner had the ability to modify the fees taken from token transfers by calling the `setFeeReceivers` function. This function allowed the owner to add, remove, or update fee recipient addresses and their respective shares. Additionally, the `mint` function could also influence fee-related state variables. However, it is important to note that the ownership of this contract has been renounced, meaning the `owner` address can no longer execute these functions, rendering this capability dormant.

**Recommendation:** While the `owner` can no longer change transfer fees due to renounced ownership, token holders should be aware that if ownership were ever to be reinstated or transferred, this function would allow a single entity to alter the token's economic model. For future projects, consider implementing a decentralized governance mechanism or a timelock for such critical parameter changes to enhance security and trust.


### `CD-01` — Rounding Loss from Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

The functions `_isReflectionEligible` and `_update` perform division operations before multiplication. In Solidity, integer division truncates any fractional part, leading to a loss of precision. If the division result is less than 1, it will be rounded down to 0, potentially causing minor discrepancies or unexpected behavior in calculations, especially with small numbers.

**Recommendation:** To prevent potential rounding losses, it is generally recommended to perform multiplication operations before division whenever possible. For example, instead of `(a / b) * c`, consider `(a * c) / b`. This ensures that precision is maintained for as long as possible during calculations.


### `CP-08` — Privileged Address Could Change Transfer or Wallet Limits  *(Severity: Low · Status: Unresolved)*

The `mint` function, which was restricted to the contract owner, had the capability to influence state variables such as `totalReflectionShares`, `reflectionShares`, `magnifiedReflectionPerShare`, and `magnifiedReflectionCorrections`. These variables are often used to manage token distribution, reflection mechanics, and could indirectly affect effective transfer or wallet limits within the token's logic. However, since the contract ownership has been renounced, the `owner` can no longer call the `mint` function, making this potential control dormant.

**Recommendation:** Given that ownership is renounced, the ability to change these parameters is currently inactive. In scenarios where such controls are active, it is recommended to implement robust access control, potentially involving multi-signature wallets or decentralized governance, to prevent a single entity from arbitrarily changing critical token parameters that affect user holdings or transfer behavior.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 26.7% of supply. Of that, 5.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.6% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 1.8%. 671 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

671 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $59K (DexScreener, all pools). 24h trading volume $202K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $59K of DEX liquidity across 1 pools. Launch: 67 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcd6a...0c0c`](https://bscscan.com/address/0xcd6a1b8f6e1498672724397de679a9ad19470c0c) |
| **Network** | BNB Chain |
| **Price** | $0.0005773 |
| **24h Volume** | $202.2K |
| **Liquidity** | $59.1K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 26.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 700 buys / 323 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x6f9963b69f62015f1f12be8a0fb73ca7c47ecbc2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lity-protocol-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
