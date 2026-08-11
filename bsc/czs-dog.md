---
token: CZ'S DOG
ticker: BROCCOLI
network: bsc
risk_score: 39
status: medium
date: 2026-08-11
---

# CZ'S DOG (BROCCOLI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/czs-dog-bsc)

---

## Audit Summary

The audit of the Token contract identified a critical vulnerability where the token becomes permanently unusable if ownership is renounced while transfer restrictions are active. This is compounded by the initial `MODE_TRANSFER_RESTRICTED` state and the provided `ownership_renounced: true` status. Additional findings include a potential revert in `increaseAllowance`, an irreversible design choice for transfer modes, and minor best practice recommendations.

> **Final Recommendation:** Prioritize addressing the critical issue of token usability. If the token is intended for general circulation, ensure `setMode(MODE_NORMAL)` is called *before* ownership is renounced. For future deployments, consider a more robust mechanism for managing critical parameters like transfer modes if ownership renunciation is a goal, potentially involving a multi-sig or time-locked contract.

Additionally, review the `increaseAllowance` implementation to prevent unexpected reverts and consider adding events for critical state changes like `setMode` for enhanced transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements a standard ERC20 token with `Ownable` access control. It correctly uses `unchecked` blocks for most arithmetic operations after necessary checks, preventing common integer… |
| **Governance / Economics** | 4/10 | Medium | The token incorporates a `_mode` mechanism to control transferability, allowing for restricted, controlled, or normal modes (7.4 Economic). The `setMode` function is `onlyOwner`, providing… |
| **Upgrades** | 8/10 | Low | The contract is not designed with an upgradeability pattern (e.g., proxy) and is therefore immutable once deployed. This simplifies its architecture by removing upgrade-related complexities and risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 69.0% — GoPlus SafeToken Locker |
| **Top-1 Unlocked Holder** | 18.6% |
| **Top-3 Unlocked** | 30.8% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Token Permanently Unusable Due to Renounced Ownership and Transfer Restrictions  *(Severity: Critical · Status: Unresolved)*

The `Token` contract initializes with `_mode = MODE_TRANSFER_RESTRICTED`, preventing all transfers. The `setMode` function, which can change `_mode` to `MODE_NORMAL` (allowing free transfers), is protected by `onlyOwner`. According to the provided information, ownership has been renounced (`ownership_renounced: true`), meaning `owner()` is `address(0)`. Consequently, `setMode` can no longer be called. If `_mode` was not set to `MODE_NORMAL` *before* ownership renunciation, the token is permanently stuck in `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED` (where transfers are only to/from `address(0)`), rendering it completely unusable for its intended purpose.

**Recommendation:** For any token intended for general use, ensure that transfer restrictions are lifted (i.e., `setMode(MODE_NORMAL)` is called) *before* renouncing ownership. If ownership renunciation is a project goal, a mechanism to manage critical parameters like `_mode` without an owner should be considered, such as a time-locked governance or a pre-defined transition schedule.


### `H-01` — `increaseAllowance` Potential Revert on Overflow  *(Severity: High · Status: Unresolved)*

The `increaseAllowance` function calculates `allowance(owner, spender) + addedValue`. If the sum exceeds `type(uint256).max`, the transaction will revert. While this prevents an overflow, it can lead to unexpected reverts for users attempting to increase allowance to a very large value, especially if the current allowance is already substantial. This behavior deviates from common ERC20 implementations where `increaseAllowance` often allows for "infinite" approvals (by setting to `type(uint256).max`) or handles large additions without reverting. This could disrupt user experience for high-value operations.

**Recommendation:** To align with common ERC20 behavior and prevent unexpected reverts for large allowance increases, consider wrapping the addition `allowance(owner, spender) + addedValue` in an `unchecked` block. Alternatively, explicitly check for overflow and revert with a more specific error message if a maximum allowance is intended, or cap the `addedValue`.


### `M-01` — Immutability of `_mode` to `MODE_NORMAL`  *(Severity: Medium · Status: Unresolved)*

The `setMode` function includes the condition `if (_mode != MODE_NORMAL) { _mode = v; }`. This design means that once the token's `_mode` is set to `MODE_NORMAL`, it cannot be changed back to `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`. This makes the token's transferability permanently unrestricted once `MODE_NORMAL` is activated, which is an irreversible decision with long-term implications for project control and potential future incident response.

**Recommendation:** Confirm that this permanent immutability of `MODE_NORMAL` is an intentional design decision. If there's a possibility that future restrictions might be required (e.g., in response to security incidents or regulatory changes), the logic in `setMode` should be adjusted to allow for re-enabling restrictions by the owner (if an owner exists).


### `L-01` — Unlocked Solidity Pragma  *(Severity: Low · Status: Unresolved)*

The contract uses `pragma solidity ^0.8.0;`. This allows compilation with any compiler version from 0.8.0 up to, but not including, 0.9.0. Using a floating pragma can lead to inconsistent bytecode if different compiler versions are used, potentially introducing subtle bugs or unexpected behavior due to compiler updates.

**Recommendation:** Lock the Solidity pragma to the specific compiler version used for deployment (e.g., `pragma solidity 0.8.20;`) to ensure deterministic compilation and prevent potential issues with future compiler versions.


### `I-01` — Missing Event for `setMode`  *(Severity: Informational · Status: Unresolved)*

The `setMode` function modifies the critical `_mode` state variable, which dictates the token's transferability. However, no event is emitted when the mode is changed. Emitting an event would provide crucial on-chain transparency and allow off-chain monitoring tools and users to track changes in the token's operational status.

**Recommendation:** Add an event, such as `event ModeChanged(uint256 oldMode, uint256 newMode);`, and emit it within the `setMode` function after the `_mode` variable is updated.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6d5a...6714`](https://bscscan.com/address/0x6d5ad1592ed9d6d1df9b93c793ab759573ed6714) |
| **Network** | BNB Chain |
| **Price** | $0.01676 |
| **24h Volume** | $770.2K |
| **Liquidity** | $1.73M |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 79.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 850 buys / 1197 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xa5067360b13fc7a2685dc82dcd1bf2b4b8d7868b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/czs-dog-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
