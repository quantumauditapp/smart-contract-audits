---
token: Fren Pet
ticker: FREN PET
network: base
risk_score: 66
status: high
date: 2026-08-11
---

# Fren Pet (FREN PET) — Smart Contract Security Analysis | Base

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fren-pet-base)

---

## Audit Summary

The Fren Pet Token contract is an ERC20 token with burnable capabilities, integrating with Uniswap V2 for liquidity management. It features a complex tokenomics model including transaction fees, anti-whale mechanisms, a blacklist, and a pre-migration phase. The contract leverages OpenZeppelin and Solmate libraries for standard functionalities and security. While the code demonstrates good practices in using established libraries and includes reentrancy protection for liquidity operations, it exhibits a high degree of centralization through extensive owner privileges. The owner has significant control over critical parameters such as fees, trading status, and user blacklisting, which introduces considerable trust assumptions and potential economic risks for token holders.

> **Final Recommendation:** To enhance the security and decentralization of the Fren Pet Token, it is strongly recommended to reduce the extensive owner privileges. Consider implementing a multi-signature wallet for critical administrative functions or introducing a time-lock for sensitive parameter changes, such as fee adjustments or blacklist modifications. Additionally, clearly communicate the current fee structure and the potential for changes to the community to manage expectations and foster transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract's architecture (7.1) is a standard ERC20 token with added DeFi features, utilizing well-audited OpenZeppelin and Solmate libraries for core functionalities. Code security (7.2) is… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4) is highly dependent on owner actions, as fees can be set up to 25% for both buy and sell transactions, potentially leading to excessive taxation. The anti-whale mechanisms… |
| **Upgrades** | 6/10 | Medium | The contract is not designed to be upgradeable, meaning its logic is immutable once deployed. This eliminates upgrade-related risks but requires any future changes to be implemented via a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Extensive Owner Privileges and Centralization Risk  *(Severity: High · Status: Unresolved)*

The `FrenPetToken` contract grants the `owner` (via `Ownable`) extensive control over critical parameters and functionalities. This includes the ability to: update buy and sell fees up to 25% each, set maximum transaction amounts and maximum wallet holdings (potentially to zero, halting transfers), enable/disable trading, blacklist any address, and control the pre-migration phase. This high degree of centralization introduces significant trust assumptions and a single point of failure. A compromised or malicious owner could severely impact token holders. (7.3 Access Control, 7.4 Economic, 7.5 Governance, 7.8 Operations)

**Recommendation:** Consider implementing a multi-signature wallet for critical owner functions or a time-locked contract for sensitive parameter changes to reduce the risk associated with a single point of control. Clearly communicate the extent of owner privileges to the community.


### `H-02` — Potential for Excessive Transaction Fees  *(Severity: High · Status: Unresolved)*

The owner has the capability to set `buyTotalFees` and `sellTotalFees` up to 25% (2500 basis points) each. While the current default fees are 5% and 5% respectively, the `updateBuyFees` and `updateSellFees` functions allow the owner to increase these significantly. Such high transaction fees could render the token illiquid, discourage trading, and effectively drain value from token holders with each transaction. (7.4 Economic)

**Recommendation:** Implement a maximum cap for fees that is lower than 25%, or introduce a community governance mechanism to approve fee changes. Clearly document the fee structure and potential for changes.


### `M-01` — Anti-whale Mechanism Limitations  *(Severity: Medium · Status: Unresolved)*

The `maxTransactionAmount` and `maxWallet` limits are designed to prevent large transactions and concentrated holdings. However, these mechanisms can be bypassed by sophisticated users through splitting transactions across multiple wallets or by using multiple addresses to accumulate tokens beyond the `maxWallet` limit. While common in token contracts, this limits the effectiveness of the anti-whale measures. (7.4 Economic)

**Recommendation:** Acknowledge that anti-whale mechanisms have inherent limitations. For more robust control, consider alternative strategies or clearly communicate these limitations to users.


### `M-02` — Pre-migration Phase Operational Risk  *(Severity: Medium · Status: Unresolved)*

The contract includes a `preMigrationPhase` and a `preMigrationTransferrable` mapping, allowing the owner to control token transfers during a specific phase. This adds significant complexity to the transfer logic and grants the owner granular control over who can transfer tokens during this period. Mismanagement or errors in setting these parameters could lead to unintended restrictions on token movement or operational issues during a migration event. (7.8 Operations, 7.1 Architecture)

**Recommendation:** Ensure thorough testing of the pre-migration phase logic. Clearly define and communicate the conditions and duration of this phase to users. Consider if such a complex mechanism is strictly necessary or if simpler, more transparent migration strategies could be employed.


### `L-01` — Redundant SafeMath Usage  *(Severity: Low · Status: Unresolved)*

The contract imports and uses `SafeMath` for `uint256` operations. However, the contract is compiled with Solidity 0.8.19, which includes built-in overflow and underflow checks for all arithmetic operations by default. The explicit use of `SafeMath` is therefore redundant and adds unnecessary code complexity without providing additional security benefits in this Solidity version. (7.2 Code Security)

**Recommendation:** Remove the `using SafeMath for uint256;` statement and all explicit `SafeMath` calls. This will simplify the code without compromising security.


### `L-02` — Hardcoded Uniswap Router Address  *(Severity: Low · Status: Unresolved)*

The Uniswap V2 Router address (`0x327Df1E6de05895d2ab08513aaDD9313Fe505d86`) is hardcoded in the constructor. While this is a common practice, it means that if the Uniswap router contract were to be upgraded, deprecated, or compromised, the `FrenPetToken` contract's `swapAndLiquify` functionality would cease to work correctly, requiring a new deployment of the token contract to update the address. (7.6 External)

**Recommendation:** For future contracts, consider making critical external contract addresses configurable by the owner (e.g., via an `onlyOwner` function) to allow for updates without redeploying the entire token.


### `I-01` — Complex Transfer Logic  *(Severity: Informational · Status: Unresolved)*

The `_transfer` function in `FrenPetToken` is highly complex due to the numerous conditional checks for fees, anti-whale limits, blacklist status, trading activity, and the pre-migration phase. This intricate logic, while designed to implement specific tokenomics, increases the cognitive load for auditors and developers, making it more challenging to reason about correctness and potentially increasing the risk of subtle bugs or unexpected interactions. (7.2 Code Security, 7.1 Architecture)

**Recommendation:** While the current implementation appears functionally correct, consider refactoring complex logic into smaller, more focused internal functions in future contracts to improve readability, testability, and maintainability. Ensure comprehensive unit and integration tests cover all possible execution paths within the `_transfer` function.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xff0c...e105`](https://basescan.org/address/0xff0c532fdb8cd566ae169c1cb157ff2bdc83e105) |
| **Network** | Base |
| **Price** | $1.1000 |
| **24h Volume** | $145.4K |
| **Liquidity** | $520.7K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 2y |
| **Top-10 Holders** | 63.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 347 buys / 140 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xde66c35e01ed8e619bf092352338ef94f2327337)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fren-pet-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
