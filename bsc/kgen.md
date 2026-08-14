---
token: KGEN
ticker: KGEN
network: bsc
risk_score: 78
status: critical
date: 2026-08-14
---

# KGEN (KGEN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 78/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kgen-bsc)

---

## Audit Summary

The KgenOFT contract implements an Omnichain Fungible Token (OFT) utilizing LayerZero for cross-chain functionality. It incorporates robust access control via OpenZeppelin's `AccessControl` and `Ownable2Step` patterns, along with pausing mechanisms and a blacklist. Critical administrative roles are managed by a 2/3 multisig, enhancing security. The contract demonstrates good adherence to security best practices for EVM development.

> **Final Recommendation:** It is recommended to carefully review the distribution of roles and responsibilities within the multisig to ensure robust operational security and prevent potential misuse of administrative powers. Consider indexing all critical event parameters to enhance off-chain monitoring capabilities. Maintain strict security protocols for the multisig keys and ensure a clear emergency response plan is in place for potential security incidents.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract exhibits strong technical security, leveraging Solidity 0.8.x for automatic overflow/underflow protection, `ReentrancyGuard` for reentrancy prevention, and `SafeERC20` for secure token… |
| **Governance / Economics** | 1/10 | High | Governance is centralized, with a 2/3 multisig holding the `DEFAULT_ADMIN_ROLE`, which grants extensive control over the contract's operations (7.5 Governance). This includes the ability to pause the… |
| **Upgrades** | 6/10 | Medium | The KgenOFT contract is implemented as a standard, non-upgradeable contract (7.7 Upgrades). It does not utilize proxy patterns for in-place upgrades. Any future modifications to the contract logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control Over Critical Functions  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE`, held by a 2/3 multisig, possesses extensive control over critical contract functions. This includes the ability to pause the contract (`setPaused`), pause cross-chain operations (`setCrossChainPaused`), blacklist users (`setBlacklistStatus`, `batchSetBlacklistStatus`), manage trusted forwarders (`addTrustedForwarder`, `removeTrustedForwarder`, `updateTrustedForwarder`), and recover ERC20/ETH (`recoverERC20`, `recoverETH`). While a multisig mitigates single-point-of-failure risks, the concentration of such broad power in a single entity (the multisig) represents a significant centralization risk. Compromise or malicious action by the multisig signers could lead to a…

**Recommendation:** While a multisig is a good mitigation, consider further decentralizing control where feasible, or implementing time-locks/governance delays for highly sensitive operations. Ensure the multisig signers are diverse, trusted, and follow stringent key management practices. Implement robust monitoring for all administrative actions.


### `M-01` — Potential Gas Limit Issues in `batchSetBlacklistStatus`  *(Severity: Medium · Status: Unresolved)*

The `batchSetBlacklistStatus` function iterates through an array of `accounts` to update their blacklist status. If the `accounts` array contains a very large number of addresses, the transaction's gas cost could exceed the block gas limit. This would prevent the function from being executed, making it impossible to blacklist a large batch of users in a single transaction, potentially hindering administrative operations during an incident.

**Recommendation:** While this is an administrative function, consider implementing a mechanism to process large batches in smaller, manageable chunks off-chain, or add a maximum array size check to prevent accidental gas limit overruns. Alternatively, ensure that the expected usage of this function will always involve a reasonable number of accounts.


### `L-01` — Unindexed Event Parameter in `UpdateFeeVault`  *(Severity: Low · Status: Unresolved)*

The `UpdateFeeVault` event, emitted by the `updateFeeVault` function, includes `new_fee_vault` and `old_fee_vault` parameters. However, neither of these parameters is indexed. Indexing critical event parameters allows for more efficient and faster filtering and retrieval of event data by off-chain applications, block explorers, and analytics tools. Without indexing, searching for specific fee vault changes requires scanning all events.

**Recommendation:** Index the `new_fee_vault` and `old_fee_vault` parameters in the `UpdateFeeVault` event to improve off-chain data querying efficiency. For example: `event UpdateFeeVault(address indexed new_fee_vault, address indexed old_fee_vault);`


### `L-02` — Redundant Modifier in `setCrossChainPaused`  *(Severity: Low · Status: Unresolved)*

The `setCrossChainPaused` function includes the `whenCrossChainNotPaused` modifier. This modifier checks `if (crossChainPaused) revert CrossChainOperationsPaused();`. However, the purpose of `setCrossChainPaused` is to *change* the `crossChainPaused` state. Applying `whenCrossChainNotPaused` to a function that intends to pause cross-chain operations creates a logical redundancy and prevents the function from being called if cross-chain operations are already paused, which might not be the intended behavior for an 'unpause' action.

**Recommendation:** Remove the `whenCrossChainNotPaused` modifier from the `setCrossChainPaused` function. The function should only be gated by `whenNotPaused` (for global pause) and `onlyRole(PAUSER_ROLE)` to allow the PAUSER_ROLE to toggle the `crossChainPaused` state freely.


### `I-01` — Redundant `Ownable` Inheritance in Constructor  *(Severity: Informational · Status: Unresolved)*

The `KgenOFT` contract inherits from both `Ownable2Step` and `Ownable`. In the constructor, `Ownable(_delegate)` is explicitly called. However, `Ownable2Step` itself inherits from `Ownable`, meaning the `Ownable` constructor is implicitly called when `Ownable2Step()` is invoked. Explicitly calling `Ownable(_delegate)` in the inheritance list is redundant and does not add new functionality or change behavior, but it can make the inheritance chain slightly less clear.

**Recommendation:** Remove the explicit `Ownable(_delegate)` call from the constructor's inheritance list. The `Ownable` constructor will be correctly called via the `Ownable2Step` inheritance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf3d5...3a1e`](https://bscscan.com/address/0xf3d5b4c34ed623478cc5141861776e6cf7ae3a1e) |
| **Network** | BNB Chain |
| **Price** | $0.1861 |
| **24h Volume** | $48.0K |
| **Liquidity** | $30.7K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 93.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 392 buys / 367 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x81965714e2a1ec25fb8bcb3de60a11fe6bca929a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kgen-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
