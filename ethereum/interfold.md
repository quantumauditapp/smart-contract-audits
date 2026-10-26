---
token: Interfold
ticker: FOLD
network: ethereum
risk_score: 48
status: medium
date: 2026-08-30
---

# Interfold (FOLD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/interfold-eth)

---

## Audit Summary

The InterfoldToken contract implements an ERC20 token with advanced features including vesting locks, role-based access control, and a multi-phase lifecycle. While it leverages battle-tested OpenZeppelin libraries and includes robust checks in its constructor and public functions, a significant portion of the critical business logic resides in internal functions not provided for review. This limitation prevents a comprehensive security assessment of the core token mechanics and vesting logic, leading to a higher overall risk rating.

> **Final Recommendation:** It is imperative to conduct a comprehensive audit of all internal functions related to token minting, locking, vesting, and transfer restrictions to verify their correctness, security, and adherence to the intended economic model. Ensure all privileged roles, especially the `DEFAULT_ADMIN_ROLE`, are controlled by robust multi-signature wallets with a high threshold to mitigate centralization risks. Consider implementing an emergency pause mechanism to provide a rapid response capability in case of unforeseen vulnerabilities or exploits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes OpenZeppelin's ERC20, ERC20Permit, ERC20Votes, Ownable2Step, and AccessControl, providing a solid foundation for token functionality and access management (7.2 Code Security).… |
| **Governance / Economics** | 4/10 | Medium | The contract implements a robust role-based access control system using OpenZeppelin's AccessControl, defining specific roles like MINTER_ROLE, WHITELIST_ROLE, and LOCK_MANAGER_ROLE, which enhances… |
| **Upgrades** | 4/10 | Medium | The contract is not designed as an upgradeable proxy, meaning its core logic cannot be changed post-deployment (7.7 Upgrades). This provides immutability and reduces the attack surface associated… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 4 Medium · ⚪ 2 Informational_

### `M-01` — Lack of Emergency Pause Mechanism  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract does not include a general emergency pause mechanism that could halt critical operations or all token transfers in response to a discovered vulnerability, a major exploit, or unforeseen market conditions. While `transferWhitelist` allows for restricting transfers to specific accounts, it is not a comprehensive solution for a system-wide emergency. Without a pause, the project team's ability to react quickly and mitigate damage during a crisis is limited.

**Recommendation:** Consider implementing an emergency pause mechanism (e.g., using OpenZeppelin's `Pausable` module) that can be triggered by a trusted role (e.g., the `DEFAULT_ADMIN_ROLE` or a dedicated 'Pauser' role). This would allow for a rapid response to critical situations, preventing further damage while a permanent solution is developed and deployed.


### `M-02` — Dependency on External Bonding Registry  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `InterfoldToken` contract has an immutable dependency on an external `IBondingRegistry` contract, set during construction. While the constructor performs a basic check for a non-zero address and non-empty code, it does not guarantee the security, immutability, or continued functionality of the `BONDING_REGISTRY` itself. If the `IBondingRegistry` contract were to be compromised, upgraded maliciously (if it's a proxy), or experience a critical bug, it could indirectly impact the `InterfoldToken`'s functionality, especially if the token's internal logic relies on the registry's state or functions in critical paths (e.

**Recommendation:** Thoroughly audit the `IBondingRegistry` contract for vulnerabilities. Ensure that the `BONDING_REGISTRY` is also immutable or, if upgradeable, that its upgrade mechanism is robust and controlled by a secure governance process. Clearly document the expected behavior and security assumptions related to the `BONDING_REGISTRY` and its interaction with the `InterfoldToken`.


### `M-03` — Critical Business Logic Not Provided for Review  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). A significant portion of the contract's core business logic, including functions responsible for token minting (`_mintTokens`), lock policy validation (`_validateCurve`, `_validatePolicyMaturity`), claim linking (`_linkClaim`), lock relinking (`_relinkActiveLock`, `_relinkQueuedLock`), spendable balance calculation (`_calculateSpendable`), and the critical `_beforeTokenTransfer` hook, were not included in the provided source code. These internal functions are fundamental to the token's economic model, vesting schedules, and transfer restrictions. Without reviewing these implementations, it is impossible to fully assess

**Recommendation:** Provide the complete source code for all internal functions and dependencies that constitute the core business logic of the InterfoldToken contract. A full audit of these components is essential to ensure their security, prevent potential exploits, and verify the integrity of the token's economic model.


### `M-04` — High Centralization Risk via Privileged Roles  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract relies heavily on privileged roles (`DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, `WHITELIST_ROLE`, `LOCK_MANAGER_ROLE`) for critical operations such as minting new tokens, managing transfer whitelists, and defining/linking lock policies. The `DEFAULT_ADMIN_ROLE` has the power to grant and revoke all other roles. If the private keys controlling these roles, especially the `DEFAULT_ADMIN_ROLE`, are compromised, an attacker could mint arbitrary tokens (up to MAX_SUPPLY), freeze transfers, or manipulate vesting schedules, leading to severe economic damage and loss of user funds. While the owner is a multisig, the `Acc

**Recommendation:** Ensure that all privileged roles, particularly the `DEFAULT_ADMIN_ROLE`, are controlled by robust multi-signature wallets with a high threshold (e.g., 3-of-5 or higher) to distribute control and reduce the risk of a single point of failure. Implement strict operational procedures for managing these keys and executing privileged transactions. Regularly review and audit the addresses holding these roles.


### `I-01` — `NO_MORE_LOCKS` Constant Interpretation  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `NO_MORE_LOCKS` constant is initialized in the constructor with a check `noMoreLocks_ <= earliestTge`, requiring it to be strictly after `earliestTge`. The name 'NO_MORE_LOCKS' suggests a specific point in time after which no new locks can be created. However, the provided snippet does not show where or how this constant is enforced within the contract's logic (e.g., in `createLockPolicy` or `linkClaim`). Without this enforcement, the constant's purpose is unclear and it may not effectively prevent new locks.

**Recommendation:** Ensure that the `NO_MORE_LOCKS` constant is actively enforced in all relevant functions (e.g., `createLockPolicy`, `linkClaim`, `_mintAllocation`) to prevent the creation of new locks after the specified timestamp. Add clear comments to the code explaining the intended behavior and enforcement mechanism of this constant.


### `I-02` — Renounce Ownership/Roles Disabled by Design  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract includes custom errors `RenounceOwnershipDisabled()` and `RenounceRoleDisabledForOwner()`, indicating an intentional design choice to prevent the owner from renouncing their ownership or the `DEFAULT_ADMIN_ROLE`. This is a security-conscious decision to prevent accidental loss of administrative control, which can be catastrophic for a protocol.

**Recommendation:** This is an intentional design choice and generally considered a good security practice. Ensure that this design decision is clearly documented within the project's specifications and understood by all stakeholders. The project team should have robust procedures for transferring ownership and managing role assignments.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe172...f904`](https://etherscan.io/address/0xe172e9b6cfbeeb5593bdce3f077356fdb33af904) |
| **Network** | Ethereum |
| **Price** | $0.05735 |
| **24h Volume** | $1.16M |
| **Liquidity** | $1.68M |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 73.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 453 buys / 469 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x909e4a022a7505d44b19b36fe76ee18567379ee4c9697438acde2e159c006c32)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/interfold-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
