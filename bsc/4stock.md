---
token: 4Stock
ticker: 4STOCK
network: bsc
risk_score: 1
status: low
date: 2026-09-12
---

# 4Stock (4STOCK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/4stock-bsc)

---

## Audit Summary

This audit covers the Stock4TaxToken contract, an ERC-20 token implementation behind a proxy on the BSC network. The contract features a complex fee mechanism for buy/sell operations, distributing fees to founders, holders, burn addresses, and liquidity pools. It utilizes OpenZeppelin libraries for secure ERC-20 operations and includes reentrancy guards for fee dispatching. Key findings highlight centralized control over critical parameters and external dependencies, potential for fee accumulation, and reliance on an external `ITokenHelper` for core operations. The upgradeability pattern appears standard and secure.

> **Final Recommendation:** To enhance the security and resilience of the Stock4TaxToken protocol, it is strongly recommended to decentralize control over critical parameters and external contract configurations where feasible, potentially through multi-signature governance or time-locked operations. A comprehensive audit of all external dependencies, especially `ITokenHelper`, is crucial to mitigate risks associated with third-party contracts. Furthermore, ensure that all critical state changes and parameter modifications are accompanied by explicit event emissions for improved transparency and off-chain monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract demonstrates good technical practices, including the use of OpenZeppelin's SafeERC20 for secure token transfers and explicit reentrancy guards (`swapping`, `dispatchingFee`) for… |
| **Governance / Economics** | 8/10 | Low | The token's economic model involves a detailed fee distribution mechanism, including founder, holder, burn, and liquidity rates, which are set during initialization (7.4 Economic). However, the… |
| **Upgrades** | 9/10 | Low | The contract is designed as an upgradeable proxy implementation, using the `initializer` modifier for one-time setup, which is a standard and secure pattern for UUPS proxies (7.7 Upgrades). The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 16.1% |
| **Top-3 Unlocked** | 36.2% |

## Security Findings

_🟡 3 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `M-01` — Potential for Fee Accumulation and Stagnation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `dispatchTax` function is responsible for distributing accumulated fees to various destinations (founder, holders, burn, liquidity). However, its execution is gated by several conditions, including `tokenAccumulated > minDispatch`, `feeAccumulated > minDispatchQuote`, and the availability of `tokenHelper`. If `minDispatch` or `minDispatchQuote` are set too high, or if `tokenHelper` is not properly configured or becomes unavailable, fees could accumulate indefinitely without being distributed. This could lead to a lack of rewards for holders and an inability to fund other protocol functions (7.4 Economic).

**Recommendation:** Review and carefully set `minDispatch` and `minDispatchQuote` to ensure they are economically viable for frequent dispatching. Implement a mechanism for the `tokenModule` to manually trigger dispatching or adjust these minimums if automatic dispatching stalls. Consider adding a fallback mechanism for fee distribution if `tokenHelper` becomes unresponsive.


### `M-02` — Heavy Reliance on External `ITokenHelper` for Core Operations  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Stock4TaxToken` contract delegates crucial functionalities related to liquidity management and token swaps (e.g., `addLiquidity`, `swapForQuote`, `swapForToken`, `swapForETH`) to an external `ITokenHelper` contract. The address of this `tokenHelper` is configurable by the `tokenModule`. A compromise or malicious behavior of the `ITokenHelper` contract could directly impact the token's economic stability, potentially leading to fund loss, price manipulation, or disruption of the fee distribution mechanism. The security of `Stock4TaxToken` is thus highly dependent on the security and trustworthiness of `ITokenHelper

**Recommendation:** Conduct a thorough audit of the `ITokenHelper` contract. Ensure that the `tokenHelper` address is set to a verified, immutable, and audited contract. Implement robust monitoring for the `tokenHelper` contract's behavior. Consider adding circuit breakers or emergency pause mechanisms if the `tokenHelper` exhibits suspicious activity.


### `M-03` — Centralized Control over Critical Parameters and External Contracts  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `tokenModule` (likely an admin role) possesses significant control over the contract's operation. It can configure critical external dependencies such as `wrappedNative`, `quote`, `shareHolderManager`, `tokenHelper`, and `lpV2Manager` via the `postInitialize` function. Additionally, the `shareHolderManager` contract, once set, has the power to blacklist users, preventing them from transferring tokens. This level of centralized control introduces a single point of failure and a high trust assumption on the `tokenModule` and `shareHolderManager` addresses (7.3 Access Control, 7.6 External).

