---
token: DORA
ticker: DORA
network: bsc
risk_score: 1
status: low
date: 2026-09-14
---

# DORA (DORA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dora-bsc)

---

## Audit Summary

The TokenV2 contract is an upgradeable ERC20 token utilizing OpenZeppelin's upgradeable libraries. It implements custom transfer restrictions preventing interaction with specified Uniswap pools, which can be removed by the owner. The contract exhibits good code quality and follows standard upgradeability patterns. However, significant centralization risks exist due to the owner's control over the entire token supply and the ability to unilaterally disable critical transfer constraints, leading to a High overall risk level.

> **Final Recommendation:** To mitigate the identified risks, consider implementing a multi-signature wallet for ownership of the contract, especially for critical functions like `removeTransferConstraints`, to reduce single points of failure. Evaluate the long-term implications of the owner holding the entire token supply and consider a more decentralized distribution strategy if appropriate for the project's goals. For future upgrades, meticulously plan storage layouts to avoid collisions and ensure backward compatibility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The TokenV2 contract demonstrates good technical architecture (7.1) by extending well-audited OpenZeppelin upgradeable contracts for ERC20, ERC20Permit, and Ownable functionalities. Code security… |
| **Governance / Economics** | 9/10 | Low | The economic model (7.4) of TokenV2 presents significant centralization. The entire `maxSupply` is minted to the contract initializer (owner), giving the owner 100% of the initial token supply.… |
| **Upgrades** | 10/10 | Low | The contract is designed for upgradeability (7.7) using OpenZeppelin's `Upgradeable` pattern, correctly employing an empty constructor and an `initializer` function. This approach allows for future… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — UNCX Locker |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control Over Transfer Constraints and Token Supply  *(Severity: High · Status: Unresolved)*

The `owner` of the contract has complete and unilateral control over two critical aspects: 1) The entire `maxSupply` of tokens is minted to the `msg.sender` (the owner/initializer) during initialization, meaning the owner holds 100% of the initial token supply. 2) The `removeTransferConstraints()` function, callable only by the owner, can permanently disable the restrictions on transferring tokens to/from Uniswap V2 and V3 pools. This level of centralization introduces significant trust assumptions and a single point of failure, as a compromised owner key could lead to market manipulation or unintended token behavior.

**Recommendation:** Implement a multi-signature wallet for the contract's ownership to distribute control and reduce the risk of a single point of failure. Consider a more decentralized initial token distribution mechanism if the project aims for community governance or broader participation. For the `removeTransferConstraints` function, evaluate if a time-locked or governance-controlled mechanism would be more appropriate than immediate owner-only execution.


### `M-01` — Irreversible Removal of Transfer Constraints  *(Severity: Medium · Status: Unresolved)*

The `removeTransferConstraints()` function allows the owner to set the `transferConstraints` flag to `false`. Once set to `false`, there is no corresponding function to re-enable these constraints. This design choice makes the removal of transfer restrictions irreversible, which might not be desired in all scenarios, especially if market conditions or regulatory requirements change and necessitate re-implementing such controls.

**Recommendation:** If future scenarios might require re-enabling transfer constraints, consider adding a function (also `onlyOwner` or governance-controlled) to set `transferConstraints` back to `true`. Alternatively, clearly document this irreversible behavior as an intended design decision.


### `M-02` — Potential for Storage Collisions in Future Upgrades  *(Severity: Medium · Status: Unresolved)*

The contract introduces several custom state variables (`maxSupply`, `metaURI`, `transferConstraints`, `uniswapV2Pool`, `uniswapV3Pool`) in addition to those inherited from OpenZeppelin's upgradeable contracts. While the current implementation is correct, future upgrades must carefully manage storage slots to avoid collisions. Adding new state variables in an upgrade without proper slot management (e.g., appending new variables at the end of the storage layout) could overwrite existing data, leading to critical state corruption.

**Recommendation:** Adhere strictly to OpenZeppelin's upgradeability guidelines for storage management. When performing upgrades, always append new state variables to the end of the contract's storage layout. Utilize tools like `hardhat-upgrades` or `truffle-upgrades` to assist in detecting and preventing storage collisions during development and deployment of new versions.


### `L-01` — No Event for `removeTransferConstraints`  *(Severity: Low · Status: Unresolved)*

The `removeTransferConstraints()` function modifies the `transferConstraints` state variable, which is a critical operational change for the token. However, no event is emitted upon its execution. While `transferConstraints` is a public variable and its state can be read, an event would provide a more efficient and reliable way for off-chain systems (e.g., block explorers, dApps, monitoring services) to track this significant change.

**Recommendation:** Emit an event, such as `TransferConstraintsRemoved(address indexed owner)`, within the `removeTransferConstraints()` function to provide clear and auditable signaling of this state change.


### `I-01` — Dependency on OpenZeppelin Upgradeable Contracts  *(Severity: Informational · Status: Unresolved)*

The contract heavily relies on OpenZeppelin's upgradeable contracts (`ERC20Upgradeable`, `ERC20PermitUpgradeable`, `OwnableUpgradeable`). While these libraries are widely used and well-audited, any undiscovered vulnerability in these external dependencies could indirectly affect the security of the TokenV2 contract.

**Recommendation:** Regularly monitor OpenZeppelin's security advisories and ensure that the project's dependencies are kept up-to-date with the latest secure versions. Consider pinning specific versions of OpenZeppelin contracts to ensure deterministic behavior.


### `I-02` — Initial Mint to Initializer  *(Severity: Informational · Status: Unresolved)*

During the `initialize` function, the entire `maxSupply` of tokens is minted to `msg.sender`. This is a common pattern for fixed-supply tokens where the deployer or a designated address holds the initial supply. However, it means the initial distribution is entirely centralized to one address.

**Recommendation:** This is an intended design choice. Ensure that the implications of this initial distribution are clearly communicated to users and stakeholders. If a more decentralized distribution is desired, consider implementing a vesting schedule, airdrop mechanism, or other distribution strategies post-initialization.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x23fe...8888`](https://bscscan.com/address/0x23fe903be385832fd7bb82bf1fee93f696278888) |
| **Network** | BNB Chain |
| **Price** | $0.002756 |
| **24h Volume** | $370.4K |
| **Liquidity** | $163.8K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 5.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1361 buys / 1208 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x338041378692867363672fd0dcf8544ac159eaed)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dora-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*
