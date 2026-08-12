---
token: New BNB Coin
ticker: NNB
network: bsc
risk_score: 23
status: medium
date: 2026-08-12
---

# New BNB Coin (NNB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 23/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/new-bnb-coin-bsc)

---

## Audit Summary

The audit of the Token contract revealed a well-structured ERC20 implementation with an added owner-controlled transfer mode. While the core ERC20 functionality is robust, significant risks were identified concerning the interaction of the transfer mode mechanism with ownership management. Specifically, the design of the `setMode` function and the availability of `renounceOwnership` introduce critical operational and economic risks, potentially leading to a permanently unusable token or loss of emergency control.

> **Final Recommendation:** It is strongly recommended to address the critical operational risks associated with the `setMode` function and `renounceOwnership`. The `setMode` logic should be revised to allow the owner to re-enable transfer restrictions (e.g., a pause mechanism) even after `MODE_NORMAL` has been activated. Additionally, consider implementing a timelock for critical owner actions or a multi-signature wallet for ownership to mitigate centralized control risks. Ensure a clear operational plan is in place for the initial state and ownership management.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements a standard ERC20 token, inheriting from OpenZeppelin's `ERC20` and `Ownable` contracts, which generally ensures good code security (7.2). The use of `unchecked` blocks for… |
| **Governance / Economics** | 8/10 | Low | The token's economic model (7.4) is heavily reliant on the owner's control over transferability. The `_mode` variable allows the owner to restrict or completely halt transfers, which introduces a… |
| **Upgrades** | 9/10 | Low | The contract is not designed with upgradeability patterns (e.g., proxies) (7.7). Therefore, there are no upgrade-specific risks. Any changes to the contract logic would require deploying a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — GoPlus SafeToken Locker |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 2 Informational_

### `C-01` — Permanent Token Lock via Renounce Ownership  *(Severity: Critical · Status: Unresolved)*

The `Token` contract initializes in `MODE_TRANSFER_RESTRICTED`. The `setMode` function, which allows changing the transfer mode, is `onlyOwner`. If the contract owner calls `renounceOwnership()` while the token is in `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`, no address will be able to call `setMode(MODE_NORMAL)` to enable transfers. This would permanently lock the token in a restricted state, rendering it unusable for its intended purpose.

**Recommendation:** Implement a mechanism to prevent `renounceOwnership()` if the token is not in `MODE_NORMAL`. Alternatively, ensure that `setMode` can be called by a designated role (e.g., a multi-sig) even after ownership is renounced, or remove the `renounceOwnership` function entirely if not intended for use.


### `H-01` — Irreversible Loss of Emergency Transfer Control  *(Severity: High · Status: Unresolved)*

The `setMode` function contains the condition `if (_mode != MODE_NORMAL) { _mode = v; }`. This means that once the token's transfer mode is set to `MODE_NORMAL`, it can never be changed back to `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`. This design permanently removes the owner's ability to pause or restrict transfers in an emergency situation (e.g., a critical vulnerability in an integrated DeFi protocol), which is a significant loss of control and a potential security risk.

**Recommendation:** Modify the `setMode` function to allow the owner to switch between all defined modes at any time. This would restore the ability to implement emergency pauses or restrictions if needed. For example, remove the `if (_mode != MODE_NORMAL)` condition.


### `M-01` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The `Token` contract grants the `owner` address complete control over the token's transferability via the `setMode` function. The owner can restrict or completely halt all token transfers. While this might be an intended feature for initial setup or specific use cases, it introduces a single point of failure and a high degree of centralization, which could be a concern for decentralization-focused projects or if the owner's key is compromised.

**Recommendation:** Consider decentralizing control over critical functions like `setMode` by implementing a multi-signature wallet for the owner address or integrating a governance mechanism (e.g., DAO) for such decisions. Clearly communicate this centralized control to users.


### `I-01` — Initial Restricted Transfer State  *(Severity: Informational · Status: Unresolved)*

The `Token` contract's constructor sets the initial transfer mode to `MODE_TRANSFER_RESTRICTED`. This means that immediately after deployment, token transfers will be reverted until the owner explicitly calls `setMode(MODE_NORMAL)`. This is a common pattern for controlled launches but requires an explicit owner action to enable full functionality.

**Recommendation:** Ensure that the operational team is aware of this initial state and has a clear plan to call `setMode(MODE_NORMAL)` at the appropriate time. Document this behavior clearly for users and stakeholders.


### `I-02` — Adherence to OpenZeppelin ERC20 Standards  *(Severity: Informational · Status: Unresolved)*

The `Token` contract largely follows the well-established OpenZeppelin ERC20 implementation, including `Context`, `Ownable`, and `ERC20` base contracts. This adherence to widely audited and recognized standards contributes positively to the contract's overall security posture and reduces the likelihood of common ERC20-related vulnerabilities.

**Recommendation:** Continue to leverage and stay updated with battle-tested libraries and standards for core functionalities.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcbbc...d0d5`](https://bscscan.com/address/0xcbbc4fa9f9fbfae7ec5c5bb0f3fbeeca4750d0d5) |
| **Network** | BNB Chain |
| **Price** | $0.0003923 |
| **24h Volume** | $433.6K |
| **Liquidity** | $69.9K |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 42.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2428 buys / 1755 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc3a396b079360176f28b2ea501a66cf076977276)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/new-bnb-coin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
