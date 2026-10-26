---
token: Free Bots
ticker: BOTS
network: base
risk_score: 43
status: medium
date: 2026-08-30
---

# Free Bots (BOTS) — Smart Contract Security Analysis | Base

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/free-bots-base)

---

## Audit Summary

The DopplerERC20V1 contract implements an ERC20 token with vesting schedules and a temporary balance limit feature. The contract utilizes audited Solady libraries, enhancing code quality. However, a significant portion of the core vesting calculation and balance limit enforcement logic was not provided for review, preventing a comprehensive security assessment of these critical features. The initialization process is complex, and the `controller` role has centralized power over the balance limit.

> **Final Recommendation:** It is critical to provide the complete source code, especially the `_available` function and any token transfer overrides, to enable a full security assessment of the vesting and balance limit mechanisms. For the `controller` role, consider implementing a multi-signature wallet or a time-locked mechanism to mitigate the risk of centralized control over the balance limit disablement. Ensure thorough testing of the complex `initialize` function parameters to prevent misconfiguration during deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages robust Solady libraries for ERC20, Ownable, and Initializable functionalities, contributing to a solid architectural foundation (7.1). Access control (7.3) is implemented using… |
| **Governance / Economics** | 5/10 | Medium | The contract defines economic parameters such as `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` which are enforced during initialization (7.4). The `owner` has control over… |
| **Upgrades** | 2/10 | High | The contract includes `Initializable` and `_disableInitializers()` in its constructor, indicating a design for upgradeability (7.7). However, the provided metadata states `is_proxy: false`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 70.0% |
| **Top-3 Unlocked** | ⚠️ 92.7% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control over Balance Limit Disablement  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `controller` address, set during initialization and immutable, possesses the sole authority to disable the `isBalanceLimitActive` feature via the `disableBalanceLimit()` function. A compromise of this single key could lead to the balance limit being removed prematurely, potentially impacting token distribution or market stability if the limit is a critical economic safeguard.

**Recommendation:** Consider implementing a multi-signature wallet for the `controller` role to distribute control, or introduce a time-locked mechanism for disabling the balance limit to provide a delay for community intervention. If a single EOA is intended, ensure robust key management practices are in place.


### `M-02` — Incomplete Vesting and Balance Limit Enforcement Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code is truncated, specifically missing the implementation of the `_available` function, which is crucial for calculating releasable vested amounts. Furthermore, the actual enforcement logic for the `maxBalanceLimit` within token transfers (e.g., in `_beforeTokenTransfer` or a custom `_transfer` override) is not present. This prevents a comprehensive security assessment of two core functionalities of the token.

**Recommendation:** Provide the complete and untruncated source code, including the full implementation of the `_available` function and any logic responsible for enforcing the `maxBalanceLimit` during token transfers.


### `L-01` — Complex Initialization Function  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function is highly complex, accepting numerous parameters including multiple arrays for vesting schedules and beneficiary allocations, along with conditional setup for the balance limit. While checks are in place (e.g., `ArrayLengthsMismatch`, `InvalidSchedule`), the high number of inputs and intricate logic increases the risk of human error during deployment, potentially leading to misconfiguration or unintended behavior.

**Recommendation:** Thoroughly review and test all deployment scripts and parameters. Consider implementing robust off-chain tooling to generate and validate initialization parameters. For future versions, evaluate if some complex setup steps could be broken down into smaller, more auditable post-initialization functions if feasible.


### `I-01` — Immutability of Controller Address  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `controller` address, which is responsible for disabling the balance limit, is set during the `initialize` function and cannot be changed thereafter. While this prevents malicious reassignments, it also means that if the controller's private key is lost or compromised, the role cannot be recovered or transferred without a full contract redeployment or upgrade (if deployed as a proxy).

**Recommendation:** Acknowledge the implications of an immutable controller. If long-term flexibility or recovery mechanisms are desired, consider adding an `onlyOwner` function to update the controller address in future iterations, potentially with a timelock.


### `I-02` — Use of Initializable in Non-Proxy Context  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract inherits `Initializable` and calls `_disableInitializers()` in its constructor, which is a standard pattern for upgradeable contracts deployed behind a proxy. However, the provided metadata indicates that `is_proxy: false`, suggesting it is deployed as a standalone contract. While this setup is safe (prevents re-initialization), it implies the contract was either designed for upgradeability but deployed directly, or the metadata is incorrect.

**Recommendation:** Clarify the intended deployment strategy. If upgradeability is desired, ensure the contract is deployed behind a proxy. If not, the `Initializable` pattern is benign but adds unnecessary complexity and might cause confusion regarding the contract's upgradeability status.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4dcd...2ba3`](https://basescan.org/address/0x4dcdf3451dfc114991283c2e5b72823d69882ba3) |
| **Network** | Base |
| **Price** | $0.00000476 |
| **24h Volume** | $67.8K |
| **Liquidity** | $165.9K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 7d |
| **Top-10 Holders** | 52.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1051 buys / 1599 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x9150f6e5faf636ae28e0c70634598d7ce9d7fd3931f7c0f5d7f75faf6016086c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/free-bots-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
