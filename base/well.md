---
token: WELL
ticker: WELL
network: base
risk_score: 39
status: medium
date: 2026-09-04
---

# WELL (WELL) — Smart Contract Security Analysis | Base

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/well-base)

---

## Audit Summary

The audit of the xWELL token contract, deployed as an upgradeable proxy, identified a critical vulnerability related to a potential double mint in the `_mint` function due to multiple inheritance. Additionally, a high-severity issue was found where the `kickGuardian()` function allows unauthorized unpausing of the contract. The contract utilizes standard OpenZeppelin upgradeable patterns and robust access control via a multisig owner, but the identified critical and high-severity issues require immediate attention to prevent severe economic consequences and compromise of the emergency pause mechanism. The audit was limited by the truncation of dependent contract source code.

> **Final Recommendation:** Immediately address the critical double mint vulnerability by thoroughly reviewing the `xERC20` contract's `_mint` implementation and refactoring `xWELL._mint` to ensure token supply is incremented only once per mint operation. Rectify the `kickGuardian()` function to prevent unauthorized unpausing, ideally by restricting its access to the owner or removing it if its functionality is redundant with `ownerUnpause()`. Consider implementing a time-lock for sensitive owner operations to enhance security and provide a window for community review.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The xWELL contract leverages OpenZeppelin's upgradeable patterns and ERC-20 standards, demonstrating a solid architectural foundation (7.1 Architecture). However, a critical code security… |
| **Governance / Economics** | 5/10 | Medium | The economic model includes a `MAX_SUPPLY` and owner-configurable rate limits and buffer caps for minting, which provides flexibility and a hard cap on total supply (7.4 Economic). However, the… |
| **Upgrades** | 1/10 | High | The contract is deployed using the TransparentUpgradeableProxy pattern, adhering to OpenZeppelin's best practices for upgradeability (7.7 Upgrades). The `_disableInitializers()` in the constructor… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → OZ_ProxyAdmin |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 50.0% |
| **Top-3 Unlocked** | ⚠️ 99.5% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — High Centralization of Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner` (a multisig) possesses extensive control over critical contract parameters and operations. This includes the ability to set buffer caps, rate limits, pause duration, add/remove bridges, and grant/revoke the pause guardian. While the use of a multisig mitigates the risk of a single point of failure, this high degree of centralized control means the protocol's security and economic stability heavily rely on the owner's integrity, operational security, and responsiveness.

**Recommendation:** Consider implementing a time-lock for sensitive owner operations (e.g., `setRateLimitPerSecond`, `setBufferCap`, `setPauseDuration`, `addBridge`, `removeBridge`) to introduce a delay between the owner's decision and its execution. This provides a window for review and potential intervention, enhancing transparency and security. Explore progressive decentralization for some parameters if feasible in the future.


### `M-02` — Double Mint Vulnerability in `_mint` Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `xWELL._mint` function explicitly calls `super._mint(user, amount)` and `xERC20._mint(user, amount)`. The `super._mint` call resolves to `ERC20VotesUpgradeable._mint`, which in turn calls `ERC20Upgradeable._mint` to increment `_balances` and `_totalSupply`. If `xERC20._mint` also calls `ERC20Upgradeable._mint` or directly modifies `_balances` and `_totalSupply` (a common pattern for ERC20 implementations), then the token supply will be incremented twice for every mint operation. This would lead to an uncontrolled and incorrect token supply, severely devaluing the token and breaking core economic invariants.

**Recommendation:** Review the `xERC20` contract's `_mint` implementation. If it calls `ERC20Upgradeable._mint` or directly modifies `_balances` and `_totalSupply`, then the `xWELL._mint` function must be refactored. A common pattern for multiple inheritance is to call `super._mint()` once (which resolves to the most derived parent's implementation, e.g., `ERC20VotesUpgradeable`) and then integrate any additional logic from `xERC20` without redundant calls to the core ERC20 state modification functions.


### `M-03` — `kickGuardian()` Function Allows Unauthorized Unpausing  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `kickGuardian()` function is `public` and lacks any access control. It can be called by *anyone* if `pauseUsed()` is true and the contract is `whenNotPaused`. This function calls `_resetPauseState()`, which sets `pauseGuardian` to `address(0)` and `pauseStartTime` to `0`. This effectively removes the designated `pauseGuardian` and unpauses the contract if it was paused by the guardian. This undermines the emergency pause mechanism, allowing any malicious actor or even a confused user to bypass the guardian's control and unpause the system prematurely, potentially during an ongoing incident.

**Recommendation:** Restrict access to `kickGuardian()` to `onlyOwner` or remove the function if its intended purpose is not to allow general users to override the pause guardian. If the intent is for the owner to 'kick' a misbehaving guardian, the `ownerUnpause()` function already covers this by setting `pauseGuardian` to `address(0)`.


### `L-01` — Potential for Re-initialization in Complex Inheritance  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While `xWELL` correctly uses `_disableInitializers()` and the `initializer` modifier for its `initialize` function, ensuring the main contract is initialized once, complex inheritance hierarchies with upgradeable contracts always carry a subtle risk of re-initialization. Specifically, if `ConfigurablePauseGuardian` or its base contracts had their own `initialize` functions that could be called independently of `xWELL.initialize`, it could lead to state corruption. In this case, `__Pausable_init()` is called correctly, but the general principle warrants attention.

**Recommendation:** Ensure that all inherited upgradeable contracts are initialized exactly once through the main `initialize` function of the most derived contract. Regularly review the initialization patterns, especially after upgrades or changes to the inheritance structure, to prevent accidental re-initialization of base contract state variables.


### `I-01` — Incomplete Source Code for Dependencies  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `xWELL` contract truncates the `MintLimits.sol` file and does not include the `xERC20.sol` contract. A comprehensive security audit requires access to the complete and verified source code of all directly inherited and imported contracts, especially `xERC20` given its critical role in the `_mint` override.

**Recommendation:** Provide the full source code for `xERC20.sol` and `MintLimits.sol` to allow for a comprehensive security review and to fully assess the critical `_mint` vulnerability.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa885...96ae`](https://basescan.org/address/0xa88594d404727625a9437c3f886c7643872296ae) |
| **Network** | Base |
| **Price** | $0.001812 |
| **24h Volume** | $339.3K |
| **Liquidity** | $1.13M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 2y |
| **Top-10 Holders** | 69.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 877 buys / 4492 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x89d0f320ac73dd7d9513ffc5bc58d1161452a657)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/well-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
