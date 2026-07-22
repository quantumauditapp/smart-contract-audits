---
token: Pro Token
ticker: PRO
network: bsc
risk_score: 75
status: critical
date: 2026-07-22
---

# Pro Token (PRO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 75/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pro-token-bsc)

---

## Audit Summary

The Pro Token contract implements an ERC20 token with custom transfer logic, including a whitelist, sell tax, and a liquidity pool balancing mechanism. The contract exhibits a high degree of centralized control, with `owner` and `governance` roles possessing significant power over critical parameters and token functionality. While some basic checks are in place, the immediate effect of parameter changes and the lack of decentralized control or time-locks introduce considerable governance and economic risk. Several critical and high-severity issues related to access control and parameter manipulation were identified.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to implement a multi-signature wallet for the `owner` and `governance` roles, especially for functions that modify critical parameters or transfer administrative control. Additionally, consider introducing time-locks for sensitive parameter changes (e.g., `setSellRates`, `setTargetRatio`, `setTargetPool`, `setTransferState`) to provide a window for community review and reaction. Ensure all critical functions, especially those related to the `treasury` and minting, are fully implemented and their access controls are robustly defined and documented.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The contract's architecture (7.1) is straightforward, extending OpenZeppelin's ERC20 and Ownable. Code security (7.2) is generally good with Solidity 0.8+ preventing common integer issues, and custom… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) relies on a sell tax and a liquidity pool balancing mechanism, which can be significantly influenced by privileged roles. Governance (7.5) is highly centralized, with `owner`… |
| **Upgrades** | 4/10 | Medium | The contract is not designed as an upgradeable proxy (7.7). Therefore, there are no upgrade-specific risks. Any changes to the contract logic would require a new deployment and migration of assets… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Excessive Centralization of Control  *(Severity: Critical · Status: Unresolved)*

The `owner` and `governance` roles possess extensive power over the contract's functionality and economic parameters. The `owner` can set `targetPool`, `treasury`, `targetRatio`, `transferStatus`, `add/removeWhitelist`, and `transferGovernance`. The `governance` can set `feeReceiver`, `sellRatio`, and call `balancePool`. This high degree of centralization creates a single point of failure, where a compromised or malicious privileged account could manipulate the token's economics, halt trading, or transfer administrative control without warning. For example, the `owner` can instantly transfer `governance` to any address via `transferGovernance`.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for both the `owner` and `governance` roles. For highly sensitive functions, consider adding a time-lock mechanism to introduce a delay before changes take effect, allowing for community oversight and reaction.


### `H-01` — Critical Parameter Manipulation without Timelocks  *(Severity: High · Status: Unresolved)*

Key economic and operational parameters such as `targetPool`, `targetRatio`, `sellRatio`, `feeReceiver`, and `transferStatus` can be changed instantly by the `owner` or `governance` roles. This immediate effect allows for rapid and potentially malicious alterations to the token's behavior, such as drastically increasing the sell tax, disabling transfers from the pool, or changing the liquidity pool address, without any grace period for users or external systems to react. For instance, `setSellRates` can change the sell tax up to 30% instantly.

**Recommendation:** Introduce a time-lock mechanism for all functions that modify critical parameters. This would enforce a delay between the initiation of a parameter change and its actual activation, providing transparency and an opportunity for stakeholders to review and react to proposed changes.


### `M-01` — Incomplete Validation for `setFeeReceiver`  *(Severity: Medium · Status: Unresolved)*

The `_update` internal function correctly includes a `require(feeReceiver != address(0) && feeReceiver != targetPool, "invalid fee receiver");` check to prevent issues with fee distribution. However, the `setFeeReceiver` function, which is callable by `onlyGovernance`, only checks `_newReceiver != address(0)`. It does not prevent setting `_newReceiver` to `targetPool`. If `feeReceiver` is set to `targetPool`, any subsequent token transfers to the pool (sells) would revert due to the check in `_update`, effectively halting selling functionality.

**Recommendation:** Add a check in the `setFeeReceiver` function to ensure that `_newReceiver` is not equal to `targetPool`. This will prevent the `feeReceiver` from being set to an invalid address that would cause future transactions to revert. Example: `if (_newReceiver == address(0) \|\| _newReceiver == targetPool) revert InvalidAddress();`


### `L-01` — Missing Mint Function Implementation  *(Severity: Low · Status: Unresolved)*

The state variable `treasury` is documented with the comment `/// @dev Treasury address authorized to mint tokens`. However, no `mint` function or similar functionality that allows the `treasury` address to create new tokens is present in the provided contract snippet. This creates a discrepancy between the contract's documentation and its actual implementation, leading to confusion about the intended capabilities of the `treasury` role.

**Recommendation:** Either implement the `mint` function with appropriate access control for the `treasury` address, or remove the `treasury` variable and its associated documentation if token minting is not an intended feature of the contract. Ensure the contract's code accurately reflects its intended functionality.


### `I-01` — Non-Standard ERC20 Decimals  *(Severity: Informational · Status: Unresolved)*

The `decimals()` function is overridden to return `9`. While technically valid for an ERC20 token, the most common standard for fungible tokens in the EVM ecosystem is 18 decimals. Using a non-standard decimal count like 9 can sometimes lead to compatibility issues or require custom handling when integrating with existing DeFi protocols, exchanges, or wallets that might implicitly assume 18 decimals.

**Recommendation:** Ensure that all external systems, such as exchanges, wallets, and DeFi protocols, are explicitly aware of and correctly configured to handle the token's 9 decimals. Clearly document this choice in all public-facing materials. If possible and without significant disruption, consider migrating to 18 decimals for broader compatibility.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8d65...f0e2`](https://bscscan.com/address/0x8d65744527f55d0b2338350912d5c99a81ddf0e2) |
| **Network** | BNB Chain |
| **Price** | $60.1500 |
| **24h Volume** | $14.98M |
| **Liquidity** | $89.98M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 6mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 23622 buys / 21166 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x63844bd4bfad910b1643713302a1cc1ed20d50c3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pro-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
