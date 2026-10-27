---
token: 孙小圣
ticker: 孙小圣
network: bsc
risk_score: 36
status: medium
date: 2026-09-03
---

# 孙小圣 (孙小圣) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-e50217-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a complex, multi-state tax mechanism. The contract utilizes OpenZeppelin's upgradeable standards and `SafeERC20` for secure token interactions. A significant portion of the core tax liquidation logic in `_liquidateTax` was truncated in the provided source, preventing a full security assessment of this critical component. Identified issues include centralization risks, potential time-based manipulation, and minor economic inflexibilities.

> **Final Recommendation:** A complete and verified source code for the `_liquidateTax` function is essential for a thorough security assessment. Without it, critical vulnerabilities related to reentrancy, external calls, and complex state transitions cannot be fully evaluated. It is recommended to reduce owner privileges where possible or implement a multi-signature wallet for critical administrative functions to mitigate centralization risks. Consider making `liqExpectedOutputAmount` configurable by governance to adapt to changing market conditions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's upgradeable ERC20, Ownable, and Permit standards, ensuring a robust foundation (7.1 Architecture, 7.2 Code Security). The use of `SafeERC20` for external token… |
| **Governance / Economics** | 6/10 | Medium | The contract defines immutable liquidation thresholds and a constant `maxSupply`, contributing to economic stability (7.4 Economic). The `initialize` function includes important sanity checks for… |
| **Upgrades** | 4/10 | Medium | The contract is built on OpenZeppelin's upgradeable patterns, correctly using `Initializable` and `_disableInitializers()` in the constructor, which is a strong practice for upgrade safety (7.7… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — Centralization Risk with Owner Privileges  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `startMigration` and `finalizeMigration` functions, which control critical `PoolState` transitions, are restricted to `onlyOwner`. This grants significant power to a single address. A compromised owner key or a malicious owner could lead to unauthorized and disruptive state changes, potentially impacting the token's economic model and user trust (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the owner address to require multiple approvals for critical operations. Alternatively, explore a time-locked governance mechanism for highly sensitive state changes to provide a window for community review and reaction.


### `M-02` — Time-Based State Transitions and Potential for Manipulation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function triggers `PoolState` changes (e.g., to `TaxFree` or `TaxEnforced`) based on `block.timestamp` exceeding `taxExpirationTime` or `antiFarmerExpirationTime`. While `block.timestamp` is generally reliable, miners have a limited ability to manipulate it within a certain range (up to 900 seconds deviation from median). This could allow for minor manipulation of when state transitions occur, potentially impacting users who are sensitive to tax rate changes (7.2 Code Security).

**Recommendation:** While this is a common pattern, be aware of the inherent limitations of `block.timestamp`. For highly critical, time-sensitive events, consider using a decentralized oracle for time if precise, unmanipulable timing is paramount, or implement a grace period around state transitions.


### `M-03` — Truncated `_liquidateTax` Function Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `_liquidateTax` function is incomplete. This function contains critical logic for state transitions, tax processing, and potentially external calls to `ITaxProcessor`. Without the full code, a comprehensive security assessment of this core mechanism, including potential reentrancy vulnerabilities, gas consumption, and correct handling of tax funds, is impossible.

**Recommendation:** Provide the complete and verified source code for the `_liquidateTax` function to allow for a full security audit. Pay particular attention to external calls within this function and implement reentrancy guards if necessary.


### `L-01` — Fixed `liqExpectedOutputAmount`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `liqExpectedOutputAmount` is set only once during initialization and is immutable thereafter. In a dynamic market, a fixed expected output amount for tax liquidation might become suboptimal or even detrimental over time, potentially leading to inefficient tax processing or missed opportunities for the protocol (7.4 Economic).

**Recommendation:** Consider making `liqExpectedOutputAmount` a configurable parameter, allowing the owner or a governance mechanism to update it as market conditions evolve. This would provide greater flexibility and optimize the tax processing mechanism.


### `L-02` — `uint48` and `uint64` for Expiration Times  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `antiFarmerExpirationTime` is stored as `uint48` and `taxExpirationTime` as `uint64`. While `block.timestamp` is currently well within these limits, using smaller types for time-related variables that store `block.timestamp` values introduces a theoretical, albeit distant, risk of overflow/truncation in the very long term (e.g., `uint48` overflows in ~8900 years, `uint64` in ~580 billion years). It's generally safer to use `uint256` for `block.timestamp` values unless gas savings are critical and the lifespan of the contract is well-understood (7.2 Code Security).

**Recommendation:** For maximum future-proofing, consider using `uint256` for time-related variables that store `block.timestamp` values. If gas optimization is a primary concern, ensure the expected lifespan of the contract is well within the limits of `uint48` and `uint64`.


### `I-01` — `_liquidateTax` Called on Every Transfer  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is called on every `_transfer` operation. While this ensures timely state updates and tax processing, if the logic within `_liquidateTax` becomes complex or involves multiple external calls (as hinted by the truncation), it could lead to increased gas costs for every token transfer, potentially impacting user experience or transaction throughput (7.8 Operations).

**Recommendation:** Monitor the gas consumption of `_liquidateTax` once the full implementation is available. Optimize its logic to minimize gas costs, especially if it involves external calls. Consider if there are scenarios where liquidation can be batched or triggered less frequently without compromising the protocol's economic model.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0185...7777`](https://bscscan.com/address/0x01856bda968ddca3ae5f866a4e07405480967777) |
| **Network** | BNB Chain |
| **Price** | $0.0006888 |
| **24h Volume** | $463.3K |
| **Liquidity** | $108.7K |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 5d |
| **Top-10 Holders** | 30.3% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 3061 buys / 2154 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x554daf8c85d6e63dfa2815fc1ceb74f3bd792f69)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-e50217-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
