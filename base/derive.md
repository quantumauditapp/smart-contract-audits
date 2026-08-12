---
token: Derive
ticker: DRV
network: base
risk_score: 40
status: medium
date: 2026-08-12
---

# Derive (DRV) — Smart Contract Security Analysis | Base

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/derive-base)

---

## Audit Summary

This audit covers the DeriveL2 token contract, deployed as an upgradeable ERC20 token on the Base network. The contract utilizes OpenZeppelin's upgradeable patterns, including `Initializable` and `OwnableUpgradeable`, and is managed via a TransparentUpgradeableProxy. Ownership is secured by a 3/5 multisig wallet. The implementation uses custom storage slot definitions, which requires careful management during upgrades. While the contract benefits from well-audited OpenZeppelin components, specific attention is drawn to the upgradeability mechanism's reliance on custom storage slot management and the centralized control inherent in the `Ownable` pattern.

> **Final Recommendation:** It is recommended to thoroughly test any future upgrades, paying particular attention to storage slot compatibility to prevent data corruption, especially given the custom storage slot definitions. Ensure that the multisig wallet responsible for ownership and upgrades is securely managed and follows robust operational security procedures. Regularly review the contract's access control mechanisms and any functions callable by the owner to confirm they align with the intended security posture.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract's architecture (7.1) is based on OpenZeppelin's upgradeable ERC20 standard, which is a robust and widely adopted framework. Code security (7.2) is generally strong due to the use of… |
| **Governance / Economics** | 4/10 | Medium | The economic model (7.4) is that of a standard ERC20 token. The contract's governance (7.5) benefits from a robust access control setup where the owner is a 3/5 multisig wallet, significantly… |
| **Upgrades** | 2/10 | High | The contract is upgradeable via a TransparentUpgradeableProxy (7.7), allowing for future enhancements and bug fixes. The implementation uses OpenZeppelin's `Initializable` pattern to manage… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | Other-Contract |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Custom Storage Slot Management in Upgradeable Contract  *(Severity: Medium · Status: Unresolved)*

The implementation contract utilizes custom `bytes32` constants for defining storage locations (e.g., `OwnableStorageLocation`, `INITIALIZABLE_STORAGE`, `ERC20StorageLocation`) for its state variables. While this is a valid pattern for upgradeable contracts, it deviates from OpenZeppelin's standard `ERC1967Storage` pattern for proxy-related storage. This approach requires meticulous manual management of storage layout across upgrades. If new state variables are introduced in future versions without careful planning and calculation of their storage slots, it could lead to storage collisions, overwriting existing data, and potentially causing contract malfunction or loss of funds.

**Recommendation:** Ensure a rigorous process for managing storage layout during upgrades. Document all storage slot assignments and verify them with tools like OpenZeppelin's `hardhat-upgrades` or `foundry-upgrades` plugin to detect potential storage collisions before deployment. Consider adopting a more standardized storage pattern like `ERC1967Storage` in future implementations if feasible, or clearly document the custom slot strategy.


### `L-01` — Centralized Control by Owner  *(Severity: Low · Status: Unresolved)*

The contract implements the `OwnableUpgradeable` pattern, granting significant administrative control to a single owner address. This owner has the ability to `transferOwnership` and potentially control other critical administrative functions within the `DeriveL2` contract (e.g., if there are mint/burn functions or other privileged operations not fully visible in the provided snippet). While the owner is a 3/5 multisig wallet, which mitigates some of the risk associated with a single external account, it still represents a centralized point of control over the contract's lifecycle and potentially its core functionality.

**Recommendation:** Maintain strict operational security for the multisig wallet controlling the contract. Ensure that the multisig signers are diverse, trusted, and follow robust key management practices. Consider implementing time-locks for critical administrative actions to provide a window for community review or emergency intervention, further decentralizing control and enhancing security.


### `I-01` — Internal Minting Capability  *(Severity: Informational · Status: Unresolved)*

The `_update` function, which is an internal helper for token transfers, contains logic to increase `_totalSupply` and `_balances` when the `from` address is `address(0)`. This indicates that the contract has an internal capability to mint new tokens. While the prefill data states `has_mint: false` (implying no public `mint` function is exposed), any internal or restricted function that calls `_update` with `from = address(0)` could effectively mint tokens. The extent of this capability depends on other parts of the contract not provided in the snippet.

**Recommendation:** Ensure that any functions capable of triggering this internal minting mechanism are strictly permissioned and only callable by authorized entities (e.g., the owner). Clearly document the existence and control mechanisms of this internal minting capability to provide transparency and aid future audits or development.


### `I-02` — Use of `unchecked` block  *(Severity: Informational · Status: Unresolved)*

The `_update` function includes an `unchecked` block for the subtraction `$._balances[from] = fromBalance - value;`. This is generally safe in this specific context because the line `if (fromBalance < value) { revert ERC20InsufficientBalance(from, fromBalance, value); }` explicitly checks for underflow immediately before the `unchecked` block, guaranteeing that `fromBalance` is always greater than or equal to `value` at that point.

**Recommendation:** While safe, for enhanced code clarity and maintainability, it is a good practice to add a comment explaining the safety assumption for `unchecked` blocks. This helps future auditors or developers quickly understand why the `unchecked` block is used and confirms that the potential for underflow has been explicitly addressed.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9d0e...d083`](https://basescan.org/address/0x9d0e8f5b25384c7310cb8c6ae32c8fbeb645d083) |
| **Network** | Base |
| **Price** | $0.1015 |
| **24h Volume** | $49.7K |
| **Liquidity** | $471.2K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 58.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 76 buys / 62 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe2654cc01616e962fbfcc4277c23062e59e70e39f87221d77b6d438705a5f286)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/derive-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
