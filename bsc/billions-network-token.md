---
token: Billions Network Token
ticker: BILL
network: bsc
risk_score: 63
status: high
date: 2026-08-12
---

# Billions Network Token (BILL) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 63/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/billions-network-token-bsc)

---

## Audit Summary

The audit of the BillOFT contract, an upgradeable LayerZero Omnichain Fungible Token (OFT) implementation, identified a high-severity architectural deviation in its ownership pattern, where a multisig directly owns the implementation instead of the ProxyAdmin. Other findings include centralized control inherent to multisig ownership and dependency on LayerZero protocol security. The contract leverages well-audited OpenZeppelin and LayerZero libraries.

> **Final Recommendation:** It is strongly recommended to reconfigure the ownership of the `BillOFT` implementation contract to align with the standard TransparentUpgradeableProxy pattern, where the `ProxyAdmin` contract acts as the owner. This ensures proper separation of concerns and adherence to established security best practices for upgradeable contracts. Additionally, consider implementing time-locks for critical administrative actions to enhance security and provide a buffer for user response.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The BillOFT contract is a minimal wrapper around the `OFTUpgradeable` and `Ownable` libraries, which are generally well-audited. The core logic for token functionality and cross-chain transfers is… |
| **Governance / Economics** | 1/10 | High | The contract exhibits centralized control (7.5 Governance) through a 3/5 multisig owner, which manages critical administrative functions and upgrades. While a multisig enhances security over a single… |
| **Upgrades** | 4/10 | Medium | The contract utilizes a TransparentUpgradeableProxy pattern (7.7 Upgrades) with an OpenZeppelin ProxyAdmin, which is owned by a 3/5 multisig, providing a robust upgrade mechanism. The… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 26.2% |
| **Top-3 Unlocked** | 65.4% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Non-Standard Ownership Pattern for Transparent Upgradeable Proxy  *(Severity: High · Status: Unresolved)*

The `initialize` function calls `__Ownable_init(_delegate)`, and based on the prefill data, the `_delegate` address (a 3/5 multisig) has been set as the direct owner of the `BillOFT` implementation contract. For a TransparentUpgradeableProxy, the standard and recommended pattern is for the `ProxyAdmin` contract to be the owner of the implementation. This allows the `ProxyAdmin` to manage upgrades and other owner-restricted functions on the implementation, while the `ProxyAdmin` itself is owned by a secure entity (like a multisig). By directly assigning ownership of the implementation to the multisig, the `ProxyAdmin`'s role in managing the implementation's owner-restricted functions is bypa…

**Recommendation:** Reconfigure the ownership such that the `ProxyAdmin` contract is the owner of the `BillOFT` implementation. The `initialize` function should call `__Ownable_init()` (without arguments), which would set the `ProxyAdmin` (as `msg.sender` during initialization) as the owner. The multisig should then own the `ProxyAdmin` contract, maintaining secure control over the upgrade process. This aligns with the intended security model of TransparentUpgradeableProxies.


### `M-01` — Centralized Control by Multisig Owner  *(Severity: Medium · Status: Unresolved)*

The `BillOFT` contract's owner is a 3/5 multisig, which holds significant control over critical functions, including potential LayerZero configurations and any future owner-restricted methods. While a multisig reduces single points of failure, it still represents a centralized entity that could, if compromised or malicious, exert undue influence over the token's operations.

**Recommendation:** Implement time-locks for critical administrative actions to provide a delay for users to react to potentially malicious or erroneous operations. Consider further decentralizing control over time, if feasible, by integrating governance mechanisms or distributing ownership among a wider set of stakeholders.


### `L-01` — Reliance on External LayerZero Protocol Security  *(Severity: Low · Status: Unresolved)*

The `BillOFT` contract is an Omnichain Fungible Token (OFT) built on LayerZero, meaning its cross-chain functionality and security are inherently dependent on the LayerZero protocol. Any vulnerabilities, exploits, or operational failures within the LayerZero endpoint, relayer network, or oracle mechanisms could directly impact the integrity and availability of cross-chain token transfers for BillOFT.

**Recommendation:** While this is an inherent risk of using a bridging solution, it is crucial to monitor LayerZero's security announcements, audits, and operational status. Users should be made aware of the underlying cross-chain dependency and its associated risks.


### `I-01` — Redundant or Conflicting Ownable Import  *(Severity: Informational · Status: Unresolved)*

The `BillOFT` contract explicitly imports `Ownable` from `@openzeppelin/contracts/access/Ownable.sol`. However, `BillOFT` inherits `OFTUpgradeable`, which itself inherits `OwnableUpgradeable`. This creates a potentially redundant or conflicting import, as `OwnableUpgradeable` is the correct version for upgradeable contracts. While it might not cause a direct runtime error if the compiler resolves it correctly, it can lead to confusion and potential misapplication of `Ownable` functions or initialization patterns.

**Recommendation:** Remove the explicit `import { Ownable } from "@openzeppelin/contracts/access/Ownable.sol";` statement. Rely on the `OwnableUpgradeable` inheritance provided by `OFTUpgradeable` to ensure consistent and correct usage of access control for an upgradeable contract.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdf24...1fa5`](https://bscscan.com/address/0xdf24f8c21cb404b3031a450d8e049d6e39fc1fa5) |
| **Network** | BNB Chain |
| **Price** | $0.0235 |
| **24h Volume** | $82.1K |
| **Liquidity** | $42.1K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 92.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 376 buys / 461 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x81c170260493428923431e76b7c99f11268fec5a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/billions-network-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
