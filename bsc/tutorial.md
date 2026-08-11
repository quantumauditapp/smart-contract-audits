---
token: Tutorial
ticker: TUT
network: bsc
risk_score: 32
status: medium
date: 2026-08-11
---

# Tutorial (TUT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 32/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tutorial-bsc)

---

## Audit Summary

The audit of the Token contract, an ERC20-compliant token with custom transfer restrictions, identified several design-level risks related to its `_mode` mechanism and owner privileges. While the core ERC20 implementation is robust, the irreversible nature of mode changes and the critical dependency on owner actions for token utility present significant operational and economic considerations. The contract is not upgradeable and has a fixed supply.

> **Final Recommendation:** Prioritize a thorough review of the intended lifecycle and operational procedures for the token's transfer modes, especially the irreversible transition to `MODE_NORMAL`. Implement robust key management for the owner address, potentially utilizing a multi-signature wallet, given the critical role the owner plays in enabling token utility and managing transfer restrictions. Ensure all stakeholders are fully aware of the implications of each transfer mode and the permanent nature of certain state changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes standard OpenZeppelin patterns for ERC20 and Ownable functionalities, demonstrating good code quality (7.2 Code Security). `unchecked` blocks are used appropriately, safeguarded… |
| **Governance / Economics** | 4/10 | Medium | The token's economic utility is heavily dependent on the owner's actions due to its initial `MODE_TRANSFER_RESTRICTED` state (7.4 Economic, 7.8 Operations). The `setMode` function allows the owner to… |
| **Upgrades** | 10/10 | Low | The contract is implemented as a standard, non-upgradeable contract (7.7 Upgrades). There are no proxy patterns or upgrade mechanisms present, meaning its logic cannot be altered after deployment.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 0.1% |
| **LP Locked** | 34.4% — Dead Address, GoPlus SafeToken Locker |
| **Top-1 Unlocked Holder** | ⚠️ 65.5% |
| **Top-3 Unlocked** | 65.6% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Irreversible Transition to MODE_NORMAL  *(Severity: High · Status: Unresolved)*

The `setMode` function includes a condition `if (_mode != MODE_NORMAL)` which means that once the token's transfer mode is set to `MODE_NORMAL`, it can never be reverted to `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`. This makes the transition to fully unrestricted transfers irreversible, limiting future flexibility for the project to re-introduce transfer controls if needed.

**Recommendation:** Confirm if this irreversible transition is the intended design. If flexibility to re-impose restrictions is desired, remove the `if (_mode != MODE_NORMAL)` condition. If it is intended, ensure this critical design decision is clearly documented and communicated to all users and stakeholders.


### `M-01` — Critical Owner Role for Token Utility  *(Severity: Medium · Status: Unresolved)*

The `Token` contract initializes with `_mode = MODE_TRANSFER_RESTRICTED`, meaning no transfers are possible until the owner explicitly calls `setMode` to change it. This places a critical dependency on the owner to perform an operational step to enable the token's basic utility, creating a single point of failure if the owner key is compromised or lost.

**Recommendation:** Ensure robust key management practices for the owner address, such as using a multi-signature wallet. Clearly document the operational steps required to activate token transfers and the associated risks if these steps are not performed or the owner key is compromised.


### `M-02` — Risk of Permanent Transfer Restriction upon Ownership Renouncement  *(Severity: Medium · Status: Unresolved)*

The `Ownable` contract allows the owner to `renounceOwnership()`. If ownership is renounced while `_mode` is `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`, and `_mode` has not been set to `MODE_NORMAL`, the token's transferability could become permanently locked or restricted as there would be no owner to call `setMode`.

**Recommendation:** The owner should ensure the `_mode` is set to the desired final state (e.g., `MODE_NORMAL`) *before* considering renouncing ownership. If renouncing ownership is planned, this operational sequence is critical to prevent unintended permanent restrictions.


### `L-01` — Centralized Control in MODE_TRANSFER_CONTROLLED  *(Severity: Low · Status: Unresolved)*

When `_mode` is set to `MODE_TRANSFER_CONTROLLED`, only transfers where the `from` or `to` address is the contract owner are permitted. This effectively centralizes all token movement through the owner, which might not align with user expectations for a decentralized token and could be perceived as a high degree of control.

**Recommendation:** Clearly communicate the implications of `MODE_TRANSFER_CONTROLLED` to token holders, emphasizing the owner's centralized role in facilitating transfers during this phase. Ensure transparency regarding the project's intent for this mode.


### `I-01` — Fixed Supply Token  *(Severity: Informational · Status: Unresolved)*

The `_mint` and `_burn` functions are internal and only `_mint` is called once in the constructor. There are no public functions to mint or burn tokens after deployment, meaning the total supply is fixed at the amount specified during construction.

**Recommendation:** Document that the token has a fixed supply and no further minting or burning is possible after deployment. This clarifies the tokenomics for potential holders and investors.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcaae...99f3`](https://bscscan.com/address/0xcaae2a2f939f51d97cdfa9a86e79e3f085b799f3) |
| **Network** | BNB Chain |
| **Price** | $0.104 |
| **24h Volume** | $3.96M |
| **Liquidity** | $5.02M |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 91.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5133 buys / 5920 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6dafbf0ab4fd72e2a5c0ad5a1ed277d3bf8a8d1f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tutorial-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
