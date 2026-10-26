---
token: b-money
ticker: B-MONEY
network: bsc
risk_score: 23
status: low
date: 2026-08-31
---

# b-money (B-MONEY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/b-money-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and pool state management. The contract leverages OpenZeppelin's upgradeable standards, contributing to a robust architectural foundation. However, a critical reentrancy vulnerability exists in the tax liquidation process, potentially allowing users to bypass taxes during transfers. Additionally, significant centralization risk is present due to owner-controlled state transitions, and a denial-of-service vector could block all token transfers if the external tax processor reverts.

> **Final Recommendation:** Prioritize resolving the critical reentrancy vulnerability in `_liquidateTax` by strictly adhering to the Checks-Effects-Interactions pattern or implementing a reentrancy guard. Implement robust error handling for external calls to `ITaxProcessor.processTax` to prevent denial-of-service for token transfers. Consider decentralizing control over critical state transitions by moving towards a multi-signature wallet or a time-locked governance mechanism for the `onlyOwner` functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes OpenZeppelin's upgradeable ERC20 and Ownable patterns, providing a solid base for code security (7.2 Code Security) and architecture (7.1 Architecture). The use of `SafeERC20`… |
| **Governance / Economics** | 7/10 | Low | The contract's economic model (7.4 Economic) is centered around dynamic tax rates and state transitions (e.g., BondingCurve, TaxEnforcedAntiFarmer). The `onlyOwner` modifier protects critical… |
| **Upgrades** | 4/10 | Medium | The contract is designed as an upgradeable proxy using OpenZeppelin's `Initializable` pattern (7.7 Upgrades). The `initialize` function is correctly protected by the `initializer` modifier, and… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 61.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — Centralization Risk with Owner-Controlled State Transitions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Functions `startMigration` and `finalizeMigration` are protected by the `onlyOwner` modifier. These functions control critical state transitions of the token's economic model, including enabling and disabling tax enforcement and anti-farmer mechanisms. This grants a single address (the owner) significant power over the token's operational state, representing a single point of failure and a high degree of trust in the owner's benevolence and security practices.

**Recommendation:** Consider implementing a multi-signature wallet for ownership of the contract to distribute control and reduce the risk associated with a single private key compromise. For highly sensitive state transitions, consider adding a time-lock mechanism to allow the community or other stakeholders to react to proposed changes.


### `M-02` — Potential for Denial of Service in Transfers due to External Call Reverts  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_transfer` function calls `_liquidateTax` at its beginning. Inside `_liquidateTax`, an external call to `ITaxProcessor.processTax(taxAmount)` is made. If this external call reverts for any reason (e.g., the `taxProcessor` contract is paused, experiences an error, runs out of gas, or is malicious), the `_liquidateTax` function will revert, which in turn will cause the `_transfer` function to revert. This could effectively block all token transfers, leading to a denial of service for users.

**Recommendation:** Implement robust error handling for the external call to `ITaxProcessor.processTax`. Consider using a `try-catch` block to gracefully handle reverts from the external contract, allowing transfers to proceed even if tax processing fails. Alternatively, make the `_processTax` call an `onlyOwner` function or a function callable by anyone but with a mechanism to disable automatic liquidation if it consistently fails, preventing it from blocking all transfers.


### `M-03` — Reentrancy Vulnerability Leading to Tax Bypass  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function, called by `_transfer`, sets `poolState.notLiquidating` to `false` *before* making an external call to `ITaxProcessor.processTax`. If the `taxProcessor` contract is malicious or compromised, it can re-enter the `_transfer` function. During this re-entrant call, the `_liquidateTax` function will be called again. However, because `poolState.notLiquidating` is still `false` from the initial call, the tax processing logic within `_liquidateTax` will be skipped. More critically, the `_getTaxWithPoolState` function, which determines the tax amount for transfers, also checks `currentPoolState.notL

**Recommendation:** Implement the Checks-Effects-Interactions pattern strictly. Ensure all state changes related to `notLiquidating` are finalized *before* any external calls. A reentrancy guard on `_liquidateTax` or `_transfer` would also mitigate this. For example, set `notLiquidating` back to `true` immediately after the `_processTax` call, or use OpenZeppelin's `ReentrancyGuard`.


### `L-01` — Inefficient Loop in `initialize` for Pool Addresses  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function iterates through the `params.pools` array to set `pools[address] = true` for each address. While functional, if the `params.pools` array contains a very large number of addresses, this loop could lead to high gas costs during contract deployment or exceed block gas limits on certain networks, making initialization prohibitively expensive or impossible.

**Recommendation:** For scenarios involving a large number of pool addresses, consider implementing a separate `addPools` function that can be called multiple times by the owner after initialization, or a more gas-efficient batching mechanism that processes addresses in smaller chunks.


### `L-02` — Hardcoded `maxSupply` as a Constant  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `maxSupply` variable is declared as a `constant` with a value of `1e9 ether`. While this defines a clear maximum supply, its immutability means that the total supply can never be adjusted in the future without a full contract upgrade. This design choice removes flexibility for potential future economic adjustments, such as burning tokens to reduce supply or minting for specific purposes beyond the initial supply.

**Recommendation:** If future flexibility regarding total supply is desired, consider making `maxSupply` a `public` state variable that can be set by the owner during initialization or through a governance mechanism. Alternatively, if the token is intended to be fully elastic, remove the `maxSupply` constraint entirely.


### `I-01` — Reliance on `block.timestamp` for Time-Sensitive Logic  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses `block.timestamp` to calculate `taxExpirationTime` and `antiFarmerExpirationTime`. While commonly used, `block.timestamp` can be manipulated by miners within a certain range (e.g., up to 900 seconds on Ethereum, potentially more on other EVM chains) to slightly influence the timing of these events. For expiration times, the risk is generally low, but it's a known characteristic of `block.timestamp`.

**Recommendation:** Be aware of the potential for `block.timestamp` manipulation. For critical, short-duration events where precise timing is paramount, consider using `block.number` in conjunction with average block times, or external oracle solutions like Chainlink Keepers for more robust time-based execution. For expiration times, the current implementation is generally acceptable.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf497...7777`](https://bscscan.com/address/0xf49725118cb0707b8706ffffe895f3ab16da7777) |
| **Network** | BNB Chain |
| **Price** | $0.00339 |
| **24h Volume** | $1.15M |
| **Liquidity** | $216.2K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 8d |
| **Top-10 Holders** | 24.9% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 1318 buys / 1113 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xbae8327deb97de23940d877134cd16f1bed0f83d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/b-money-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
