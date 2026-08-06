---
token: Pendle
ticker: PENDLE
network: arbitrum
risk_score: 26
status: medium
date: 2026-08-06
---

# Pendle (PENDLE) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 26/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pendle-arb)

---

## Audit Summary

The audit of the StandardArbERC20 contract, an implementation for an Arbitrum L2 ERC20 token deployed via a beacon proxy, reveals a well-structured and robust design. The contract correctly handles L1 token metadata parsing and integrates with the `Cloneable` pattern for proxy compatibility. Identified issues are primarily related to design choices and best practices, with no critical or high-severity vulnerabilities found. The overall risk level is assessed as Low.

> **Final Recommendation:** Ensure that the `L2GatewayToken` base contract strictly enforces a single-call initialization pattern for `_initialize` to prevent re-initialization attacks on proxy instances. Document the expected behavior of `decimals()`, `name()`, and `symbol()` reverting when L1 metadata is unavailable to inform integrators and prevent unexpected failures. Consider making `bridgeInit` `external` and explicitly adding an `initializer` modifier for clearer access control and to reinforce the one-time setup expectation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The `StandardArbERC20` contract implements an L2 ERC20 token, leveraging `L2GatewayToken` for core functionality and `Cloneable` for proxy compatibility. The `bridgeInit` function correctly decodes… |
| **Governance / Economics** | 4/10 | Medium | The contract primarily functions as a standard ERC20 token on Arbitrum, with no complex governance mechanisms or unique economic incentives defined within its scope (7.5 Governance, 7.4 Economic).… |
| **Upgrades** | 1/10 | High | The `StandardArbERC20` contract is designed as an implementation for a beacon proxy, inheriting from `Cloneable` which correctly distinguishes between master copy and clone instances (7.7 Upgrades).… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 17.0% |
| **Top-3 Unlocked** | 34.9% |

## Security Findings

_🟡 1 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `M-01` — Revert on Missing ERC20 Metadata  *(Severity: Medium · Status: Unresolved)*

The `decimals()`, `name()`, and `symbol()` functions explicitly revert if the corresponding `ignore` flag (e.g., `availableGetters.ignoreDecimals`) is set, indicating that the metadata was not successfully parsed from the L1 token. While this behavior is intended to mimic L1 contracts where such functions might not exist, it deviates from standard ERC20 implementations which typically return a value (e.g., 0 for decimals, empty string for name/symbol) rather than reverting. This could cause issues for dApps or integrations that expect these standard ERC20 getters to always return a value and do not handle reverts gracefully.

**Recommendation:** Clearly document this specific behavior for integrators. Consider if returning a default value (e.g., 0 for decimals, empty string for name/symbol) is a more compatible approach for a broader range of ERC20 integrations, even if it deviates from the L1 mimicry. If reverting is critical for the design, ensure comprehensive testing of integrations under these conditions.


### `L-01` — Implicit Trust in `L2GatewayToken` Initialization Logic  *(Severity: Low · Status: Unresolved)*

The `bridgeInit` function calls `L2GatewayToken._initialize` to perform the core initialization logic. The security of preventing multiple initializations (a critical aspect for proxy contracts) relies entirely on `L2GatewayToken._initialize` correctly implementing an `initializer` pattern (e.g., using an `initialized` flag or `initializer` modifier). Without the source code for `L2GatewayToken`, this crucial protection is an assumption, introducing a dependency risk.

**Recommendation:** Verify that the `L2GatewayToken._initialize` function rigorously enforces a single-call initialization to prevent re-initialization attacks. If possible, consider adding an explicit `initializer` modifier directly to `StandardArbERC20.bridgeInit` for defense in depth, even if `L2GatewayToken` provides its own protection.


### `L-02` — Inline Assembly Usage in `BytesLib`  *(Severity: Low · Status: Unresolved)*

The `BytesLib` library, used by `BytesParser` for decoding `_data`, extensively utilizes inline assembly (`assembly { ... }`) for byte manipulation. While assembly can be highly efficient for low-level operations, it is inherently more complex, error-prone, and harder to audit than high-level Solidity. Although the library includes `require` statements for bounds checking, subtle errors in assembly logic could lead to unexpected behavior or vulnerabilities.

**Recommendation:** Ensure that `BytesLib` has undergone thorough and independent security review, specifically focusing on its assembly code. Maintain comprehensive test coverage for all functions within `BytesLib` to validate correct behavior across various input scenarios.


### `I-01` — `bridgeInit` Visibility and Explicit Initializer Pattern  *(Severity: Informational · Status: Unresolved)*

The `bridgeInit` function is declared as `public virtual`. While `L2GatewayToken._initialize` is expected to handle the single-call initialization, making `bridgeInit` `public` rather than `external` means it can be called internally, which is not strictly necessary for an initializer. Additionally, an explicit `initializer` modifier (e.g., from OpenZeppelin's `Initializable` pattern) is not directly applied to `bridgeInit` in `StandardArbERC20` itself, relying solely on the base contract.

**Recommendation:** Consider changing `bridgeInit` to `external` if it's not intended for internal calls. For clarity and robustness, explicitly apply an `initializer` modifier to `bridgeInit` within `StandardArbERC20` if `L2GatewayToken` does not already provide a sufficiently robust and explicit mechanism, or if `StandardArbERC20` needs its own initialization state.


### `I-02` — `Cloneable` `isMasterCopy` Storage Behavior in Proxy Context  *(Severity: Informational · Status: Unresolved)*

The `Cloneable` base contract initializes `isMasterCopy` to `true` in its constructor. In a proxy deployment, the constructor of the implementation contract (`StandardArbERC20`) is only called once when the implementation itself is deployed, not when proxy instances are initialized. Consequently, `isMasterCopy` will always be `true` in the implementation's storage slot. For proxy instances, this storage slot will be initialized to its default value (false) unless explicitly set during initialization. This is the intended behavior for the `Cloneable` pattern, where the implementation serves as the 'master copy' and clones are distinct.

**Recommendation:** No direct action is required as this is the designed behavior of the `Cloneable` pattern. However, it's important for developers and auditors to understand this distinction to avoid misinterpreting the state of `isMasterCopy` when analyzing proxy instances versus the master implementation.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0c88...c9e8`](https://arbiscan.io/address/0x0c880f6761f1af8d9aa9c466984b80dab9a8c9e8) |
| **Network** | Arbitrum |
| **Price** | $1.3700 |
| **24h Volume** | $51.3K |
| **Liquidity** | $1.54M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 3y |
| **Top-10 Holders** | 45.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 139 buys / 365 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xbfca4230115de8341f3a3d5e8845ffb3337b2be3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pendle-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-06*
