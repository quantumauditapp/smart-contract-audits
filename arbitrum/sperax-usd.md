---
token: Sperax USD
ticker: USDS
network: arbitrum
risk_score: 51
status: medium
date: 2026-09-15
---

# Sperax USD (USDS) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sperax-usd-arb)

---

## Audit Summary

The audit covers the USDs token implementation contract, deployed as an upgradeable proxy on Arbitrum. The contract is built using OpenZeppelin's upgradeable standards, including ERC-20, Ownable, Pausable, and Permit functionalities. Key findings include centralized control over token operations, redundant SafeMath usage, and the absence of an explicit upgrade timelock.

> **Final Recommendation:** To enhance the security and transparency of the USDs token, it is recommended to implement a timelock for critical administrative actions, particularly contract upgrades, to allow for community review and reaction time. Additionally, review the necessity of `SafeMathUpgradeable` in Solidity 0.8.19 to optimize gas usage. Maintain robust security practices for the multisig signers and their operational procedures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract leverages Solidity 0.8.19, benefiting from native overflow/underflow protection, and integrates well-tested OpenZeppelin upgradeable libraries for core functionalities (7.2 Code… |
| **Governance / Economics** | 4/10 | Medium | Governance is managed by a 3/5 multisig for critical roles, including the owner, admin, and pauser, which enhances security over a single EOA (7.5 Governance). The economic model is based on a… |
| **Upgrades** | 1/10 | High | The contract utilizes a TransparentUpgradeableProxy pattern with an OpenZeppelin ProxyAdmin, controlled by a 3/5 multisig, providing a secure and flexible upgrade path (7.7 Upgrades). OpenZeppelin's… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 85.2% |
| **Top-3 Unlocked** | ⚠️ 97.1% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control over Token Supply and Operations  *(Severity: Medium · Status: Unresolved)*

The contract's `owner` (a 3/5 multisig) and `DEFAULT_ADMIN_ROLE` (also a 3/5 multisig) hold significant power. This includes the ability to mint new tokens via `_mint`, burn tokens via `_burn`, pause all token transfers via `pause()`, and upgrade the contract logic. While a multisig mitigates single-point-of-failure risks, this concentration of power means that a compromise or collusion among multisig signers could lead to arbitrary changes in token supply, freezing of user funds, or introduction of malicious logic through upgrades. (7.3 Access Control, 7.4 Economic, 7.5 Governance)

**Recommendation:** Implement a timelock for critical administrative actions (e.g., minting, burning, pausing, upgrades) to provide a delay for users to react and for potential issues to be identified. Consider further decentralizing roles if feasible, or clearly document the multisig's operational procedures and security measures.


### `L-01` — Redundant SafeMath Usage in Solidity 0.8.19  *(Severity: Low · Status: Unresolved)*

The contract utilizes the `SafeMathUpgradeable` library for arithmetic operations. Solidity version 0.8.19, as specified by the pragma, includes native protection against integer overflows and underflows by default. Consequently, the explicit use of `SafeMathUpgradeable` for basic operations (e.g., `add`, `sub`, `mul`, `div`, `mod` without `try` or `errorMessage` parameters) is redundant. While not a security vulnerability in this context, it adds unnecessary gas costs and increases code verbosity without providing additional safety benefits. (7.2 Code Security)

**Recommendation:** For Solidity 0.8.x and above, remove `SafeMathUpgradeable` and rely on native overflow/underflow checks. If specific `try` or `errorMessage` functionalities are desired, consider implementing them directly or using a more lightweight custom library.


### `I-01` — Lack of Explicit Upgrade Timelock  *(Severity: Informational · Status: Unresolved)*

The contract is deployed behind a `TransparentUpgradeableProxy`, with the `ProxyAdmin` controlled by a 3/5 multisig. This setup allows for future upgrades to the contract's logic. However, the current architecture does not include an explicit on-chain timelock mechanism that would delay the execution of an upgrade proposal. While the multisig provides a layer of security by requiring multiple approvals, the absence of a timelock means that an approved upgrade could be executed immediately. This could limit the community's time to review proposed changes or react to potentially malicious upgrades. (7.7 Upgrades, 7.5 Governance)

**Recommendation:** Consider implementing a timelock contract between the `ProxyAdmin` and the multisig wallet. This would introduce a mandatory delay period (e.g., 24-72 hours) between the approval of an upgrade and its execution, providing transparency and a window for community review and response.


### `I-02` — Unused `_disableInitializers` Function  *(Severity: Informational · Status: Unresolved)*

The `Initializable` base contract provides a `_disableInitializers()` function, which, when called, permanently prevents any further initialization or re-initialization of the contract by setting `_initialized` to `type(uint8).max`. While this function is useful for non-upgradeable contracts to prevent re-initialization attacks, it is not explicitly called in the provided contract snippet. For upgradeable contracts, `reinitializer` might be used in future versions, making `_disableInitializers` undesirable. However, if the contract is intended to eventually become non-upgradeable or if a final initialization state is desired, not calling this function leaves the possibility of future re-ini…

**Recommendation:** Document the intended lifecycle of the contract regarding initialization. If the contract is designed to remain upgradeable indefinitely, no action is strictly required. If there's a point where re-initialization should be permanently prevented, consider calling `_disableInitializers()` at that stage, ensuring it aligns with the overall upgrade strategy.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd74f...5748`](https://arbiscan.io/address/0xd74f5255d557944cf7dd0e45ff521520002d5748) |
| **Network** | Arbitrum |
| **Price** | $0.9985 |
| **24h Volume** | $35.1K |
| **Liquidity** | $110.7K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 4y |
| **Top-10 Holders** | 92.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 132 buys / 107 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x50450351517117cb58189edba6bbad6284d45902)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sperax-usd-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
