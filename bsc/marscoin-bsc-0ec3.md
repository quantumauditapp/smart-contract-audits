---
token: Marscoin
ticker: MARS
network: bsc
risk_score: 10
status: low
date: 2026-08-17
---

# Marscoin (MARS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/marscoin-bsc-0ec3)

---

## Audit Summary

The audit of the Token contract revealed a well-structured ERC20 implementation leveraging standard OpenZeppelin patterns. However, the custom transfer mode logic introduces significant centralization and several critical operational and governance risks. Key issues include an irreversible state change for transfer modes, an initially restricted transfer state, and the potential for permanent transfer lock if ownership is renounced prematurely. These design choices could severely impact token utility and user funds if not managed carefully.

> **Final Recommendation:** It is strongly recommended to carefully review the intended lifecycle and operational requirements for the token's transfer modes. Consider modifying the `setMode` function to allow the owner to revert to restricted modes from `MODE_NORMAL` if such flexibility is desired for future emergencies or operational changes. Additionally, ensure a clear plan is in place for transitioning the token out of its initial `MODE_TRANSFER_RESTRICTED` state, and exercise extreme caution if considering renouncing ownership, as it could lead to permanent transfer restrictions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard and well-audited OpenZeppelin patterns for ERC20 functionality and ownership, including safe use of `unchecked` blocks for arithmetic operations (7.2 Code Security).… |
| **Governance / Economics** | 7/10 | Low | The `Ownable` pattern provides a clear, single point of administrative control for critical functions like `setMode` (7.5 Governance). The ability to restrict transfers offers flexibility for… |
| **Upgrades** | 10/10 | Low | The contract is not designed with an upgradeability pattern (e.g., proxy). Therefore, there are no specific upgrade-related risks (7.7 Upgrades). Any changes to the contract logic would require a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 2 High · 🟡 2 Medium_

### `H-01` — Irreversible Transfer Mode Change  *(Severity: High · Status: Unresolved)*

The `setMode` function contains a condition `if (_mode != MODE_NORMAL) { _mode = v; }`. This logic prevents the owner from changing the token's transfer mode once it has been set to `MODE_NORMAL` (0). This means that if the project ever needs to re-enable transfer restrictions (e.g., for security incidents, regulatory compliance, or specific event phases), it will be impossible to do so, permanently removing a critical control mechanism.

**Recommendation:** Modify the `setMode` function to remove the `if (_mode != MODE_NORMAL)` condition, allowing the owner full flexibility to switch between all defined modes at any time. Alternatively, if the irreversible nature is intentional, clearly document this design choice and its implications.


### `H-02` — Initial Transfer Restriction Requires Owner Action  *(Severity: High · Status: Unresolved)*

In the constructor, the `_mode` is initialized to `MODE_TRANSFER_RESTRICTED`. This means that immediately after deployment, no token transfers are possible until the contract owner explicitly calls `setMode(MODE_NORMAL)`. If the owner fails to perform this action, or if there's a delay, users might be unable to transfer their tokens, leading to confusion, frustration, and potential economic loss.

**Recommendation:** Consider initializing the `_mode` to `MODE_NORMAL` if the intention is for the token to be freely transferable from deployment. If the restricted initial state is intentional, ensure robust off-chain communication and operational procedures are in place to promptly transition the token to `MODE_NORMAL`.


### `M-01` — Centralized Transfer Control in MODE_TRANSFER_CONTROLLED  *(Severity: Medium · Status: Unresolved)*

When `_mode` is set to `MODE_TRANSFER_CONTROLLED`, the `_beforeTokenTransfer` hook enforces `require(from == owner() \|\| to == owner(), 'Token: Invalid transfer');`. This design choice means that only transfers involving the contract owner (either as sender or receiver) are permitted. While potentially intentional for specific use cases, this severely centralizes control over token movement and significantly limits the token's liquidity and utility for general users, posing a high economic risk for token holders.

**Recommendation:** Clearly communicate the implications of `MODE_TRANSFER_CONTROLLED` to all potential users and stakeholders. Ensure this mode aligns with the project's long-term vision and decentralization goals. If broader transferability is desired, this mode should be used sparingly or redesigned.


### `M-02` — Risk of Permanent Lock if Ownership Renounced in Restricted Mode  *(Severity: Medium · Status: Unresolved)*

The `Ownable` contract includes a `renounceOwnership()` function. If the contract owner renounces ownership while the token is in `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`, and especially if `MODE_NORMAL` has not been set (due to H-01), no entity will be able to call `setMode` to change the transfer restrictions. This could permanently lock the token in a restricted state, rendering it untransferable and valueless.

**Recommendation:** Implement a safeguard to prevent `renounceOwnership()` if the token is not in `MODE_NORMAL`. Alternatively, ensure that ownership is only renounced after the token has been definitively set to `MODE_NORMAL` and the irreversible nature of this action is fully understood and accepted.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1fd4...5b68`](https://bscscan.com/address/0x1fd448d0361c3212961a70930f3129a45f425b68) |
| **Network** | BNB Chain |
| **Price** | $0.00009292 |
| **24h Volume** | $51.8K |
| **Liquidity** | $47.4K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 43.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 275 buys / 192 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x58bf4f8cdaafb4b394ee8266e2c3fe420cf16b71)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/marscoin-bsc-0ec3)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
