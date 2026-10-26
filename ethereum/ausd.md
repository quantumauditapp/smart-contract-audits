---
token: AUSD
ticker: AUSD
network: ethereum
risk_score: 8
status: low
date: 2026-09-04
---

# AUSD (AUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ausd-eth)

---

## Audit Summary

The AgoraDollar contract serves as the implementation logic for an EIP-1967 Transparent Proxy, functioning as an ERC-20 token with additional EIP-2612 and EIP-3009 features. The contract employs a custom StorageLib for explicit storage management and a comprehensive role-based access control system. Key risks include significant centralized control through powerful roles and the proxy admin, and a critical limitation in the audit scope due to the unavailability of the AgoraDollarCore contract's source code, preventing a full verification of core logic.

> **Final Recommendation:** Prioritize a full security audit of the `AgoraDollarCore` and `StorageLib` contracts to ensure the integrity of core token logic and storage management. Implement robust multi-signature or time-locked mechanisms for critical administrative roles and the `ProxyAdmin` owner to mitigate centralized control risks. Establish clear, tested upgrade procedures that meticulously account for the custom storage layout to prevent potential data corruption during future upgrades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes `ShortStrings` for gas-efficient name/symbol storage and a custom `StorageLib` for explicit storage management, which is a positive for upgradeability (7.1 Architecture).… |
| **Governance / Economics** | 9/10 | Low | The contract implements a robust role-based access control system with distinct roles for various operations, such as Minter, Burner, Pauser, and Freezer (7.3 Access Control). However, the design… |
| **Upgrades** | 2/10 | High | The contract utilizes the EIP-1967 Transparent Proxy pattern, providing a standard mechanism for upgradeability. The custom `StorageLib` explicitly defines storage slots, aiming to prevent storage… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → EOA |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 74.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 8 Informational_

### `M-02` — Denial of Service via Pausing Mechanisms  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract includes multiple pausing mechanisms (e.g., `isTransferPaused`, `isMintPaused`, `isFreezingPaused`, `isSignatureVerificationPaused`, `isBridgingPaused`). While intended for emergency situations, these controls grant significant power to halt critical operations. Typically managed by a `PAUSER_ROLE`, misuse or compromise of this role could lead to a denial of service for users, preventing them from transferring tokens, minting new tokens, or performing other essential functions. This introduces a single point of failure for operational continuity (7.2 Code Security, 7.8 Operations).

**Recommendation:** Implement multi-signature control for the `PAUSER_ROLE` to distribute authority and reduce the risk of a single point of compromise. Clearly define the conditions under which pausing mechanisms can be activated and deactivated, and ensure these are communicated transparently to users. Consider adding a time-lock for unpausing operations to allow for community oversight.


### `M-04` — Incomplete Audit Scope due to Missing Core Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code is for the `AgoraDollar` contract, which inherits from `AgoraDollarCore` and utilizes `StorageLib`. Crucially, the source code for `AgoraDollarCore` and `StorageLib` was not provided. Without these core components, a comprehensive security audit of critical functionalities such as token transfers, minting, burning, access control enforcement, pausing mechanisms, and EIP-2612/EIP-3009 signature verification cannot be performed. This significantly limits the ability to identify potential vulnerabilities in the fundamental operations of the token (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Provide the complete source code for `AgoraDollarCore` and `StorageLib` to enable a full and thorough security audit of all contract functionalities. Until a full audit is completed, the security posture of the core token logic remains unverified.


### `L-01` — Compiler Version Mismatch  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `pragma solidity 0.8.28` directive in the provided source code indicates that the contract is intended to be compiled with Solidity version 0.8.28. However, the prefill data specifies a `compiler_version: 0.8.21`. While minor version differences within the 0.8.x series are often backward compatible, it is best practice to compile contracts with the exact pragma version to ensure consistent behavior, avoid potential compiler-specific issues, and prevent unexpected warnings or errors that might arise from subtle changes between compiler versions (7.2 Code Security).

**Recommendation:** Ensure that the contract is compiled using the exact Solidity compiler version specified in its `pragma` directive (0.8.28). Update the deployment pipeline or documentation to reflect the correct compiler version.


### `I-01` — Redundant `proxyAdminAddress()` in Implementation  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `proxyAdminAddress()` function in the implementation contract reads a `proxyAdminAddress` from its own storage via `StorageLib`. In a standard EIP-1967 Transparent Proxy setup, the actual proxy admin address is stored in the proxy contract itself (at a specific storage slot). Storing a copy of this address within the implementation's storage is redundant and could potentially lead to inconsistencies if the proxy admin is changed directly on the proxy but not updated in the implementation's storage. While likely intended for informational purposes, it could be misleading (7.1 Architecture).

**Recommendation:** Consider removing the `proxyAdminAddress()` function from the implementation contract, as the authoritative source for the proxy admin address is the proxy contract itself. If it must remain, clarify in documentation that this is a cached or informational value and not the authoritative source of truth for the proxy's admin.


### `I-02` — Centralized Control via Proxy Admin and Extensive Roles  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract design exhibits significant centralization of control. The owner of the EIP-1967 Transparent Proxy's `ProxyAdmin` (0x68898b77ebf7b55dca8a2e62d6fd74959a2930e2, an EOA) possesses ultimate authority over contract upgrades, allowing for arbitrary changes to the contract's logic. Additionally, the contract employs numerous powerful roles (Minter, Burner, Pauser, Freezer, Bridge Minter/Burner, Rate Limit Manager) which, if compromised or misused, can lead to severe economic consequences such as arbitrary token minting, freezing of user funds, or halting all token operations. This represents a high trust assumpti

**Recommendation:** Implement multi-signature wallets (e.g., Gnosis Safe) for the `ProxyAdmin` owner and all critical administrative roles. Consider introducing time-locks for sensitive operations like upgrades or role changes to provide a delay for community review and emergency intervention. Clearly document the responsibilities and operational procedures for each role.


### `I-03` — Storage Collision Risk in Custom Upgradeable Design  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract employs a custom `StorageLib` to manage explicit storage slots for different modules (ERC20, ERC2612, EIP3009, etc.). While this approach is intended to prevent storage collisions in an upgradeable proxy environment, it introduces significant complexity. Any future upgrades or modifications to `AgoraDollarCore` or `StorageLib` must meticulously adhere to the defined storage layout. A single miscalculation or oversight in slot allocation could lead to critical data corruption, overwriting essential state variables, or causing unexpected contract behavior (7.1 Architecture, 7.7 Upgrades). The `Initializable`

**Recommendation:** Ensure rigorous testing and formal verification of the `StorageLib` and its interaction with `AgoraDollarCore` to confirm correct storage slot allocation and prevent collisions. Implement a robust upgrade testing framework that includes simulating storage layout changes. Document the storage layout explicitly and enforce strict review processes for any changes to `AgoraDollarCore` or `StorageLib` that affect storage.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 88.8% of supply. What remains: 42.0% in wallets, 46.7% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as AUSD (AUSD), market cap $171M, rank #192. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $52.0M (DexScreener, all pools). 24h trading volume $2.7M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $52.0M of DEX liquidity across 6 pools. Launch: 753 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0000...012a`](https://etherscan.io/address/0x00000000efe302beaa2b3e6e1b18d08d69a9012a) |
| **Network** | Ethereum |
| **Price** | $0.9999 |
| **24h Volume** | $2.68M |
| **Liquidity** | $34.17M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 88.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 64 buys / 50 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xbafead7c60ea473758ed6c6021505e8bbd7e8e5d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ausd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
