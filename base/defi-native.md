---
token: defi-native
ticker: DEFI-NATIVE
network: base
risk_score: 76
status: high
date: 2026-08-31
---

# defi-native (DEFI-NATIVE) — Smart Contract Security Analysis | Base

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/defi-native-base)

---

## Audit Summary

The DopplerERC20V1 contract implements an ERC20 token with vesting capabilities and a balance limit mechanism. The audit identified a critical vulnerability where the intended balance limit mechanism is not enforced due to a missing override of the `_beforeTokenTransfer` hook. This renders the balance limit ineffective. Additionally, the contract exhibits centralized control by the owner and controller roles. The core vesting logic could not be fully assessed due to truncated code. Addressing the critical functional flaw is paramount to ensure the intended security properties of the token.

> **Final Recommendation:** Prioritize the immediate implementation of the `_beforeTokenTransfer` override to correctly enforce the balance limit mechanism, as its current state renders it ineffective. Enhance access control by implementing a multi-signature wallet for the owner and controller roles to mitigate risks associated with centralized control. Ensure that the complete source code for all vesting-related functions is available for a comprehensive security review to validate the integrity of the token distribution logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages well-audited Solady libraries for its ERC20 and Ownable functionalities, contributing to a solid foundation (7.1 Architecture). It utilizes custom errors for clear error… |
| **Governance / Economics** | 2/10 | High | The economic model incorporates vesting schedules with cliff and duration periods, along with pre-mint limits to manage initial token distribution effectively (7.4 Economic). The `initialize`… |
| **Upgrades** | 1/10 | High | The contract incorporates the `Initializable` pattern from Solady and correctly calls `_disableInitializers()` in its constructor, preventing re-initialization in a non-proxy deployment (7.7… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 52.4% |
| **Top-3 Unlocked** | ⚠️ 94.7% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Missing `_beforeTokenTransfer` Override for Balance Limit Enforcement  *(Severity: Critical · Status: Unresolved)*

The contract defines a balance limit mechanism (`isBalanceLimitActive`, `maxBalanceLimit`, `balanceLimitEnd`, `isExcludedFromBalanceLimit`) and related access control (`disableBalanceLimit` by controller). However, the provided code snippet does not include an override of the `_beforeTokenTransfer` hook from the inherited `ERC20` (Solady) contract. Without this override, the `maxBalanceLimit` and `balanceLimitEnd` checks are not enforced during token transfers, rendering the entire balance limit mechanism ineffective for its primary purpose.

**Recommendation:** Implement the `_beforeTokenTransfer` hook to include the necessary checks for `isBalanceLimitActive`, `balanceLimitEnd`, `maxBalanceLimit`, and `isExcludedFromBalanceLimit` for the `to` address before allowing any token transfer.


### `M-01` — Centralized Control by Owner/Controller  *(Severity: Medium · Status: Unresolved)*

The contract utilizes the `Ownable` pattern, granting the `owner` significant administrative privileges, including `lockPool`, `unlockPool`, and `updateTokenURI`. Additionally, a `controller` role is introduced with the ability to `disableBalanceLimit`. While common for initial deployment phases, this centralization of power introduces a single point of failure and potential for malicious or compromised control.

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` and `controller` roles to enhance security and decentralization. For critical functions, explore time-locks or community governance mechanisms if the project matures.


### `L-01` — Potential Gas Cost for `computeAvailableVestedAmount` with Many Schedules  *(Severity: Low · Status: Unresolved)*

The `computeAvailableVestedAmount(address beneficiary)` function iterates through all schedule IDs associated with a beneficiary via `_scheduleIdsOf[beneficiary]`. If a beneficiary accumulates a very large number of individual vesting schedules, this array could grow significantly, leading to increased gas costs for calling this view function. While view functions don't directly cost the caller gas on-chain, they can impact off-chain queries and potentially on-chain calls if another contract were to query it.

**Recommendation:** For beneficiaries expected to have a very high number of vesting schedules, consider alternative data structures or aggregation methods to reduce iteration costs. For typical use cases, the current implementation is likely acceptable.


### `I-01` — Truncated Code Prevents Full Vesting Logic Review  *(Severity: Informational · Status: Unresolved)*

The provided contract snippet is truncated, specifically omitting the full implementation of the `_available`, `_releaseFor`, and `_releaseAllFor` internal functions. These functions are central to the core vesting mechanism, calculating releasable amounts and handling token transfers. Without their complete code, a comprehensive security assessment of the vesting logic cannot be performed.

**Recommendation:** Provide the complete source code for all relevant functions to enable a thorough security review of the vesting mechanism.


### `I-02` — `pool` Address Excluded from Balance Limit  *(Severity: Informational · Status: Unresolved)*

The `lockPool` function, callable by the owner, sets a `pool` address and then explicitly excludes this address from the balance limit checks by setting `isExcludedFromBalanceLimit[pool_] = true`. This design choice allows the designated pool contract to hold an unlimited amount of tokens, bypassing the `maxBalanceLimit`.

**Recommendation:** Ensure that the `pool` contract is thoroughly audited and trusted, as its exclusion from the balance limit could be exploited if the pool contract itself is compromised or contains vulnerabilities. Document the rationale for this exclusion clearly.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xad46...2ba3`](https://basescan.org/address/0xad46308a6f6999bacc099f3029b77c352e772ba3) |
| **Network** | Base |
| **Price** | $0.00000147 |
| **24h Volume** | $22.3K |
| **Liquidity** | $79.7K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | 65.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1852 buys / 2975 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xb4a7c81b8a45d52872c86d3825ccbd4f4882773337ada59f85148a95e3ad37d8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/defi-native-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
