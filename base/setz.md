---
token: SETZ
ticker: SETZ
network: base
risk_score: 68
status: high
date: 2026-09-03
---

# SETZ (SETZ) — Smart Contract Security Analysis | Base

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/setz-base)

---

## Audit Summary

The DopplerERC20V1 contract implements an ERC20 token with vesting functionalities and a temporary balance limit mechanism. The contract is deployed as an upgradeable proxy, leveraging Solady libraries for efficiency and security. Key features include owner-controlled pool locking, controller-managed balance limit disabling, and a robust vesting schedule system. While the codebase demonstrates high quality and adherence to best practices, the audit identified a high-severity access control issue related to the balance limit, medium-severity concerns regarding parameter immutability and unrestricted release functions, and minor informational findings.

> **Final Recommendation:** To enhance the security and decentralization of the DopplerERC20V1 contract, it is recommended to implement a multi-signature wallet or a time-locked governance mechanism for the `controller` role, particularly for sensitive actions like disabling the balance limit. Additionally, consider making key economic parameters configurable by the owner or through governance, allowing for greater flexibility in adapting to future project needs. Review the access control for `releaseFor` functions to align with the intended user experience for claiming vested tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract exhibits strong technical foundations (7.2 Code Security), utilizing audited Solady libraries for ERC20, Ownable, Initializable, and ERC20Votes functionalities. The vesting mechanism… |
| **Governance / Economics** | 3/10 | High | The economic model (7.4 Economic) incorporates a balance limit and vesting schedules, with initial parameters set during deployment. The `owner` has control over pool locking and token URI updates… |
| **Upgrades** | 2/10 | High | The contract is designed for upgradeability (7.7 Upgrades) using the `Initializable` pattern from Solady, with `_disableInitializers()` in the constructor and the `initializer` modifier. This setup… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 54.3% |
| **Top-3 Unlocked** | ⚠️ 85.8% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Balance Limit  *(Severity: High · Status: Unresolved)*

The `controller` address has the unilateral ability to disable the token's balance limit at any time via `disableBalanceLimit()`. This grants a single entity significant power over a core economic parameter, which, if compromised or misused, could drastically alter token distribution dynamics and market stability. This impacts 7.3 Access Control and 7.4 Economic.

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance mechanism for the `controller` role, or introduce a timelock for the `disableBalanceLimit` function itself to provide a window for community review or intervention.


### `M-01` — Immutability of Key Economic and Vesting Parameters  *(Severity: Medium · Status: Unresolved)*

Several critical parameters, including `MAX_PRE_MINT_PER_ADDRESS_WAD`, `MAX_TOTAL_PRE_MINT_WAD`, `MIN_VESTING_DURATION`, `maxBalanceLimit`, and `balanceLimitEnd`, are set as immutable constants or during the `initialize` function and cannot be modified post-deployment. While this provides certainty, it removes flexibility to adapt to unforeseen market conditions or evolving project requirements without a full contract upgrade. This impacts 7.4 Economic and 7.8 Operations.

**Recommendation:** Evaluate whether these parameters truly need to be immutable. For parameters that might require future adjustments, consider making them configurable by the `owner` or through a governance mechanism, potentially with timelocks.


### `M-02` — Unrestricted `releaseFor` Function Access  *(Severity: Medium · Status: Unresolved)*

The `releaseFor(address beneficiary, uint256 scheduleId, uint256 amount)` and `releaseFor(address beneficiary, uint256 amount)` functions are `external` and lack access control. This allows any external address to call these functions and trigger the release of vested tokens for any beneficiary. While tokens are transferred *to* the beneficiary, this design choice could lead to unexpected gas costs for beneficiaries if malicious actors repeatedly call these functions, or it might not align with the project's intended user experience for claiming tokens. This impacts 7.3 Access Control and 7.2 Code Security.

**Recommendation:** Consider restricting the `releaseFor` functions to only allow the `beneficiary` themselves or a specifically authorized address (e.g., the `owner` or `controller`) to initiate a release. Alternatively, if the current design is intentional, document this behavior clearly to manage user expectations.


### `L-01` — Misleading `BalanceLimitDisabled` Event Parameter  *(Severity: Low · Status: Unresolved)*

The `BalanceLimitDisabled` event is emitted with a hardcoded `false` value for its `expired` parameter when `disableBalanceLimit()` is called. This parameter name is misleading, as the limit is being disabled by the controller, not due to expiration. This impacts 7.2 Code Security and 7.8 Operations.

**Recommendation:** Rename the `expired` parameter in the event to something more generic like `byExpiration` or `isExpired`, and pass `false` when disabled by the controller and `true` if the limit naturally expires (though there's no explicit expiration check in the current code for this event). Alternatively, add a new parameter to indicate the reason for disabling.


### `I-01` — `computeAvailableVestedAmount` Overload Clarity  *(Severity: Informational · Status: Unresolved)*

The contract provides two `computeAvailableVestedAmount` functions: one that takes a `scheduleId` and one that does not (which sums across all schedules). While functional, the overloaded name for the latter might be ambiguous for integrators. This impacts 7.2 Code Security.

**Recommendation:** To enhance clarity for integrators and users, consider renaming the function that sums across all schedules to `computeTotalAvailableVestedAmount` or similar.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x020e...1ba3`](https://basescan.org/address/0x020eaeee24bcad37cb9a01aa1f8c591c47341ba3) |
| **Network** | Base |
| **Price** | $0.00000298 |
| **24h Volume** | $152.4K |
| **Liquidity** | $120.5K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 49.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 983 buys / 1538 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x2d6474a460ac27ffc6cb262243173ac25036c44e3c81113ed786cec7a970814c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/setz-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
