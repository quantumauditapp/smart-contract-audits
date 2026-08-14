---
token: Edel
ticker: EDEL
network: base
risk_score: 16
status: low
date: 2026-08-14
---

# Edel (EDEL) — Smart Contract Security Analysis | Base

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/edel-base)

---

## Audit Summary

The audit reviewed the provided Solidity code for `ContractOne`, an ERC20 token implementing a time-decaying levy mechanism and integration with Aerodrome for liquidity provision. The contract utilizes OpenZeppelin libraries for security and best practices. However, a significant portion of the levy reduction logic (`getCurrentLevyBps()` and `_updateLevyReductionStatus()`) was truncated, preventing a complete assessment of this critical component. Identified risks include centralized ownership, immutability of key operational addresses, and reliance on external protocols.

> **Final Recommendation:** It is recommended to provide the complete source code for a comprehensive security assessment, particularly for the levy reduction logic. Consider implementing a multi-signature wallet for owner functions to mitigate centralization risks. For immutable addresses, ensure robust key management or consider a mechanism for updates if operational flexibility is desired in the future. Thoroughly test all external interactions, especially with Aerodrome, to ensure expected behavior under various conditions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract demonstrates good technical practices by inheriting from OpenZeppelin's `ERC20`, `ERC20Permit`, `Ownable`, and `ReentrancyGuard`. It also uses `SafeERC20`, `Math`, and `SafeCast` for… |
| **Governance / Economics** | 7/10 | Low | The tokenomics include an initial levy on swaps that reduces over time, with a portion of initial tokens allocated for liquidity provision and the remainder to a specified recipient. Levy funds are… |
| **Upgrades** | 9/10 | Low | The contract is not designed with an upgrade proxy pattern (e.g., UUPS, Transparent) and is therefore not upgradeable. This eliminates upgrade-related risks such as storage collisions or proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 3 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The contract inherits `Ownable`, granting a single external address (the owner) significant control over the contract. While the current code does not expose many owner-only functions beyond standard `Ownable` features, any future additions of administrative functions could introduce a single point of failure or potential for malicious actions if the owner's private key is compromised. This centralization affects access control (7.3 Access Control) and operational risk (7.8 Operations).

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the contract owner to distribute control among multiple trusted parties. This enhances security by requiring multiple approvals for critical operations, reducing the risk associated with a single point of failure.


### `L-01` — Immutability of Key Operational Addresses  *(Severity: Low · Status: Unresolved)*

The `_lpRecipient` and `_levyRecipients` addresses are set as `immutable` in the constructor. While this prevents unauthorized modification, it also means these addresses cannot be updated if they become compromised, inactive, or if the project's operational needs change. This could lead to levy funds or LP tokens being sent to an inaccessible or malicious address, impacting economic stability and operations (7.4 Economic, 7.8 Operations).

**Recommendation:** Assess the long-term operational requirements. If flexibility is desired, consider implementing owner-controlled functions to update these recipient addresses. If immutability is a deliberate design choice, ensure robust, long-term security and management of the designated recipient addresses.


### `L-02` — External Protocol Dependency Risk  *(Severity: Low · Status: Unresolved)*

The contract relies on external protocols, specifically Aerodrome DEX (router, factory, pool) and WETH, for its liquidity provision mechanism. The security and functionality of `ContractOne` are directly dependent on the correct and secure operation of these external contracts. Any vulnerabilities, exploits, or unexpected behavior in Aerodrome or WETH could directly impact the functionality and assets managed by this contract (7.6 External).

**Recommendation:** Regularly monitor the security posture and operational status of all integrated external protocols. Implement robust error handling and consider circuit breakers or emergency mechanisms if the contract's functionality is critically dependent on external systems that could fail or be exploited.


### `L-03` — Publicly Callable Single-Use Liquidity Pool Creation  *(Severity: Low · Status: Unresolved)*

The `createLiquidityPool` function is `external` and can be called by any address, but only once. While the function includes checks for `ethAmount`, `maxSlippageBps`, and ensures LP tokens are sent to `_lpRecipient`, allowing any user to trigger this critical, one-time setup could lead to suboptimal initial liquidity parameters if not coordinated. A malicious or uncoordinated actor could front-run the intended caller with less favorable slippage settings (within the allowed range) or a smaller ETH amount, potentially impacting the initial market health (7.4 Economic, 7.8 Operations).

**Recommendation:** While the current implementation ensures the LP tokens go to the designated recipient, consider restricting the `createLiquidityPool` function to the owner or a trusted address. This would allow for controlled and coordinated liquidity pool creation with optimal parameters, preventing potential griefing or suboptimal initial market conditions.


### `I-01` — Incomplete Code Provided for Levy Logic  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `getCurrentLevyBps()` function and the latter part of `_updateLevyReductionStatus()` is truncated. This prevents a full and accurate assessment of the core levy calculation and reduction mechanism, which is central to the token's economic model. Without this code, potential issues such as incorrect levy calculation, unexpected reduction behavior, or edge case vulnerabilities cannot be identified.

**Recommendation:** Provide the complete and untruncated source code for all contract functions, especially `getCurrentLevyBps()` and `_updateLevyReductionStatus()`, to enable a comprehensive security audit of the levy mechanism.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfb31...cc95`](https://basescan.org/address/0xfb31f85a8367210b2e4ed2360d2da9dc2d2ccc95) |
| **Network** | Base |
| **Price** | $0.008371 |
| **24h Volume** | $93.7K |
| **Liquidity** | $500.6K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 54.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 572 buys / 299 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x566bee7ef7b39f29d150ab3be6b6242c17cc5a31)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/edel-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