**Recommendation:** Implement a multi-signature wallet for the `tokenModule` address and any other privileged roles. Consider time-locks for critical parameter changes to allow users to react to impending modifications. Clearly document the roles and responsibilities of each privileged address.


### `L-01` — Incomplete Event Emission for Critical Parameter Changes  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function sets several critical economic parameters such as `buyFeeRate`, `sellFeeRate`, `rateFounder`, `rateHolder`, `rateBurn`, `rateLiquidity`, `minDispatch`, `minDispatchQuote`, and `minShare`. While `LPV2ManagerConfigured` is emitted in `postInitialize`, there are no corresponding events emitted when these core economic parameters are initially set or if they were to be changed in a future upgrade. This lack of event emission hinders off-chain monitoring, transparency, and the ability for users and external systems to track the token's economic model effectively (7.8 Operations).

**Recommendation:** Emit explicit events for all critical parameters set during `initialize` and `postInitialize`. If any of these parameters are made mutable in future upgrades, ensure that corresponding events are emitted upon each modification.


### `L-02` — Default `founder` to `creator` in `_decodeOrDefault`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_decodeOrDefault` function, used during initialization, sets the `founder` address to the `creator` (which is `msg.sender` of the `initialize` call, typically the `tokenModule` or deployer) if `p.founder` is `address(0)` in the provided `TaxTokenParams`. While this might be intended, it means the `tokenModule` automatically becomes a recipient of a portion of the fees if a specific founder is not explicitly set. This could lead to an unintended distribution of funds if the `tokenModule` is not the intended long-term founder or if the `creator` address is a temporary deployment wallet (7.2 Code Security).

**Recommendation:** Explicitly require `p.founder` to be a non-zero address in `TaxTokenParams` to prevent accidental assignment to the `creator`. Alternatively, clearly document this default behavior and ensure the `creator` address is appropriately managed if it's intended to receive founder fees.


### `I-01` — Redundant `quote` parameter in `postInitialize`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `quote` state variable is initialized in the `initialize` function using `c.quoteAsset`. Subsequently, the `postInitialize` function also takes an `address quote_` parameter and assigns it to the `quote` state variable, effectively overwriting the value set during the main initialization. While this might be intentional to allow for a two-step configuration, it introduces redundancy and could be a source of confusion or potential misconfiguration if the two values are intended to be different or if the `quote_` parameter in `postInitialize` is accidentally set incorrectly (7.2 Code Security).

**Recommendation:** Clarify the intended purpose of setting `quote` in both `initialize` and `postInitialize`. If `postInitialize` is meant to finalize this value, ensure clear documentation. If it's truly redundant, remove the `quote_` parameter from `postInitialize` and rely solely on the value set in `initialize`.


### `I-02` — Potential Reentrancy in `_transfer` (Truncated Code)  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided `_transfer` function snippet is truncated, preventing a full security analysis. However, in fee-on-transfer tokens, `_transfer` often involves complex logic, including calculating and distributing fees, which may entail external calls (e.g., to swap fees, add liquidity). If these external calls are made before critical state updates or without robust reentrancy guards, the contract could be vulnerable to reentrancy attacks. While `swapping` and `dispatchingFee` flags are present elsewhere, their application and effectiveness within the full `_transfer` logic cannot be confirmed (7.2 Code Security).

**Recommendation:** A complete review of the `_transfer` function and any related fee-handling logic is crucial. Ensure strict adherence to the Checks-Effects-Interactions pattern. All state changes must be finalized before any external calls are made. Confirm that all functions involving external calls or sensitive state modifications are protected by appropriate reentrancy guards, such as `swapping` or `dispatchingFee`, and that these guards are correctly implemented and scoped.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd270...ffff`](https://bscscan.com/address/0xd270d4e1ec6e6e0d28c0ecb8be966ec75997ffff) |
| **Network** | BNB Chain |
| **Price** | $0.0318 |
| **24h Volume** | $2.88M |
| **Liquidity** | $840.8K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 4d |
| **Top-10 Holders** | 47.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2560 buys / 1845 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x90c3c770087eb9e63ad47e99a66e260aa10c31ae)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/4stock-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
