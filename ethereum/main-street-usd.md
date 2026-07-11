---
token: Main Street USD
ticker: MSUSD
network: ethereum
risk_score: 84
status: critical
date: 2026-06-21
---

# Main Street USD (MSUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 84/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/main-street-usd-eth)

---

## Audit Summary

This audit covers the ERC1967Proxy contract, which is a standard upgradeable proxy implementation from OpenZeppelin. The contract facilitates upgradeability by delegating calls to an implementation address stored in an EIP-1967 compliant storage slot. The core proxy logic is robust and battle-tested, with inherent risks primarily stemming from the deployment process, the security of the admin key, and the design of the implementation contracts.

> **Final Recommendation:** The ERC1967Proxy contract is a robust and secure component, leveraging OpenZeppelin's audited libraries. The primary risks are not within the proxy's code itself but in its deployment, the security of the admin key, and the design and deployment of the implementation contracts. It is crucial to ensure proper initialization of implementation contracts and robust access control for the admin role. Consider a Premium Deploy option for enhanced security during deployment, including multi-signature control over the admin key and a time-locked upgrade mechanism for critical contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes OpenZeppelin's battle-tested ERC1967Proxy, Proxy, and ERC1967Utils libraries, ensuring a high standard of code security (7.2 Code Security). It correctly implements the EIP-1967  |
| **Governance / Economics** | 1/10 | High | This ERC1967Proxy contract itself does not contain any economic or governance logic (7.4 Economic, 7.5 Governance). Its sole purpose is to delegate calls to an implementation contract. Therefore, econ |
| **Upgrades** | 3/10 | High | The contract is designed for upgradeability using the EIP-1967 proxy pattern (7.7 Upgrades). It allows for the implementation contract to be changed via the `upgradeToAndCall` function, which also sup |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ⚠️ Unverified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 2 Low · ⚪ 3 Informational_

### `L-01` — Implementation Contract Initialization Vulnerability  *(Severity: Low · Status: Unresolved)*

The proxy's constructor calls `upgradeToAndCall`, which can execute initialization logic on the implementation. If the implementation contract's `initialize` function is not called correctly or is omitted during deployment, it can lead to an uninitialized state. This often allows an attacker to call the `initialize` function themselves, gaining administrative control over the implementation contract, even if the proxy's admin is secure. This is a common pitfall in proxy deployments.

**Recommendation:** Ensure that the `_data` parameter in the proxy's constructor or a subsequent `upgradeToAndCall` call securely invokes the `initialize` function of the implementation contract. The `initialize` function should use an `initializer` modifier to prevent multiple calls and ensure it's called by a trusted address (e.g., the deployer or a governance contract).


### `L-02` — Admin Key Security Criticality  *(Severity: Low · Status: Unresolved)*

The security of the entire system relies heavily on the private key or mechanism controlling the `admin` role, which has the power to upgrade the implementation contract (7.3 Access Control, 7.8 Operations). A compromise of this admin key would allow an attacker to deploy a malicious implementation, potentially leading to a complete loss of funds or system control.

**Recommendation:** Implement robust security measures for the admin key. This typically involves using a multi-signature wallet (e.g., Gnosis Safe) for the admin address, potentially with a time-lock mechanism for upgrades. Avoid using a single externally owned account (EOA) as the sole admin.


### `I-01` — Standard OpenZeppelin Proxy Implementation  *(Severity: Informational · Status: Resolved)*

The contract utilizes the `ERC1967Proxy` from OpenZeppelin Contracts, which is a widely adopted, thoroughly audited, and battle-tested library for upgradeable proxy patterns. This significantly reduces the risk of vulnerabilities within the proxy's core logic (7.2 Code Security).

**Recommendation:** Continue to rely on well-established and audited libraries like OpenZeppelin. Regularly monitor for updates and security advisories from the OpenZeppelin team.


### `I-02` — Storage Collision Risk in Implementation Contracts  *(Severity: Informational · Status: Unresolved)*

While the `ERC1967Proxy` itself uses EIP-1967 compliant storage slots to prevent collisions with its own logic, the implementation contract must carefully manage its storage layout across upgrades. Incorrectly modifying the storage layout in a new implementation can lead to storage collisions, corrupting data or causing unexpected behavior (7.1 Architecture).

**Recommendation:** Adhere strictly to storage layout compatibility rules when developing and upgrading implementation contracts. Avoid changing the order or type of state variables, and only append new variables to the end of the storage layout. Utilize tools like OpenZeppelin's Upgrades Plugins to detect potential storage collisions during development and deployment.


### `I-03` — Immutability of Proxy Core Logic  *(Severity: Informational · Status: Resolved)*

The `ERC1967Proxy` contract's core delegation logic (`_delegate`, `fallback`) is immutable once deployed. This means that the fundamental mechanism of how the proxy operates cannot be changed, providing a stable and predictable base layer (7.1 Architecture). Only the target implementation contract can be upgraded.

**Recommendation:** This is an inherent design feature of the proxy pattern and is considered a strength, as it ensures the proxy's behavior remains consistent. No specific action is required.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4ba0...7c00`](https://etherscan.io/address/0x4ba01f22827018b4772cd326c7627fb4956a7c00) |
| **Network** | Ethereum |
| **Price** | $0.2725 |
| **24h Volume** | $5.15M |
| **Liquidity** | $253.9K |
| **Volume / Liquidity** | 20.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 99.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1155 buys / 990 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Frequently Asked Questions

### Is Main Street USD a scam?

Based on available data, Main Street USD exhibits high-risk characteristics, especially its highly concentrated token distribution where 99.2% is held by the top 10 wallets, and unlocked liquidity. While the contract is verified and ownership renounced, these don't mitigate the direct market manipulation or rug pull potential from concentrated holders and unprotected liquidity. It requires careful consideration.

### Is Main Street USD safe to buy?

Investing in Main Street USD carries significant risks. The extreme centralization, with 99.2% of tokens held by the top 10 addresses, makes it vulnerable to price manipulation. Additionally, liquidity is not locked, posing a risk of liquidity withdrawal (rug pull) that could leave investors unable to sell. These factors contribute to its high-risk score.

### Has Main Street USD been audited?

The Main Street USD contract has been verified on Ethereum, meaning its code is publicly visible and matches the deployed bytecode. However, "contract verified" is not the same as a comprehensive security audit by an independent third party. An audit typically involves deeper code analysis for vulnerabilities beyond just transparency.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x111ce2a60c30f6058a57d0dbae1a39a42d998826-0x4ba01f22827018b4772cd326c7627fb4956a7c00-0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/main-street-usd-eth)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-21*
