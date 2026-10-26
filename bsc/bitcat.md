---
token: Bitcat
ticker: BITCAT
network: bsc
risk_score: 7
status: low
date: 2026-09-12
---

# Bitcat (BITCAT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bitcat-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and a multi-state pool system. While leveraging OpenZeppelin's secure patterns for upgradeability and token operations, a critical portion of the `_liquidateTax` function is truncated in the provided source, preventing a complete security assessment. This missing code introduces significant uncertainty regarding potential vulnerabilities and operational risks.

> **Final Recommendation:** It is imperative to obtain the complete and verified source code for the `_liquidateTax` function to conduct a thorough security assessment. Without this, the contract's overall security posture cannot be fully determined. Additionally, consider implementing multi-signature control for critical owner-only functions to mitigate centralized governance risks and review the gas implications of `_liquidateTax` being called on every transfer to the main pool.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages OpenZeppelin's upgradeable patterns and `SafeERC20` for secure token interactions, demonstrating a solid foundation for code security (7.2). The `PackedPoolState` struct… |
| **Governance / Economics** | 6/10 | Medium | The contract defines immutable liquidation thresholds and uses a clear tax calculation mechanism, contributing to predictable economic behavior (7.4). However, the `OwnableUpgradeable` pattern grants… |
| **Upgrades** | 9/10 | Low | The contract correctly implements OpenZeppelin's `Initializable` pattern, including `_disableInitializers()` in the constructor and the `initializer` modifier, which mitigates re-initialization risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Potential Gas Cost and Unexpected Behavior from `_liquidateTax` Invocation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is called internally within `_transfer` whenever a transfer is made to the `mainPool`. Given that the full logic of `_liquidateTax` is unknown due to truncation, there's a risk that this function could perform complex operations, external calls, or significant state changes. This could lead to unexpectedly high gas costs for users transferring to the `mainPool` or introduce reentrancy vectors if external calls are made without proper reentrancy guards (7.2, 7.8).

**Recommendation:** Once the full `_liquidateTax` code is available, thoroughly review its complexity and gas implications. If it performs heavy operations, consider optimizing it or decoupling its execution from every transfer. Implement reentrancy guards (e.g., ReentrancyGuard) if external calls are made to untrusted contracts.


### `M-02` — Critical Code Truncation in `_liquidateTax` Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `_liquidateTax` function is truncated, specifically after the line `\|\| taxAmount >= currentPoolState.liqu...`. This prevents a complete audit of the function's logic, including its full conditions for liquidation, potential external calls, and state modifications. Any unreviewed code could contain critical vulnerabilities such as reentrancy, access control bypasses, or economic exploits (7.2, 7.6, 7.8).

**Recommendation:** Provide the complete and verified source code for the `_liquidateTax` function. A full security review of this critical component is essential to ensure the contract's integrity and security.


### `M-03` — Centralized Control Over Critical State Transitions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `startMigration` and `finalizeMigration` functions, which control significant state changes in the token's lifecycle, are protected only by the `onlyOwner` modifier. This grants a single address (the contract owner) unilateral control over these critical transitions. A compromise of the owner's private key could lead to unauthorized state changes, potentially disrupting token functionality or economic model (7.3, 7.5).

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance mechanism for critical owner-only functions like `startMigration` and `finalizeMigration`. This would introduce a delay or require multiple approvals, reducing the risk associated with a single point of failure.


### `L-01` — Long-Term `uint48` Truncation Risk for `antiFarmerExpirationTime`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `antiFarmerExpirationTime` variable is stored as `uint48`. While `block.timestamp` currently fits within `uint48` (representing approximately 270,000 years), in the extremely long term (hundreds of thousands of years), `block.timestamp` could exceed the maximum value of `uint48`. This could lead to truncation or unexpected behavior if the contract is intended to operate over such extended periods (7.2).

**Recommendation:** For time-related variables that store `block.timestamp` or future timestamps, it is generally safer to use `uint256` to avoid any potential long-term truncation issues, even if the immediate risk is negligible. Alternatively, ensure that `antiFarmerDuration` is always small enough such that `block.timestamp + antiFarmerDuration` will not exceed `uint48` max.


### `I-01` — Initial Token Distribution to Initializer  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). During the `initialize` function, the entire `maxSupply` (1 billion tokens) is minted to `msg.sender`. This means the address that calls `initialize` will hold the entire initial supply of tokens. While a common pattern for new tokens, it centralizes the initial distribution (7.4).

**Recommendation:** Ensure that the address used to call `initialize` is a secure, controlled entity (e.g., a multi-signature wallet or a cold wallet) and that the project's token distribution strategy is clearly communicated to the community.


### `I-02` — Unused Public State Variables  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Several public state variables (`v2Router`, `liqExpectedOutputAmount`, `metaURI`, `dividendContract`, `initialLiquidationThreshold`) are declared and initialized but not explicitly used within the provided (non-truncated) functions of the `FlapTaxTokenV3` contract. While they might be used in the truncated `_liquidateTax` function or external interfaces, their current apparent lack of use could indicate dead code or incomplete functionality (7.1).

**Recommendation:** Review the contract's design to confirm if these variables are intended for future use, external interactions (e.g., by `taxProcessor` or `dividendContract`), or if they are indeed unused. If unused, consider removing them to reduce contract complexity and deployment costs. If they are used in the truncated code, this will become clear upon full code review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7d1a...7777`](https://bscscan.com/address/0x7d1a8dbb40b7b5518ef69b93a6faeba91eea7777) |
| **Network** | BNB Chain |
| **Price** | $0.0003995 |
| **24h Volume** | $234.3K |
| **Liquidity** | $77.0K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 3d |
| **Top-10 Holders** | 26.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1494 buys / 1098 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xd09e60fb451cdc6e1fcd0e1dee6db553e89dafa9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bitcat-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
