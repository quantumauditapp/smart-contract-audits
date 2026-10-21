---
token: Cea Industries
ticker: BNC4
network: bsc
risk_score: 85
status: critical
date: 2026-09-12
---

# Cea Industries (BNC4) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cea-industries-bsc)

---

## Audit Summary

The Stock4Token contract, deployed as an upgradeable BeaconProxy, implements an ERC20 token with custom scaling logic and administrative controls. The audit identified significant centralization risks associated with the 'admin' and 'issuer' roles, which possess extensive power over token supply, metadata, and the unique UI multiplier mechanism. While the contract utilizes OpenZeppelin's upgradeable standards, the core economic logic for the UI multiplier is not fully visible in the provided snippet, posing a challenge for complete assessment. Dependencies on an immutable factory address also introduce long-term operational risks.

> **Final Recommendation:** Prioritize securing the 'admin' and 'issuer' private keys with multi-signature wallets and robust operational security procedures, given their extensive control over the token's functionality and economics. Conduct a thorough review of the complete `uiMultiplier()` implementation and its interaction with token balances to ensure the scaling mechanism functions as intended and is free from vulnerabilities. Consider implementing a timelock for critical administrative actions, especially for upgrades and changes to the UI multiplier, to provide a window for community review and reaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract demonstrates good adherence to OpenZeppelin's upgradeable patterns (7.1 Architecture) and includes robust input validation for addresses and strings (7.2 Code Security). Standard… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a high degree of centralized control, with the 'admin' and 'issuer' roles holding significant power (7.3 Access Control, 7.5 Governance). The 'admin' can transfer administrative… |
| **Upgrades** | 1/10 | High | The contract correctly implements the `Initializable` pattern and `_disableInitializers()` for upgradeability via a BeaconProxy (7.7 Upgrades). This design allows for future logic updates, which is a… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 38.4% |
| **Top-3 Unlocked** | 74.0% |

## Security Findings

_🟠 2 High · 🟡 3 Medium · 🟢 1 Low_

### `H-01` — Centralized Control by Admin and Issuer Roles  *(Severity: High · Status: Unresolved)*

The `_admin` and `_issuerOverride` roles possess extensive control over the contract. The `_admin` can transfer admin rights, change token metadata (name, symbol, identifier, URI), pause/unpause the contract, and set the `_issuerOverride`. The `_issuer` (either `_issuerOverride` or `_factory.issuer()`) can mint new tokens, burn existing tokens, and set the UI multiplier. This high degree of centralization (7.3 Access Control, 7.5 Governance) means that a compromise of these keys could lead to significant damage, including arbitrary token minting/burning, contract pausing, or malicious metadata changes.

**Recommendation:** Implement multi-signature wallets for both the 'admin' and 'issuer' roles to distribute control and reduce the risk of a single point of failure. Consider adding a timelock for critical administrative actions, such as transferring admin rights or setting the issuer, to provide a delay for review and potential intervention.


### `H-02` — High Economic Power of Issuer Role  *(Severity: High · Status: Unresolved)*

The `issuer` role has direct control over the token's supply through the `mint` and `burn` functions, and can significantly influence the token's perceived value by setting the `_uiMultiplier` (7.4 Economic). While the `setUIMultiplier` function includes range and time checks, the ability to arbitrarily increase supply or manipulate the multiplier can have profound economic consequences for token holders. This concentration of economic power represents a substantial risk if the `issuer` account is compromised or acts maliciously.

**Recommendation:** Evaluate if the `mint` and `burn` functionalities are strictly necessary post-initialization, or if their scope can be limited (e.g., only for specific events or with community governance). For the `setUIMultiplier` function, consider implementing a governance mechanism or a timelock for changes, allowing token holders or a decentralized body to review and approve significant multiplier adjustments.


### `M-01` — Incomplete `uiMultiplier()` Logic for Audit  *(Severity: Medium · Status: Unresolved)*

The contract implements the `IScaledUIAmount` interface, which implies a `uiMultiplier()` function and the application of this multiplier to token balances. However, the provided code snippet does not include the implementation of `uiMultiplier()` or any functions that demonstrate how `_uiMultiplier` and `_newUIMultiplier` are actually applied to scale token balances (e.2 Code Security). Without this critical logic, it is impossible to fully assess the correctness, security, and economic impact of the token's unique scaling mechanism.

**Recommendation:** Provide the complete source code for all implemented interfaces, especially the `uiMultiplier()` function and any related balance scaling logic. A full audit of this core functionality is essential to ensure its integrity and prevent potential miscalculations or exploits.


### `M-02` — Immutability of `_factory` Address and External Dependency  *(Severity: Medium · Status: Unresolved)*

The `_factory` address is set during initialization and cannot be changed thereafter (7.8 Operations). The `issuer()` function relies on `_factory.issuer()` if `_issuerOverride` is `address(0)`. This creates a permanent, unchangeable dependency on the `IStock4Factory` contract. If the factory contract were to be compromised, upgraded maliciously, or become defunct, it could directly impact the `Stock4Token`'s `issuer` role and overall functionality, with no recourse to update the factory address.

**Recommendation:** Consider if the `_factory` address needs to be immutable. If not, implement a controlled mechanism (e.g., `onlyAdmin` with a timelock) to update the `_factory` address in case of emergencies or upgrades to the factory contract. If immutability is intended, ensure the `IStock4Factory` contract is extremely robust and its long-term availability and security are guaranteed.


### `M-03` — Centralized Upgradeability  *(Severity: Medium · Status: Unresolved)*

The contract is deployed as a BeaconProxy, allowing for future upgrades of its logic. However, the control over these upgrades is centralized under the `_admin` role (7.7 Upgrades, 7.5 Governance). This means that a single entity has the power to change the contract's entire logic, which could introduce new vulnerabilities or malicious functionality without broader consensus. While common for proxy patterns, it represents a significant trust assumption.

**Recommendation:** Implement a timelock for upgrade operations to provide a delay between the proposal and execution of an upgrade. This allows time for community review and potential objection. For enhanced decentralization, consider integrating a governance mechanism (e.g., DAO voting) to approve upgrade proposals.


### `L-01` — Potential Redundancy in `setUIMultiplier`  *(Severity: Low · Status: Unresolved)*

In the `setUIMultiplier` function, the line `_uiMultiplier = oldMultiplier;` appears before `_newUIMultiplier` and `_effectiveAt` are updated. Given that `oldMultiplier` is derived from `uiMultiplier()` (which would return the currently effective multiplier), this assignment might be redundant or a no-op if `oldMultiplier` is already equal to `_uiMultiplier`. Without the full `uiMultiplier()` implementation, its exact effect is unclear, but it could potentially be simplified or clarified (7.2 Code Security).

**Recommendation:** Review the logic of `setUIMultiplier` in conjunction with the full `uiMultiplier()` implementation. If `_uiMultiplier = oldMultiplier;` is indeed redundant, it should be removed for clarity. If it serves a specific purpose (e.g., finalizing a previous pending update), add a comment to explain its intent.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7c8d...545c`](https://bscscan.com/address/0x7c8d5502b544ddaf8852fc46d1174e34876d545c) |
| **Network** | BNB Chain |
| **Price** | $5.2300 |
| **24h Volume** | $5.78M |
| **Liquidity** | $1.82M |
| **Volume / Liquidity** | 3.2× |
| **Token Age** | 4d |
| **Top-10 Holders** | 51.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 19448 buys / 19886 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xbec6906a984f4695aca0f15bafa7de5eb45b54ab)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cea-industries-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
