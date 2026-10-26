---
token: Global Dollar
ticker: USDG
network: ethereum
risk_score: 8
status: low
date: 2026-09-02
---

# Global Dollar (USDG) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/global-dollar-eth)

---

## Audit Summary

The USDG contract implements an upgradeable ERC-20 token with a claimable rewards system. It leverages OpenZeppelin's UUPS proxy pattern and AccessControl for robust role management. A critical finding is the use of `uint64` for token balances, which introduces a hard limit on total supply and individual balances, posing a significant risk of overflow and fund loss if not meticulously managed. Additionally, deprecated storage variables and centralized control mechanisms warrant attention.

> **Final Recommendation:** Prioritize a thorough review of the `uint64` balance implementation, especially the `StorageLib.toUint64Balance` function, to ensure it handles potential overflows by reverting rather than truncating. Evaluate the maximum expected total supply and individual balances to confirm `uint64` is sufficient for the project's long-term scale. Address all deprecated storage variables by either removing them entirely if unused (ensuring no storage collisions) or clearly documenting their status and ensuring they cannot be accidentally re-used in future upgrades. Strengthen documentation around the centralized control mechanisms and the complex multiplier logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes a modular architecture with clear separation of storage and logic, inheriting from OpenZeppelin's `AccessControlDefaultAdminRulesUpgradeable` for robust role management (7.1… |
| **Governance / Economics** | 9/10 | Low | The protocol benefits from a strong governance setup, with the `DEFAULT_ADMIN_ROLE` controlled by a Timelock, enhancing operational security and decentralization of critical actions (7.5, 7.8).… |
| **Upgrades** | 5/10 | Medium | The contract employs the UUPS upgradeable proxy pattern, with upgrade authorization strictly limited to the `DEFAULT_ADMIN_ROLE`, ensuring controlled and secure upgrades (7.7). The use of `__gap`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 25.2% |
| **Top-3 Unlocked** | 56.1% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 8 Informational_

### `M-02` — Potential for `uint64` Balance Overflow/Truncation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses `uint64` for `balance` and `shares` within `TokenAccountData` and `PayoutGroupData`. This is highly unusual for an ERC-20 token, which typically uses `uint256`. A `uint64` variable can only hold values up to `2^64 - 1` (approximately 1.8 * 10^19). Given the token has 6 decimals, this implies a maximum total supply or individual balance of approximately 1.8 * 10^13 USDG. If the total supply or any account's balance exceeds this limit, an overflow could occur. The behavior of `StorageLib.toUint64Balance` and `StorageLib.toUint64Shares` is critical here; if they truncate values rather than reverting on o

**Recommendation:** Re-evaluate the decision to use `uint64` for balances. If `uint64` is strictly necessary for gas optimization or other reasons, ensure that `StorageLib.toUint64Balance` and `StorageLib.toUint64Shares` explicitly revert on overflow. Implement robust checks before any operation that could push a `uint64` balance beyond its maximum value. Consider migrating to `uint256` for balances if the potential scale of the token could exceed `uint64` limits.


### `L-01` — Complexity of Multiplier and Payout Logic  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ClaimableRewardsBase` contract includes functions such as `_getMultiplierAtTime` and `_updatePayoutGroupBals`, which rely on `MultiplierGrowthLib` and involve complex arithmetic for time-dependent calculations and payout adjustments. While the full implementation of `MultiplierGrowthLib.projectMultiplier` is not provided, complex financial logic is inherently prone to subtle errors, especially when dealing with multiple parameters, time, and rates.

**Recommendation:** Conduct extensive unit and integration testing for all multiplier and payout calculation logic, covering edge cases, boundary conditions, and various time scenarios. Consider formal verification or a mathematical proof of correctness for the core `MultiplierGrowthLib` functions to ensure their integrity and accuracy under all conditions.


### `I-01` — Extensive Inheritance Hierarchy  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `USDG` contract inherits from a large number of parent contracts: `PaxosTokenClaimableRewards`, `UUPSUpgradeable`, `ClaimableRewardsBase`, `BaseStorageV3`, `AccessControlDefaultAdminRulesUpgradeable`, `ClaimableRewardsStorageV3`, `ClaimableRewardsEvents`, and `TokenAdminEvents`. While modularity is beneficial, such a deep and broad inheritance hierarchy can increase code complexity, make it harder to trace logic and state changes, and potentially introduce unexpected interactions or subtle bugs between parent contracts.

**Recommendation:** Ensure comprehensive documentation and clear architectural diagrams are maintained to explain the contract's structure, inheritance flow, and state variable ownership. Conduct thorough reviews to ensure there are no unintended method overrides or storage collisions due to the complex inheritance. Consider refactoring to reduce the depth or breadth of inheritance if it becomes a significant maintenance burden.


### `I-02` — Unused/Deprecated Storage Variables  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `BaseStorageV3` contract contains multiple explicitly named `deprecated` storage variables (e.g., `assetProtectionRoleDeprecated`, `supplyControllerDeprecated`, `proposedOwnerDeprecated`, `betaDelegateWhitelisterDeprecated`, `nextSeqsDeprecated`, `EIP712_DOMAIN_HASH_DEPRECATED`, `DOMAIN_SEPARATOR_DEPRECATED`). While `__gap` variables are used for future compatibility, the presence of these named deprecated variables can lead to confusion, potential misuse if not properly documented and guarded, or storage collisions if not carefully managed during future upgrades. This increases the risk of errors during maintenanc

**Recommendation:** Clearly document the status and purpose of all deprecated variables. Ideally, remove truly unused deprecated variables from the storage layout in a controlled upgrade, ensuring no storage collisions. If they must remain for historical reasons, ensure they are explicitly marked as immutable and cannot be written to or read in a misleading way by new logic. Consider using a dedicated `DeprecatedStorage` contract or library to isolate such variables.


### `I-03` — Centralized Control Over Token Operations  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract implements pausing functionality (`_isPaused`) and address freezing (`_isAddrFrozen`, `_setFrozen`), controlled by privileged roles (e.g., `DEFAULT_ADMIN_ROLE`). While common for stablecoins to enable emergency responses to security incidents or regulatory requirements, this introduces significant centralization risk. Privileged roles have the ability to halt all transfers or freeze specific user funds, which could be exploited or misused.

**Recommendation:** Ensure that the roles controlling these centralized functions are secured by multi-signature wallets and/or Timelocks with appropriate delays. Clearly document the conditions under which these functions would be invoked and the process for their activation and deactivation. Consider implementing a community-driven governance mechanism for critical actions if feasible for the project's roadmap.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 73.2% of supply. What remains: 61.1% in wallets, 12.1% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Global Dollar (USDG), market cap $3.1B, rank #35. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $24.8M (DexScreener, all pools). 24h trading volume $4.6M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — a timelock with a 24h delay — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a timelock with a 24h delay. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $24.8M of DEX liquidity across 11 pools. Launch: 358 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe343...491d`](https://etherscan.io/address/0xe343167631d89b6ffc58b88d6b7fb0228795491d) |
| **Network** | Ethereum |
| **Price** | $1.0002 |
| **24h Volume** | $4.64M |
| **Liquidity** | $20.03M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 73.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 97 buys / 86 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc061caa073f3d95f80f8e5428d32d2d76f5e1622)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/global-dollar-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
