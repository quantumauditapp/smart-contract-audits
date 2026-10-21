---
token: ZK Coin
ticker: ZKC
network: ethereum
risk_score: 85
status: critical
date: 2026-08-31
---

# ZK Coin (ZKC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zk-coin-eth)

---

## Audit Summary

The ZKC token contract implements an upgradeable ERC-20 token with a custom epoch-based emission schedule and role-based access control. The audit identified several high and medium severity issues primarily related to tokenomics design, centralization of control, and potential for misinterpretation of core functions. Key concerns include a non-standard `totalSupply()` implementation, significant centralization risks in initial token distribution and critical parameter initialization, and reliance on an unaudited external library for core emission logic.

> **Final Recommendation:** It is strongly recommended to address the high-severity issues, particularly the non-standard `totalSupply()` implementation and the centralization risks associated with initial minters. A thorough audit of the `Supply` library is crucial to validate the core tokenomics. Consider implementing multi-signature control for critical roles like `ADMIN_ROLE` and initial minters to mitigate centralization risks. Enhance documentation for the `totalSupply()` function and reward claiming logic to prevent misinterpretation by integrators and users. Ensure robust operational procedures are in place for the `epoch0StartTime` initialization.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages battle-tested OpenZeppelin upgradeable libraries for ERC-20, access control, and UUPS proxy patterns, contributing to a robust technical foundation (7.1 Architecture, 7.2 Code… |
| **Governance / Economics** | 1/10 | High | The tokenomics design includes an epoch-based emission schedule with distinct roles for PoVW and Staking minters (7.4 Economic). Initial token distribution is managed by two designated minters, which… |
| **Upgrades** | 1/10 | High | The contract utilizes the UUPS upgradeable proxy pattern, allowing for future logic updates (7.7 Upgrades). Upgrade authorization is appropriately restricted to the `ADMIN_ROLE` via… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## Security Findings

_🟠 2 High · 🟡 3 Medium · 🟢 1 Low_

### `H-01` — Misleading `totalSupply()` Implementation  *(Severity: High · Status: Unresolved)*

The `totalSupply()` function overrides the standard ERC-20 behavior by returning a *projected* supply based on the current epoch's calculated emissions (`getSupplyAtEpochStart(getCurrentEpoch())`), rather than the actual number of tokens minted and in circulation (`super.totalSupply()`). This deviation from the ERC-20 standard can lead to significant confusion for users, incorrect calculations by external protocols, and misrepresentation of the token's true circulating supply. The actual minted supply is available via `claimedTotalSupply()`, but this requires specific knowledge of the contract's non-standard implementation.

**Recommendation:** It is highly recommended to align `totalSupply()` with the ERC-20 standard by returning the actual minted supply (`super.totalSupply()`). If a projected supply is necessary for specific use cases, it should be provided through a clearly named, separate function (e.g., `getProjectedSupply()`) to avoid ambiguity and maintain ERC-20 compliance.


### `H-02` — Centralization Risk of Initial Minting  *(Severity: High · Status: Unresolved)*

The `initialMint` function allows `initialMinter1` or `initialMinter2` to mint the entire `INITIAL_SUPPLY` to any specified recipients. If either of these initial minter addresses is compromised or acts maliciously, they could mint the entire initial supply to themselves or other unauthorized addresses, leading to a complete loss of control over the initial token distribution.

**Recommendation:** Implement multi-signature control for the `initialMinter1` and `initialMinter2` roles to distribute trust and prevent single points of failure. Alternatively, consider a more decentralized initial distribution mechanism or a time-locked release schedule for the initial supply.


### `M-01` — Critical `epoch0StartTime` Initialization  *(Severity: Medium · Status: Unresolved)*

The `epoch0StartTime` variable, which dictates the entire token emission schedule, is set only once via the `initializeV3()` reinitializer. This function is restricted to the `ADMIN_ROLE`. The precise timing of this initialization is critical; an accidental delay or premature call could significantly alter the intended tokenomics and emission curve. This represents a single point of operational risk.

**Recommendation:** Establish clear, documented operational procedures for the `initializeV3()` call, including a specific window for execution. Consider adding a time-lock or a multi-signature requirement for this critical function to ensure careful deliberation before execution. Implement monitoring to detect any unintended delays or premature calls.


### `M-02` — Reliance on Unaudited `Supply` Library for Core Tokenomics  *(Severity: Medium · Status: Unresolved)*

The contract's core tokenomics, including the calculation of total supply at each epoch (`getSupplyAtEpochStart`) and epoch-specific emissions (`getEmissionsForEpoch`), are delegated to an external `Supply` library. The source code for this library was not provided for audit. Without a thorough review of the `Supply` library, the accuracy, security, and economic soundness of the token's emission schedule cannot be fully verified. Any vulnerabilities or incorrect logic within this library would directly impact the `ZKC` token.

**Recommendation:** Provide the complete source code for the `Supply` library for a comprehensive security and economic audit. Ensure the library's logic is thoroughly tested, especially for edge cases in epoch calculations and emission rates.


### `M-03` — Centralized Control over Key Roles and Upgrades  *(Severity: Medium · Status: Unresolved)*

The `ADMIN_ROLE` holds extensive power, including the ability to grant `POVW_MINTER_ROLE` and `STAKING_MINTER_ROLE`, set the critical `epoch0StartTime`, and authorize contract upgrades via `_authorizeUpgrade`. This high degree of centralization means that a compromise of the `ADMIN_ROLE` address could lead to significant security breaches, including unauthorized minting, alteration of tokenomics, or malicious contract upgrades.

**Recommendation:** Implement multi-signature control for the `ADMIN_ROLE` to distribute trust and reduce the risk associated with a single point of failure. Consider separating critical responsibilities into distinct roles with different access policies, if feasible, to further decentralize control.


### `L-01` — Potential for Reward Claiming Logic Misinterpretation  *(Severity: Low · Status: Unresolved)*

The functions `getTotalPoVWEmissionsAtEpochStart` and `getTotalStakingEmissionsAtEpochStart` calculate the *cumulative* total emissions available up to a given epoch. These are then used to check against `poVWClaimed` and `stakingClaimed`, which are also *cumulative* totals of claimed rewards. While this logic appears consistent for cumulative tracking, the function names might be misinterpreted by developers or auditors as representing *epoch-specific* emissions, potentially leading to confusion or incorrect assumptions about the reward distribution mechanism.

**Recommendation:** Enhance clarity by either renaming the functions to explicitly indicate cumulative totals (e.g., `getOverallPoVWEmissionsUpToEpoch`) or by adding comprehensive NatSpec documentation to explain that these functions return cumulative values, not epoch-specific ones.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0000...5555`](https://etherscan.io/address/0x000006c2a22ff4a44ff1f5d0f2ed65f781f55555) |
| **Network** | Ethereum |
| **Price** | $0.04848 |
| **24h Volume** | $1.8K |
| **Liquidity** | $81.2K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 302 buys / 293 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x39d8c5f8c61e975e9aa68e61609d40b93fcb452496639648d60d4f4af89f7872)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zk-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
