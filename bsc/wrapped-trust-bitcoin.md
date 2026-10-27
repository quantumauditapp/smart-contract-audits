---
token: Wrapped Trust Bitcoin
ticker: WTBC
network: bsc
risk_score: 61
status: medium
date: 2026-09-17
---

# Wrapped Trust Bitcoin (WTBC) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-trust-bitcoin-bsc)

---

## Audit Summary

The WTBC contract implements an ERC20 token with custom transaction fees, access control roles, and a fixed maximum supply. The contract leverages OpenZeppelin's ERC20 and AccessControl for robust foundational security. Key features include conditional fees for burning and validator rewards, and administrative functions for managing fee exclusions and liquidity pairs. The primary risks identified relate to the high centralization of administrative roles, which control critical parameters and minting capabilities, and the immutability of core economic parameters like transaction fees and the main liquidity pair.

> **Final Recommendation:** It is strongly recommended to implement robust multi-signature governance for critical administrative roles, especially the `DEFAULT_ADMIN_ROLE` and `MINTER_ROLE`, to mitigate centralization risks. Consider adding functionality to adjust transaction fees within predefined safe bounds to allow for future economic adaptability. For the validator wallet, explore options for multi-signature control or a more resilient fund distribution mechanism to prevent a single point of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good code quality, utilizing Solidity 0.8.28 which mitigates common integer overflow/underflow issues (7.2 Code Security). It correctly implements OpenZeppelin's ERC20 and… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a high degree of centralization through the `DEFAULT_ADMIN_ROLE`, which can assign `MINTER_ROLE` and `BURNER_ROLE`, and control fee exclusions and validator wallet (7.3 Access… |
| **Upgrades** | 4/10 | Medium | The WTBC contract is not designed with an upgrade mechanism (e.g., proxy pattern) (7.7 Upgrades). This means the contract's logic is immutable once deployed, eliminating upgrade-specific risks but… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 86.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 4 Medium · 🟢 2 Low_

### `M-01` — Single Point of Failure for Validator Wallet  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `validator` address, which receives `VALIDATOR_FEE` from transactions, is a single address controlled by the `DEFAULT_ADMIN_ROLE`. If this `validator` address is compromised, all collected fees will be diverted to an attacker, leading to a loss of funds intended for the protocol's operations or beneficiaries. There is no built-in mechanism for multi-signature control or recovery for this specific wallet. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Consider using a multi-signature wallet for the `validator` address to secure the collected fees. Alternatively, implement a mechanism to distribute fees to multiple addresses or a contract that manages funds more securely, such as a timelock or a vesting contract.


### `M-02` — Irreversible Main Liquidity Pair Creation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The primary liquidity pair with `USDT` is created once in the constructor using the provided `_router` address and is then stored as an `immutable` variable `pair`. While `updateLiquidityPair` allows managing *other* liquidity pairs, the main `pair` cannot be changed or removed. If the initial `_router` address is incorrect, or the associated DEX becomes deprecated or compromised, the core liquidity mechanism for WTBC could be permanently affected without recourse. (7.1 Architecture, 7.6 External)

**Recommendation:** While direct modification of an immutable variable is impossible, consider a future version or a wrapper contract that allows for more flexible management of the primary liquidity source, perhaps by allowing the protocol to interact with multiple DEX pairs or to migrate liquidity if necessary. For the current contract, ensure the `_router` and `USDT` addresses are thoroughly verified before deployment.


### `M-03` — High Centralization of Administrative Roles  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` holds extensive power, including the ability to grant `MINTER_ROLE` and `BURNER_ROLE`, update the validator wallet, and set fee exclusions. A compromised `DEFAULT_ADMIN_ROLE` or `MINTER_ROLE` could lead to unauthorized minting up to `MAX_SUPPLY`, manipulation of transaction fees, or diversion of validator funds, severely impacting the token's integrity and value. (7.3 Access Control, 7.4 Economic, 7.8 Operations)

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `DEFAULT_ADMIN_ROLE` and `MINTER_ROLE` to require multiple approvals for critical operations. This significantly reduces the risk of a single point of compromise. Consider time-locks for sensitive administrative actions.


### `M-04` — Hardcoded Transaction Fees  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `BURN_FEE` and `VALIDATOR_FEE` are defined as `public constant` variables, making them immutable after deployment. This lack of flexibility prevents any adjustments to the token's economic model in response to changing market conditions, community feedback, or unforeseen circumstances, potentially hindering the protocol's long-term sustainability or competitiveness. (7.4 Economic)

**Recommendation:** Introduce administrative functions to allow the `DEFAULT_ADMIN_ROLE` (preferably via multi-sig) to update `BURN_FEE` and `VALIDATOR_FEE` within predefined, reasonable bounds. This provides necessary adaptability while preventing arbitrary changes.


### `L-01` — Lack of Role Management Flexibility  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses OpenZeppelin's `AccessControl` but does not implement explicit functions for renouncing roles or transferring the `DEFAULT_ADMIN_ROLE` directly. While `_grantRole` and `_revokeRole` exist, a direct `transferAdmin` function or a `renounceRole` for the admin itself is not present, which could complicate governance transitions or reduce decentralization over time. (7.3 Access Control)

**Recommendation:** Consider adding a `transferAdmin` function that allows the current `DEFAULT_ADMIN_ROLE` to transfer its role to a new address, potentially with a two-step transfer mechanism for added security. Also, evaluate if `renounceRole` functionality for `DEFAULT_ADMIN_ROLE` is desired, understanding its implications.


### `L-02` — Hardcoded USDT Address  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `USDT` token address (0x55d398326f99059fF775485246999027B3197955) is hardcoded as a `public constant`. While this is common for specific deployments, it ties the contract to a particular token on a specific blockchain (BSC in this case). If the protocol were to expand to other networks or if the canonical USDT address were to change, the contract would need redeployment. (7.1 Architecture, 7.6 External)

**Recommendation:** For future deployments or multi-chain considerations, consider making the `USDT` address configurable via a constructor parameter or an administrative function. For the current deployment, ensure the hardcoded address is indeed the correct and canonical USDT address on the target network.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7619...30bd`](https://bscscan.com/address/0x76198caaa0e132fb76713fa76dae31fa0c4230bd) |
| **Network** | BNB Chain |
| **Price** | $508.5100 |
| **24h Volume** | $247.2K |
| **Liquidity** | $3.17M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 86.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 160 buys / 112 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x8563572a9604f246b7f8835ecfc5e2a0ff9a68b5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-trust-bitcoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-17*
