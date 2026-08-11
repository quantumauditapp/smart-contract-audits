---
token: The White Wolf
ticker: WOLF
network: base
risk_score: 78
status: critical
date: 2026-08-11
---

# The White Wolf (WOLF) — Smart Contract Security Analysis | Base

> **Risk Score: 78/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-white-wolf-base)

---

## Audit Summary

The audit of the DopplerERC20V1 contract identified a critical issue due to incomplete code, preventing a full assessment of the core vesting logic. The contract implements an ERC20 token with vesting schedules and a configurable balance limit. Key strengths include the use of battle-tested Solady libraries and robust input validation in the initialization process. However, the balance limit mechanism has several explicit exclusions, and the `controller` role introduces a point of centralization. A full security assessment requires the complete source code for the vesting functions.

> **Final Recommendation:** It is critical to provide the complete source code for the vesting calculation and release functions (`_available`, `_releaseFor`, `_releaseAllFor`) to enable a full security assessment of the core token functionality. Review the design implications of the balance limit exclusions and ensure they align with the intended security model. Consider implementing a timelock for the `controller` role or making it a multisig to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages Solady libraries for ERC20, Ownable, and Initializable functionalities, which contributes to a solid architectural foundation (7.1 Architecture). Input validation in the… |
| **Governance / Economics** | 4/10 | Medium | The contract's economic model includes a balance limit feature intended to restrict token holdings, and vesting schedules to control token distribution over time (7.4 Economic). The `initialize`… |
| **Upgrades** | 1/10 | High | The contract is not identified as an upgradeable proxy, and therefore, upgrade safety considerations (7.7 Upgrades) are not applicable. The `Initializable` pattern is used, but… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 69.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 2 Medium · ⚪ 2 Informational_

### `C-01` — Incomplete Vesting Logic Source Code  *(Severity: Critical · Status: Unresolved)*

The provided source code for the `DopplerERC20V1` contract is truncated, specifically omitting the full implementation of the `_available`, `_releaseFor`, and `_releaseAllFor` functions. These functions are central to the contract's core vesting mechanism, responsible for calculating releasable amounts and executing token transfers. Without the complete code, a comprehensive security assessment of the vesting logic, including potential reentrancy vulnerabilities, incorrect calculations, or denial-of-service risks, cannot be performed.

**Recommendation:** Provide the complete and untruncated source code for the `DopplerERC20V1` contract, especially the `_available`, `_releaseFor`, and `_releaseAllFor` functions, to allow for a thorough security review of the vesting mechanism.


### `M-01` — Centralized Control by Controller Role  *(Severity: Medium · Status: Unresolved)*

The `controller` address has the exclusive privilege to call `disableBalanceLimit()`, which permanently deactivates the token's balance limit feature. If the `controller` address is controlled by a single External Owned Account (EOA), it represents a single point of failure. A compromise of this EOA could lead to the balance limit being disabled against the protocol's intent, potentially impacting the token's economic model (7.3 Access Control, 7.5 Governance). While the owner is a multisig, the controller's status is not specified.

**Recommendation:** Consider assigning the `controller` role to a multi-signature wallet or a contract with a timelock mechanism. This would introduce a delay or require multiple approvals for critical actions, enhancing security and decentralization.


### `M-02` — Balance Limit Bypass for Excluded Addresses  *(Severity: Medium · Status: Unresolved)*

The `initialize` function explicitly excludes the `owner`, `recipient`, and all `beneficiaries` from the `isBalanceLimitActive` check by setting `isExcludedFromBalanceLimit` to `true` for these addresses. Additionally, the `lockPool` function excludes the designated `pool` address. This design choice means that these privileged addresses can hold token balances exceeding `maxBalanceLimit` even when the balance limit is active. While potentially intended, this significantly narrows the scope of the balance limit and should be clearly documented and understood as a core design decision impacting the token's economic security model (7.4 Economic).

**Recommendation:** Clearly document the rationale behind excluding these specific addresses from the balance limit. Ensure that this behavior aligns with the intended economic model and security assumptions. If the intent was for the balance limit to apply more broadly, reconsider these exclusions.


### `I-01` — Potential for Front-running in `releaseFor` (Conditional)  *(Severity: Informational · Status: Unresolved)*

The `releaseFor(address beneficiary, uint256 scheduleId, uint256 amount)` function is `external`, allowing any address to call it to release tokens for a specified beneficiary. Depending on the exact implementation of the truncated `_available` and `_releaseFor` functions, this could potentially open a window for front-running attacks. If the calculation of available tokens or the release process has a time-sensitive component that can be exploited, a malicious actor could observe a pending transaction and submit their own transaction with a higher gas price to claim tokens before the intended beneficiary or to grief the transaction (7.2 Code Security).

**Recommendation:** Once the full source code for `_available` and `_releaseFor` is available, carefully review the logic for any time-sensitive dependencies or race conditions. Consider restricting `releaseFor` to only be callable by the `beneficiary` themselves, or by an authorized `controller` with appropriate safeguards, if front-running is deemed a significant risk.


### `I-02` — Ambiguity in Vesting Duration for `duration == 0`  *(Severity: Informational · Status: Unresolved)*

The `initialize` function's validation for vesting schedules allows `s.duration == 0` or `s.duration >= MIN_VESTING_DURATION`. While `MIN_VESTING_DURATION` is set to 1 day, a `duration` of 0 implies immediate vesting. This dual condition is likely intended to support both immediate and time-locked vesting schedules. However, the naming `MIN_VESTING_DURATION` might suggest all vesting should have a minimum duration, which is not strictly enforced if `duration` is 0. This could lead to minor confusion or misinterpretation of the vesting schedule's behavior (7.2 Code Security).

**Recommendation:** Clarify the intended behavior for vesting schedules with `duration == 0` in the contract's documentation. Consider renaming `MIN_VESTING_DURATION` to something like `MIN_NON_ZERO_VESTING_DURATION` or adding a comment to explicitly state that `duration == 0` signifies immediate vesting, distinct from the minimum duration for time-locked schedules.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x73ac...5ba3`](https://basescan.org/address/0x73ac2806c40ab4741ea7a35b7328aca957755ba3) |
| **Network** | Base |
| **Price** | $0.00000642 |
| **24h Volume** | $144.4K |
| **Liquidity** | $257.3K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 59.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 284 buys / 436 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x0b94ef042317de1c60e1787778f7c46b58e73417cf252e571c8d544de964ab92)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-white-wolf-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
