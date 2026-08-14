---
token: Axelar Wrapped LAVA
ticker: LAVA
network: arbitrum
risk_score: 79
status: critical
date: 2026-08-14
---

# Axelar Wrapped LAVA (LAVA) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 79/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/axelar-wrapped-lava-arb)

---

## Audit Summary

The audit of the `BurnableMintableCappedERC20` token and `DepositHandler` contracts revealed a critical access control vulnerability in the `DepositHandler`, allowing anyone to execute arbitrary code or self-destruct the contract. The token itself exhibits high centralization, with the owner possessing significant control over minting and burning, including a unique deterministic burning mechanism. These issues pose substantial security and economic risks.

> **Final Recommendation:** It is critical to immediately address the access control vulnerability in the `DepositHandler` contract by implementing appropriate `onlyOwner` or similar restrictions for its `execute` and `destroy` functions. Without this, any `DepositHandler` instance is fully exposed to arbitrary external calls and self-destruction. 

Furthermore, evaluate the implications of the highly centralized `owner` role for the token and consider implementing a multi-signature wallet (e.g., Gnosis Safe) for critical operations such as `mint`, `burn`, and `transferOwnership` to enhance security and reduce the single point of failure risk. Ensure comprehensive documentation and communication regarding the deterministic burning mechanism and its intended operational use.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The technical architecture (7.1) is modular, utilizing standard ERC20, Ownable, and Permit patterns. Solidity 0.8.9 mitigates integer overflow/underflow risks (7.2). A reentrancy guard is implemented… |
| **Governance / Economics** | 2/10 | High | The token's economic model (7.4) is highly centralized, with the owner having extensive control over token supply through minting and burning functions. This introduces significant governance risk… |
| **Upgrades** | 3/10 | High | The contracts are not designed with an explicit upgrade mechanism (7.7), meaning their logic is immutable once deployed. This eliminates upgrade-related risks such as proxy misconfigurations or logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Critical Access Control Vulnerability in DepositHandler  *(Severity: Critical · Status: Unresolved)*

The `DepositHandler` contract's `execute` and `destroy` functions lack any access control. Any external caller can invoke `execute(address callee, bytes calldata data)` to perform arbitrary calls from the `DepositHandler` contract to any address with arbitrary data. Similarly, `destroy(address etherDestination)` can be called by anyone to self-destruct the contract, sending any held Ether to an arbitrary address. This poses a severe risk if `DepositHandler` instances are intended to hold assets or perform sensitive operations, as they can be fully compromised by any malicious actor.

**Recommendation:** Implement robust access control for the `execute` and `destroy` functions in `DepositHandler`. For instance, restrict these functions to be callable only by a trusted `owner` address (e.g., using an `onlyOwner` modifier) or a predefined set of authorized entities. This is crucial to prevent unauthorized arbitrary code execution and contract destruction.


### `H-01` — High Centralization Risk and Owner Privileges  *(Severity: High · Status: Unresolved)*

The `BurnableMintableCappedERC20` token contract grants significant power to the `owner` address, including the ability to `mint` new tokens (up to the defined cap), `burn` tokens from specific `depositAddress` accounts, `burnFrom` any account (with allowance), and `transferOwnership`. This high level of centralization introduces a single point of failure. Compromise of the owner's private key would lead to complete control over the token's supply and critical operations, posing a substantial economic risk.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the `owner` role to manage critical operations. This would require multiple approvals for sensitive transactions, significantly enhancing security and reducing the risk associated with a single point of failure. Clearly document the owner's capabilities and the security measures in place for the owner's key.


### `M-01` — Deterministic Address Burning Mechanism  *(Severity: Medium · Status: Unresolved)*

The `burn` function allows the token owner to burn tokens from an address derived using `depositAddress(salt)`. This address is deterministically generated based on the token owner's address and the `DepositHandler`'s creation code. While potentially intended for a specific cross-chain or deposit mechanism, this grants the owner the ability to unilaterally burn tokens from these specific addresses. If these addresses are used by external users or other protocols, this capability could be unexpected or misused if not clearly communicated and understood by all stakeholders.

**Recommendation:** Ensure that the purpose and implications of the deterministic address burning mechanism are thoroughly documented and clearly communicated to all users and integrated protocols. Provide clear guidelines on how these `depositAddress` accounts are intended to be used and managed, and any potential risks associated with the owner's ability to burn tokens from them.


### `L-01` — Unused Import  *(Severity: Low · Status: Unresolved)*

The `IAxelarGateway` interface is imported in `contracts/BurnableMintableCappedERC20.sol` but is not utilized within the provided contract code. While not a functional vulnerability, unused imports can clutter the codebase, slightly increase compilation time, and potentially lead to confusion for future developers.

**Recommendation:** Remove the `import { IAxelarGateway } from './interfaces/IAxelarGateway.sol';` statement from `contracts/BurnableMintableCappedERC20.sol` if the interface is not intended for immediate use. If it's for future integration, consider adding a comment to explain its purpose.


### `I-01` — Lack of Multi-signature for Critical Operations  *(Severity: Informational · Status: Unresolved)*

Given the high level of centralization and the critical powers of the `owner` role (minting, burning, ownership transfer), relying on a single External Owned Account (EOA) for the `owner` introduces a single point of failure. A compromise of this single private key could lead to catastrophic loss of control and assets.

**Recommendation:** For enhanced security and to mitigate the risk of a single point of failure, it is strongly recommended to use a multi-signature wallet (e.g., Gnosis Safe) as the `owner` address. This would require multiple independent approvals for any critical operation, significantly increasing the security posture of the protocol.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x11e9...61af`](https://arbiscan.io/address/0x11e969e9b3f89cb16d686a03cd8508c9fc0361af) |
| **Network** | Arbitrum |
| **Price** | $0.0187 |
| **24h Volume** | $165.9K |
| **Liquidity** | $382.2K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 56.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 820 buys / 982 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xcfe0acf3b242aef2697ba94f11a31f61f2349bcb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/axelar-wrapped-lava-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
