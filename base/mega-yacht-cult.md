---
token: MEGA YACHT CULT
ticker: MYC
network: base
risk_score: 76
status: high
date: 2026-10-10
---

# MEGA YACHT CULT (MYC) — Smart Contract Security Analysis | Base

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mega-yacht-cult-base)

---

## Audit Summary

The MegaYachtCult contract is an ERC-20 token with advanced features including taxation, fee distribution, and reentrancy protection. The contract exhibits a high degree of centralized control, with the owner having extensive power over critical parameters such as swap routers, liquidity ownership, and fee configurations. Key findings include the owner's ability to replace critical external contracts, control transfer switches, and modify transfer fees, alongside a reentrancy vulnerability in the `_transfer` function and potential rounding issues.

> **Final Recommendation:** It is strongly recommended to decentralize control over critical functions where possible, or implement a multi-signature wallet for the owner address to mitigate single points of failure. Review all owner-controlled parameters, especially those affecting external contract interactions and fee mechanisms, to ensure they align with the project's long-term vision and community expectations. Address the identified reentrancy vulnerability by ensuring all state changes occur before external calls in the `_transfer` function.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The MegaYachtCult token incorporates robust features like ERC20Votes, ERC20Permit, and a ReentrancyGuard, enhancing its functionality and basic security posture (7.2 Code Security). However, the… |
| **Governance / Economics** | 3/10 | High | The economic model of the MegaYachtCult token is highly centralized, with the owner retaining extensive control over key financial mechanisms (7.4 Economic, 7.5 Governance). The owner can dynamically… |
| **Upgrades** | 6/10 | Medium | The MegaYachtCult contract is not designed as an upgradeable proxy, meaning its core logic cannot be changed after deployment (7.7 Upgrades). This provides immutability for the contract's fundamental… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 98.1% — Null Address, UNCX |
| **Top-1 Unlocked Holder** | 1.0% |

## Security Findings

_🟠 2 High · 🟡 3 Medium · 🟢 2 Low · ⚪ 5 Informational_

### `CP-03` — Owner can change critical external contracts, affecting how tokens are swapped or managed.  *(Severity: High · Status: Unresolved)*

The owner of the MegaYachtCult token has the power to change the addresses of external contracts that are crucial for token operations. Specifically, the `setSwapRouter` function allows the owner to replace the contract used for swapping tokens, and `setLiquidityOwner` allows changing the address responsible for liquidity. If these addresses are changed to malicious contracts, it could lead to funds being misdirected or token transfers failing.

**Recommendation:** Token holders should be aware that the owner can unilaterally change these critical external contracts. Consider advocating for these functions to be controlled by a multi-signature wallet or a time-locked mechanism to prevent immediate, unauthorized changes.


### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 56.4% of supply. Of that, 6.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 38.3% in wallets, 11.3% in other contracts. The deployer/owner wallet itself holds 26.2%. A holder that also controls the contract can sell into its own liquidity. 1,860 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `CD-02` — Risk of reentrancy during token transfers involving ETH.  *(Severity: Medium · Status: Unresolved)*

The `_transfer` function, which handles token movements, might update its internal state *after* making an external call that sends ETH. This creates a reentrancy vulnerability. If a malicious contract receives ETH from this function, it could call back into the `_transfer` function before the initial transaction's state is fully updated, potentially leading to repeated withdrawals or other unintended behavior.

**Recommendation:** This is a critical security vulnerability. The project team should ensure that all state changes in the `_transfer` function are completed *before* any external calls are made, following the Checks-Effects-Interactions pattern. The `nonReentrant` guard should be applied to all functions that perform external calls and modify state.


### `CP-05` — Owner can stop or start fee processing, impacting token transfers.  *(Severity: Medium · Status: Unresolved)*

The owner can use the `processFees` function to control whether fees are processed during token transfers. This acts as a switch that can enable or disable a core part of the token's economic mechanism. If fee processing is stopped, it could disrupt the intended fee collection and distribution, potentially affecting the token's value or functionality.

**Recommendation:** Token holders should understand that the owner has direct control over this fee processing switch. Transparency regarding the use of this function is important. Consider if this control should be subject to a community vote or a time-lock.


### `CP-07` — Owner can change token transfer fees and how they are distributed.  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to modify the fees applied to token transfers and how these fees are collected. Functions like `addFeeCollector`, `removeFeeCollector`, and `updateFeeCollectorShare` allow the owner to add new addresses to collect fees, remove existing ones, or change the percentage of fees each collector receives. This means the owner can unilaterally alter the token's fee structure, potentially increasing fees or redirecting them to different addresses.

**Recommendation:** Token holders should be aware that the owner can change the fee structure at any time. It is important for the project to clearly communicate any changes to fees or fee collectors. Consider proposing a governance mechanism for fee changes.


### `CD-01` — Potential for small rounding losses in fee calculations.  *(Severity: Low · Status: Unresolved)*

In functions like `_processFees` and `_transfer`, calculations involving fees might perform division before multiplication. This order of operations can lead to minor rounding errors, where a very small amount of tokens might be lost or gained due to integer arithmetic. While typically small, these losses can accumulate over many transactions.

**Recommendation:** While the impact is usually minimal, it's best practice to perform multiplication before division in Solidity to minimize rounding errors. This ensures more precise calculations for token amounts and fees.


### `CP-08` — Owner can change the amount of tokens swapped at once.  *(Severity: Low · Status: Unresolved)*

The owner can use the `setNumTokensToSwap` function to change the maximum number of tokens that can be swapped in a single transaction. This limit directly affects the token's trading mechanics and liquidity management. While this control can be used for operational efficiency, it also means the owner can unilaterally impose restrictions on trading volume.

**Recommendation:** Token holders should be aware that the owner can adjust this trading limit. Transparency about the rationale for any changes to this limit is beneficial.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,860 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked, lock term not visible  *(Severity: Informational · Status: Acknowledged)*

98.1% of the pool's LP is burned or time-locked. 98.1% is held by UNCX, but the lock's end date is not published in the data we can read — its duration is unverified. 0.8% is held, unlocked, by the token's owner/deployer (0xa79d…760f) — they can pull that liquidity at any moment. This is the rug-pull path. 1.1% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $84K (DexScreener, all pools). 24h trading volume $31K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: 0% on buy, 5% on sell. Market: $84K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xccb6...ea4d`](https://basescan.org/address/0xccb655bf8a03b57d80aa3835a39de5242605ea4d) |
| **Network** | Base |
| **Price** | $0.001659 |
| **24h Volume** | $30.8K |
| **Liquidity** | $83.6K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 1d |
| **Top-10 Holders** | 56.4% of supply |
| **Buy / Sell Tax** | 0.0% / 5.0% |
| **24h Transactions** | 266 buys / 40 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x973a9cd3008ac2e83172b811726e6219cfb33195)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mega-yacht-cult-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
