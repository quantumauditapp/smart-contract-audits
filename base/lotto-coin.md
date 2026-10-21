---
token: Lotto Coin
ticker: LOTTO
network: base
risk_score: 63
status: medium
date: 2026-09-13
---

# Lotto Coin (LOTTO) — Smart Contract Security Analysis | Base

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lotto-coin-base)

---

## Audit Summary

The DopplerERC20V1 contract implements an ERC20 token with vesting functionalities, utilizing Solady libraries for efficiency and security. It operates as an upgradeable proxy, correctly using the `Initializable` pattern. Key features include a temporary balance limit, vesting schedules with cliff and duration, and a controller role for specific administrative actions. While the core ERC20 and vesting logic appears sound, the audit identified several areas of concern related to access control immutability, misleading function naming, and high token concentration limits, leading to a Medium overall risk level.

> **Final Recommendation:** It is recommended to address the identified centralization risks by implementing mechanisms to update critical roles like the `controller` and to manage the `isExcludedFromBalanceLimit` mapping post-initialization, possibly through a multi-signature wallet or governance. Clarifying the behavior of the `lockPool` function through renaming or enhanced documentation is advised to prevent misunderstandings. Consider implementing a general emergency pause mechanism to provide a safety net in unforeseen circumstances. Review the high pre-mint allocation limits to ensure they align with the project's decentralization goals.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good architectural practices by leveraging battle-tested Solady libraries for ERC20, Ownable, and Initializable functionalities (7.1 Architecture). The code generally… |
| **Governance / Economics** | 2/10 | High | The economic model includes a temporary balance limit and vesting schedules, providing structured token distribution. The `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` constants allow… |
| **Upgrades** | 7/10 | Low | The contract correctly implements the upgradeable pattern using Solady's `Initializable` module, including `_disableInitializers()` in the constructor and an `external initializer` function. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 58.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `H-01` — Centralization Risk: Immutable Controller and Inflexible Exclusion List  *(Severity: High · Status: Unresolved)*

The `controller` address, which is authorized to call `disableBalanceLimit`, is set only during the `initialize` function and cannot be changed thereafter. If the controller's private key is lost or compromised, the ability to manage the balance limit is permanently affected. Similarly, the `isExcludedFromBalanceLimit` mapping is primarily populated during initialization and when `lockPool` is called. There is no function to add or remove addresses from this exclusion list post-initialization, leading to significant operational inflexibility. For example, if a new exchange or critical protocol integration requires exclusion, it cannot be done without an upgrade.

**Recommendation:** Implement a mechanism for the owner (preferably a multi-signature wallet) to update the `controller` address. Introduce functions, callable by the owner, to add or remove addresses from the `isExcludedFromBalanceLimit` mapping. This enhances operational flexibility and reduces single points of failure.


### `M-01` — Misleading Function Name `lockPool`  *(Severity: Medium · Status: Unresolved)*

The `lockPool` function's name is misleading. Despite its name, it does not 'lock' the pool's ability to transfer tokens or interact with the contract in any restrictive way beyond adding it to the `isExcludedFromBalanceLimit` mapping. The `isPoolLocked` state variable, set by this function, only gates subsequent calls to `lockPool` and `unlockPool` and has no direct impact on token transfer logic. This could lead to incorrect assumptions about the contract's behavior and potential operational errors.

**Recommendation:** Rename the `lockPool` function to accurately reflect its functionality, e.g., `addPoolToBalanceLimitExclusion` or `setPoolExclusionStatus`. Update documentation to clearly explain its actual effect.


### `M-02` — Lack of Emergency Stop/Pause Mechanism  *(Severity: Medium · Status: Unresolved)*

The contract lacks a general emergency stop or pause mechanism. In the event of a critical vulnerability, exploit, or unforeseen issue affecting the token or its ecosystem, there is no way for the owner or a designated role to temporarily halt transfers or vesting releases to prevent further damage. This is a common security feature in critical smart contracts.

**Recommendation:** Consider implementing a `Pausable` mechanism (e.g., from Solady or OpenZeppelin) that allows the owner to pause and unpause critical functions like `_transfer` and `release`. This provides a crucial safety net for incident response.


### `L-01` — High Pre-Mint Allocation Limits  *(Severity: Low · Status: Unresolved)*

The constants `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` are both set to `0.8 ether`. Assuming `WAD = 1e18`, this means up to 80% of the `initialSupply` can be allocated to a single beneficiary, and the total pre-minted amount can be up to 80% of the `initialSupply`. While technically consistent, allowing such a high concentration of vested tokens to a single address or in total could lead to significant centralization of token distribution, potentially impacting market dynamics or decentralization goals.

**Recommendation:** Review these allocation limits to ensure they align with the project's desired token distribution strategy and decentralization objectives. If a more distributed initial allocation is desired, these constants should be adjusted.


### `L-02` — Potential Gas Limit Issues for `computeAvailableVestedAmount`  *(Severity: Low · Status: Unresolved)*

The `computeAvailableVestedAmount(address beneficiary)` function iterates through all `_scheduleIdsOf[beneficiary]` to sum up available amounts. If a beneficiary has an extremely large number of individual vesting schedules, this loop could potentially consume a significant amount of gas, possibly approaching the block gas limit for a single transaction. While unlikely for typical usage, it represents an edge case for denial-of-service for specific beneficiaries.

**Recommendation:** Consider if there's a practical limit to the number of schedules a single beneficiary might have. If this number could grow very large, explore alternative designs, such as paginated retrieval of available amounts or a mechanism to claim all available amounts in batches.


### `I-01` — Vesting Schedule Creation Limited to Initialization  *(Severity: Informational · Status: Unresolved)*

Vesting schedules (`vestingSchedules` array) can only be created during the `initialize` function. There is no public or owner-controlled function to add new vesting schedules post-initialization. This design choice limits the flexibility of the vesting mechanism, requiring a contract upgrade if new vesting terms are needed for future allocations or programs.

**Recommendation:** Confirm if this limitation is an intentional design choice. If future flexibility is desired, consider adding an owner-controlled function to create new vesting schedules, ensuring proper validation and access control.


### `I-02` — Local Import Path for `Wad.sol`  *(Severity: Informational · Status: Unresolved)*

The contract imports `WAD` from `src/types/Wad.sol`. While functionally correct within the project structure, using a local import path for a fundamental constant like `WAD` (typically `1e18`) means its definition is project-specific rather than relying on a universally recognized library. It's important to ensure `Wad.sol` consistently defines `WAD` as `1e18` to avoid miscalculations in critical economic logic.

**Recommendation:** Ensure `src/types/Wad.sol` is correctly defined and its value is `1e18`. For clarity and consistency, consider explicitly defining `WAD = 1e18` within the contract or using a more standard library import if available, although the current approach is not inherently insecure if the definition is correct.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x908b...679c`](https://basescan.org/address/0x908b1d6b6c12bfdfcaaeb658b365ce39c21e679c) |
| **Network** | Base |
| **Price** | $0.000775 |
| **24h Volume** | $577.6K |
| **Liquidity** | $559.0K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 78.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1284 buys / 2073 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe36ad7fdd277c5bd37db459130f508d6e995cd07324b461989a1d6ce77405884)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lotto-coin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
