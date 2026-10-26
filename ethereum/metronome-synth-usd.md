---
token: Metronome Synth USD
ticker: MSUSD
network: ethereum
risk_score: 41
status: medium
date: 2026-09-01
---

# Metronome Synth USD (MSUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/metronome-synth-usd-eth)

---

## Audit Summary

The SyntheticToken contract serves as an upgradeable ERC-20 token implementation, designed to interact within a broader DeFi ecosystem involving PoolRegistry, Pools, DebtTokens, and a ProxyOFT. The contract demonstrates good practices such as using OpenZeppelin's `Initializable` for upgradeability, custom error handling, and correct `_msgSender()` usage in a proxy context. However, the audit identified areas of concern, including significant centralized control by the governor, complex access control logic relying on external contracts, and a default uncapped total supply. A critical part of the token's logic, the `_transfer` function, was not provided in the audit scope, limiting a full assessment of token movement security.

> **Final Recommendation:** It is recommended to conduct a comprehensive review of the `_transfer` function and any other omitted code to ensure full security coverage, particularly regarding reentrancy and balance integrity. Strengthen the access control mechanisms by thoroughly auditing all external contracts (`IPoolRegistry`, `IPool`, `IDebtToken`, `IProxyOFT`) that interact with `SyntheticToken`'s critical functions, ensuring their security and expected behavior. Consider implementing a specific `maxTotalSupply` if an uncapped supply is not the long-term economic goal, or clearly document the implications of an uncapped supply. Ensure the `_poolRegistry.governor()` is controlled by a robust, multi-signature mechanism to mitigate the risks associated with centralized control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The technical architecture of the SyntheticToken contract (7.1 Architecture) is based on an upgradeable ERC-20 standard, utilizing OpenZeppelin's `Initializable` and `SyntheticTokenStorageV2` for… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4 Economic) of the SyntheticToken includes mechanisms for tracking bridged-in/out supply and an AMO supply, with configurable maximum limits. However, the `maxTotalSupply` is… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable proxy implementation (7.7 Upgrades), inheriting `Initializable` from OpenZeppelin and using `SyntheticTokenStorageV2`, indicating a structured approach to… |

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
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Missing `_transfer` Function Implementation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code snippet for the `SyntheticToken` contract is truncated, specifically omitting the implementation of the crucial `_transfer` function. This function is called by `transfer`, `transferFrom`, and `seize`, making it central to all token movements (7.2 Code Security). Without its full implementation, a complete security assessment of token balance updates, reentrancy risks, and other potential vulnerabilities related to token transfers cannot be performed. This represents a significant gap in the audit coverage.

**Recommendation:** Provide the complete source code for the `_transfer` function and any other omitted parts of the contract. A full audit of these critical components is necessary to ensure the integrity of token transfers and overall contract security.


### `M-02` — `maxTotalSupply` Default to `type(uint256).max`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `initialize` function, the `maxTotalSupply` variable is set to `type(uint256).max`. While this effectively means an uncapped total supply, it could be a misconfiguration if a specific total supply limit is intended for the token's economic model (7.4 Economic). If a cap is desired later, it would require a governor action to update, and the implications of an uncapped supply should be fully understood and documented to prevent unexpected economic behavior or potential hyperinflation if minting mechanisms are not tightly controlled.

**Recommendation:** Clarify the intended economic model for the SyntheticToken's total supply. If a specific cap is desired, set `maxTotalSupply` to that value during initialization or ensure the governor has a clear mandate and process to set it. If an uncapped supply is intentional, document this decision and its implications for the token's long-term stability.


### `M-03` — Centralized Control by Governor  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_poolRegistry.governor()` address, as defined by the `onlyGovernor` modifier, holds extensive control over critical parameters and the operational status of the SyntheticToken. This includes the ability to update `maxAmoSupply`, `maxTotalSupply`, `maxBridgedInSupply`, `maxBridgedOutSupply`, `proxyOFT`, `amo`, and `isActive`. Such centralized control (7.3 Access Control, 7.5 Governance) represents a single point of failure; a compromise of the governor's private key or its controlling entity could lead to severe economic damage, unauthorized minting/burning, or freezing of token operations.

**Recommendation:** Ensure the `_poolRegistry.governor()` is controlled by a robust, multi-signature wallet with a high threshold for execution. Implement strict operational procedures and access controls for the multisig signers. Consider time-locks for critical parameter changes to allow for community review and reaction time.


### `M-04` — Complex External Access Control Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The access control modifiers `onlyIfCanBurn`, `onlyIfCanMint`, and `onlyIfCanSeize` rely on complex internal functions (`_isMsgSenderDebtToken`, `_isMsgSenderPool`) that involve multiple external calls to `_poolRegistry`, `IManageable`, `IPool`, and `IDebtToken` interfaces (7.3 Access Control, 7.6 External). This intricate dependency chain increases the attack surface and introduces significant risk. A misconfiguration, bug, or malicious behavior in any of these external contracts could lead to unauthorized minting, burning, or seizing of tokens, bypassing the intended access controls. For example, if `IManageable(send

**Recommendation:** Thoroughly audit all external contracts (`IPoolRegistry`, `IPool`, `IDebtToken`, `IProxyOFT`) that interact with SyntheticToken's access control logic. Implement robust validation and sanity checks on return values from external calls. Consider simplifying the access control logic if possible, or clearly document the expected behavior and security assumptions of each external dependency.


### `L-01` — Cumulative Bridged Supply Variables  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `totalBridgedIn` and `totalBridgedOut` variables are cumulative sums, which can grow indefinitely. While `bridgedInSupply()` and `bridgedOutSupply()` correctly return the net difference, the cumulative variables themselves could reach very large numbers over time. Although `uint256` provides ample capacity, it's important to ensure that any off-chain or monitoring systems correctly interpret these cumulative values versus the net supply (7.4 Economic). The current checks against `maxBridgedOutSupply` correctly use the net `bridgedOutSupply()`, mitigating direct overflow risks for the limits.

**Recommendation:** Ensure that all external systems and integrations interacting with `totalBridgedIn` and `totalBridgedOut` are aware of their cumulative nature and differentiate them from the net `bridgedInSupply()` and `bridgedOutSupply()` values. No direct code change is required if the current logic is fully understood and intended.


### `I-01` — Correct `_msgSender()` Usage in Proxy Context  *(Severity: Informational · Status: Resolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract correctly utilizes `_msgSender()` (likely inherited from OpenZeppelin's `ContextUpgradeable` via `SynthContext`) to retrieve the original caller in an upgradeable proxy environment (7.1 Architecture, 7.2 Code Security). This is a best practice for upgradeable contracts deployed behind proxies, ensuring that access control and other sender-dependent logic correctly identify the external account initiating the transaction, rather than the proxy contract itself.

**Recommendation:** Maintain this pattern for all sender-dependent logic within the contract and any future upgrades.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xab5e...befa`](https://etherscan.io/address/0xab5eb14c09d416f0ac63661e57edb7aecdb9befa) |
| **Network** | Ethereum |
| **Price** | $0.4659 |
| **24h Volume** | $288.8K |
| **Liquidity** | $3.86M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 98.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 49 buys / 103 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x9a9e2e70919c75d80aaaa1d483c46cdbb8ac4d1b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/metronome-synth-usd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
