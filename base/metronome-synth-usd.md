---
token: Metronome Synth USD
ticker: MSUSD
network: base
risk_score: 59
status: high
date: 2026-07-24
---

# Metronome Synth USD (MSUSD) — Smart Contract Security Analysis | Base

> **Risk Score: 59/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/metronome-synth-usd-base)

---

## Audit Summary

The audit of the SyntheticToken contract (implementation for a TransparentUpgradeableProxy) on the Base network identified several areas of concern, primarily related to centralized control and reliance on external dependencies. While the contract demonstrates good coding practices and adheres to upgradeability standards, the extensive powers granted to the governor role and the immutability of a critical dependency introduce notable risks. The core ERC-20 logic was partially truncated, limiting a full assessment of internal functions.

> **Final Recommendation:** To enhance the security posture of the SyntheticToken contract, it is highly recommended to decentralize critical administrative powers currently held by the single `governor` role. Implementing a multi-signature wallet with a sufficient threshold or a time-locked governance mechanism for sensitive operations like setting supply caps or updating privileged addresses would significantly mitigate the risk of a single point of failure. Additionally, consider adding a governor-controlled setter for the `_poolRegistry` address to allow for more flexible management of this critical dependency without requiring a full contract upgrade.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates good adherence to secure coding practices, including comprehensive input validation with custom error messages (e.g., `NameIsNull`, `AmountExceedsAllowance`). It correctly… |
| **Governance / Economics** | 1/10 | High | The contract clearly defines a `governor` role and uses specific modifiers (`onlyGovernor`, `onlyIfCanBurn`, `onlyIfCanMint`, `onlyIfCanSeize`) to enforce access control for sensitive operations.… |
| **Upgrades** | 1/10 | High | The contract correctly utilizes the OpenZeppelin `Initializable` pattern, including `_disableInitializers()` in the constructor and the `initializer` modifier, which is standard practice for secure… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control Over Token Supply and Operations  *(Severity: High · Status: Unresolved)*

The `SyntheticToken` contract grants significant control to the `governor` role (obtained from `_poolRegistry`). The governor can update `maxTotalSupply`, `maxAmoSupply`, `maxBridgedInSupply`, `maxBridgedOutSupply`, `proxyOFT`, and `amo` addresses. These addresses are then used in `onlyIfCanBurn` and `onlyIfCanMint` modifiers, effectively allowing the governor to dictate which external entities can mint or burn tokens. This centralization introduces a single point of failure; compromise of the governor's private key could lead to arbitrary minting/burning or manipulation of supply caps. (Coverage: 7.3 Access Control, 7.4 Economic, 7.5 Governance)

**Recommendation:** Implement a multi-signature wallet or a time-locked governance mechanism for critical administrative functions to reduce the risk associated with a single point of control. Clearly document the powers of the governor and the associated risks.


### `M-01` — Immutability of `_poolRegistry` after Initialization  *(Severity: Medium · Status: Unresolved)*

The `_poolRegistry` address, which is crucial for determining the `governor` and potentially other core functionalities, is set only once during the `initialize` function. There is no setter function to update this address. If `_poolRegistry` is initialized incorrectly or if the referenced `IPoolRegistry` contract needs to be upgraded or replaced in the future, it would require a full contract upgrade of `SyntheticToken` itself, which is a more complex and risky operation than a simple address update. (Coverage: 7.1 Architecture, 7.3 Access Control, 7.8 Operations)

**Recommendation:** Consider adding a `setPoolRegistry` function, protected by `onlyGovernor`, to allow for updates to this critical dependency. This would provide more flexibility for future protocol evolution and error correction, while still maintaining appropriate access control.


### `M-02` — Reliance on External Contract Security and Liveness  *(Severity: Medium · Status: Unresolved)*

The `SyntheticToken` contract heavily relies on external contracts such as `IPoolRegistry`, `IProxyOFT`, `IPool`, and `IDebtToken` for its core access control logic (`onlyIfCanBurn`, `onlyIfCanMint`, `onlyIfCanSeize`) and to determine the `governor`. The security, liveness, and correct functioning of these external contracts are paramount. A vulnerability, compromise, or unexpected behavior in any of these dependencies could directly impact the `SyntheticToken`'s integrity, potentially leading to unauthorized minting/burning or frozen operations. (Coverage: 7.6 External, 7.1 Architecture)

**Recommendation:** Conduct thorough security audits of all integrated external contracts. Implement robust monitoring for the health and activity of these dependencies. Consider circuit breakers or emergency pause mechanisms in `SyntheticToken` that can be triggered if a critical external dependency is compromised or malfunctions.


### `L-01` — Default `maxTotalSupply` to `type(uint256).max`  *(Severity: Low · Status: Unresolved)*

During initialization, `maxTotalSupply` is set to `type(uint256).max`, effectively imposing no initial cap on the total supply of the synthetic token. While the `governor` can later set a specific `maxTotalSupply` via `setMaxTotalSupply`, this initial state means that until a specific cap is set, the token's supply is theoretically unbounded, subject only to the `onlyIfCanMint` restrictions. This might not align with the intended economic model if a hard cap is desired from the outset. (Coverage: 7.4 Economic, 7.5 Governance)

**Recommendation:** If a specific total supply cap is intended from deployment, it should be set during the `initialize` function or immediately after deployment by the governor. Otherwise, ensure clear documentation that the initial supply is uncapped and relies on the governor to set a limit.


### `I-01` — Incomplete Code for Core ERC-20 Logic  *(Severity: Informational · Status: Unresolved)*

The provided contract snippet for `SyntheticToken` truncates the implementations of critical internal functions such as `_approve`, `_burn`, `_mint`, and `_transfer`. These functions are fundamental to the token's ERC-20 behavior and supply management, including the enforcement of supply caps (`SurpassMaxBridgingSupply`, `SurpassMaxSynthSupply`) and balance updates. Without the full code, a comprehensive audit of these core mechanics, including potential reentrancy vectors or subtle arithmetic errors, cannot be fully performed. (Coverage: 7.2 Code Security)

**Recommendation:** Always provide the complete and final source code for all contracts and their dependencies for a thorough security audit. Assume standard and safe OpenZeppelin-like implementations for these internal functions, but verify this assumption with the full code.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5267...ae9d`](https://basescan.org/address/0x526728dbc96689597f85ae4cd716d4f7fccbae9d) |
| **Network** | Base |
| **Price** | $0.9842 |
| **24h Volume** | $863.9K |
| **Liquidity** | $13.28M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 99.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 706 buys / 562 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x7501bc8bb51616f79bfa524e464fb7b41f0b10fb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/metronome-synth-usd-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-24*
