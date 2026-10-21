---
token: Stonx
ticker: STONX
network: base
risk_score: 49
status: medium
date: 2026-09-14
---

# Stonx (STONX) — Smart Contract Security Analysis | Base

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stonx-base)

---

## Audit Summary

This audit covers the DopplerERC20V1 contract, which serves as an implementation for a proxy. The contract introduces vesting functionalities, a balance limit mechanism, and a pool lock feature. A significant limitation of this audit is that the provided source code was truncated, preventing a full review of critical vesting release logic and balance limit enforcement. Based on the available code, several areas of concern regarding centralization and potential gas inefficiencies were identified, alongside informational observations about the contract's design choices.

> **Final Recommendation:** It is strongly recommended to conduct a full audit with the complete and untruncated source code, particularly focusing on the vesting release logic and balance limit enforcement, to ensure no critical vulnerabilities are present. To mitigate potential gas cost issues, consider implementing a mechanism to paginate or limit the number of vesting schedules a single beneficiary can have, or optimize the `computeAvailableVestedAmount` function. Review the `controller` role's single-address nature and assess if a multi-signature or time-locked mechanism would be more appropriate for critical administrative functions like disabling the balance limit, enhancing the protocol's decentralization and security posture.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The DopplerERC20V1 contract leverages well-audited Solady libraries, contributing to a robust foundation and good code quality. It employs custom error types for clarity and gas efficiency. However… |
| **Governance / Economics** | 5/10 | Medium | The contract implements a dual-role access control system with an `owner` and a `controller`. While the `owner` (responsible for critical actions like pool locking/unlocking and upgrades) is noted to… |
| **Upgrades** | 7/10 | Low | The DopplerERC20V1 contract is designed as an implementation for a proxy, utilizing Solady's `Initializable` pattern. This is a standard and secure approach for upgradeability, ensuring that the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 21.2% |
| **Top-3 Unlocked** | 58.5% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 3 Informational_

### `H-01` — Incomplete Source Code Provided for Audit  *(Severity: High · Status: Unresolved)*

The provided source code for the `DopplerERC20V1` contract is truncated. Critical functions related to the core vesting release logic (`_available`, `_releaseFor`, `_releaseAllFor`) and potentially the enforcement of the balance limit (`_beforeTokenTransfer` if overridden) are missing. This prevents a comprehensive security assessment of the contract's primary functionalities.

**Recommendation:** Provide the complete and untruncated source code for all relevant contracts to enable a thorough security audit. Without the full code, the reliability of this audit is significantly limited, and undetected vulnerabilities may exist in the missing sections.


### `M-01` — Centralization Risk with Controller Role  *(Severity: Medium · Status: Unresolved)*

The `controller` role has the authority to call `disableBalanceLimit()`, which permanently deactivates the balance limit feature. While the `owner` role is managed by a multi-signature wallet (as per prefill data), the `controller` is a single address. This introduces a single point of failure and a centralization risk, as a compromise of this address could lead to an unauthorized disabling of a key economic control mechanism.

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked mechanism for the `controller` role, especially for critical functions like `disableBalanceLimit()`. This would enhance the security and decentralization of the protocol by requiring multiple approvals or introducing a delay for sensitive operations.


### `M-02` — Potential Gas Limit Issues with Unbounded Array Iteration  *(Severity: Medium · Status: Unresolved)*

The `_scheduleIdsOf[beneficiary]` mapping stores an array of schedule IDs for each beneficiary. The `computeAvailableVestedAmount(address beneficiary)` function iterates over this array to sum up available vested amounts across all schedules. If a beneficiary accumulates a very large number of vesting schedules, this array could grow indefinitely, leading to increased gas costs for the `computeAvailableVestedAmount` function and potentially causing transaction failures or denial-of-service for that beneficiary due to block gas limits.

**Recommendation:** Implement a mechanism to limit the number of vesting schedules a single beneficiary can have, or consider paginating the `getScheduleIdsOf` function and requiring clients to sum amounts off-chain. Alternatively, optimize the `computeAvailableVestedAmount` function to avoid iterating over potentially large arrays on-chain, perhaps by storing a pre-calculated total available amount.


### `I-01` — Vested Beneficiaries Excluded from Balance Limit  *(Severity: Informational · Status: Unresolved)*

During initialization and when allocating vesting, beneficiaries are automatically added to the `isExcludedFromBalanceLimit` mapping. This design choice means that any address receiving vested tokens will not be subject to the `maxBalanceLimit` or `balanceLimitEnd` restrictions, allowing them to transfer any amount of tokens regardless of the active balance limit.

**Recommendation:** Ensure this behavior is an intentional design choice and is clearly documented. If the intention was for the balance limit to apply universally or under specific conditions for vested beneficiaries, the exclusion logic should be reviewed and adjusted.


### `I-02` — Clarity on WAD Constant Usage for Percentage Calculations  *(Severity: Informational · Status: Unresolved)*

Constants like `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` are defined as `0.8 ether`. In the `initialize` function, these are used in calculations such as `initialSupply * CONSTANT / WAD`. Since `WAD` is typically `1 ether`, these calculations effectively represent 80% of the `initialSupply`. While mathematically correct, the use of `0.8 ether` as a constant name might be misinterpreted as an absolute value of 0.8 tokens rather than a percentage factor.

**Recommendation:** Consider renaming the constants to reflect their percentage nature (e.g., `MAX_PRE_MINT_PERCENTAGE_WAD`) or adding comments to clarify that `0.8 ether` represents 80% when divided by `WAD` (1 ether). This improves code readability and reduces potential for misinterpretation.


### `I-03` — Usage of LibTransient for Storage Optimization  *(Severity: Informational · Status: Unresolved)*

The contract utilizes `LibTransient` with `HAS_SCHEDULE_TRANSIENT_SLOT` to manage a boolean flag indicating if a schedule ID has been added to `_scheduleIdsOf` for a beneficiary. This is an advanced Solady pattern designed to optimize storage by using transient storage slots. While efficient, it's a less common pattern that might require specific understanding for future maintenance or audits.

**Recommendation:** Ensure that the development team is fully aware of the implications and usage of `LibTransient` for state management. Document the rationale behind using this pattern and its expected behavior to facilitate future code reviews and maintenance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x89d8...2bfc`](https://basescan.org/address/0x89d8cb38067b55f820f29a9e12d0ce18682a2bfc) |
| **Network** | Base |
| **Price** | $0.005005 |
| **24h Volume** | $260.8K |
| **Liquidity** | $36.7K |
| **Volume / Liquidity** | 7.1× |
| **Token Age** | 8d |
| **Top-10 Holders** | 50.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 576 buys / 532 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x9cd6944d88fdafde3f3d40ebf08df62a4728e54d9a8a59102c69b4bf724db662)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stonx-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*
