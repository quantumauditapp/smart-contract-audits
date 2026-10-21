---
token: Momentum
ticker: MNTM
network: bsc
risk_score: 8
status: low
date: 2026-09-04
---

# Momentum (MNTM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/momentum-bsc)

---

## Audit Summary

The MomentumToken contract implements an ERC20 token with custom tax mechanics, a vesting system, and integrations with PancakeSwap for liquidity management and price discovery. The contract utilizes OpenZeppelin libraries and includes a reentrancy guard. Key findings include a reliance on spot prices from PancakeSwap V2, which is susceptible to manipulation, and the absence of the `nonReentrant` modifier on critical functions involving external calls. Additionally, the `executeBondLiquidity` function exhibits inefficient token transfer logic. The audit was conducted on partial source code, specifically the vesting-related functions were truncated, limiting a full assessment of that module.

> **Final Recommendation:** Prioritize addressing the oracle manipulation vulnerability by implementing a robust price oracle solution, such as a Time-Weighted Average Price (TWAP) or a decentralized oracle network, for any critical operations relying on token prices. Ensure all functions performing external calls and modifying state are protected with the `nonReentrant` modifier. Review and optimize the `executeBondLiquidity` function's token transfer logic to enhance efficiency and reduce potential attack surface. Consider the implications of centralized control and implement multi-signature wallets for privileged roles to enhance security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract leverages OpenZeppelin's ERC20 and ReentrancyGuard for foundational security, and employs custom error types for clarity (7.2 Code Security). However, the reliance on PancakeSwap V2's… |
| **Governance / Economics** | 8/10 | Low | The protocol's economic model includes a 5% sell tax on transfers to the PancakeSwap pair, directed to a `taxWallet`, which is a common tokenomic feature (7.4 Economic). Centralized control is… |
| **Upgrades** | 10/10 | Low | The MomentumToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This means its core logic is immutable once deployed, eliminating risks associated with upgrade mechanisms but also… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Oracle Manipulation Risk from Spot Price  *(Severity: High · Status: Unresolved)*

The `livePrice()` and `calcAvgExecPrice()` functions directly query the spot reserves from the PancakeSwap V2 pair (`IPancakePair(pancakePair).getReserves()`). Spot prices from AMMs are highly susceptible to manipulation via flash loans or large trades within a single block. An attacker could temporarily inflate or deflate the MNTM price to exploit functions that rely on these price feeds, potentially leading to incorrect calculations for `executeBondLiquidity` or other price-sensitive operations (7.4 Economic).

**Recommendation:** Implement a more robust and decentralized price oracle solution. Consider using a Time-Weighted Average Price (TWAP) oracle from PancakeSwap V2 (if available and suitable for the required time window) or integrate with a decentralized oracle network like Chainlink. Ensure that any critical logic relying on token prices is resilient to short-term price fluctuations and manipulations.


### `M-01` — Missing `nonReentrant` Modifier on Critical Functions  *(Severity: Medium · Status: Unresolved)*

While the contract inherits `ReentrancyGuard`, the `nonReentrant` modifier is not explicitly applied to the `executeBondLiquidity` function. This function performs multiple external calls to the PancakeRouter (`swapExactTokensForTokens`, `addLiquidity`) and transfers tokens (`safeTransferFrom`). Without the `nonReentrant` guard, a malicious contract could potentially re-enter the function during an external call, leading to unexpected state changes or double-spending (7.2 Code Security). Furthermore, if the truncated `claimVesting` function involves external token transfers, it would also be a critical candidate for this modifier.

**Recommendation:** Apply the `nonReentrant` modifier to `executeBondLiquidity` and any other functions that perform external calls to untrusted contracts and modify the contract's state, especially those involving token transfers or value calculations. For example: `function executeBondLiquidity(...) external nonReentrant { ... }`.


### `M-02` — Inefficient and Complex `executeBondLiquidity` Logic  *(Severity: Medium · Status: Unresolved)*

The `executeBondLiquidity` function's logic for swapping USDT to MNTM is inefficient. It first swaps USDT for MNTM, sending the MNTM to the `logicContract`, and then immediately transfers that MNTM from `logicContract` back to the `MomentumToken` contract using `safeTransferFrom`. This adds an unnecessary intermediate transfer, increases gas costs, and requires the `logicContract` to have approved the `MomentumToken` contract to spend its MNTM, introducing an additional point of failure (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Optimize the `executeBondLiquidity` function by having the PancakeRouter swap USDT directly to the `MomentumToken` contract's address instead of the `logicContract`. This eliminates the need for the intermediate `safeTransferFrom` and the associated approval, reducing complexity, gas costs, and potential failure points.


### `L-01` — Insufficient Slippage Protection in `executeBondLiquidity`  *(Severity: Low · Status: Unresolved)*

In the `executeBondLiquidity` function, the `swapExactTokensForTokens` call uses `minMNTMOut = 1`. This value provides extremely minimal slippage protection. If market conditions change unfavorably or if the transaction is front-run, a significant portion of the `half` USDT could be exchanged for a much smaller amount of MNTM than expected, leading to value loss for the protocol (7.4 Economic).

**Recommendation:** Implement a more robust slippage control mechanism. The `logicContract` (or the caller of `executeBondLiquidity`) should calculate and provide a reasonable `minMNTMOut` based on current market conditions and an acceptable slippage tolerance, rather than a fixed low value like `1`. This would protect against unfavorable trade execution.


### `I-01` — Centralization Risk with Privileged Roles  *(Severity: Informational · Status: Unresolved)*

The `owner` role holds significant control over critical contract parameters, including setting the `logicContract`, `pancakePair`, `taxWallet`, `projectWallet`, and managing `taxExempt` addresses. The `logicContract` itself possesses powerful capabilities, such as minting new tokens and executing bond liquidity. While common for initial deployments, this centralization introduces a single point of failure; compromise of either the `owner` or `logicContract` address could lead to severe consequences for the protocol. If ownership has been renounced (as indicated by external data), the `logicContract` becomes the primary point of centralized control for ongoing operations, making its securit…

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the `owner` and `logicContract` roles to distribute control and reduce the risk associated with a single compromised private key. For parameters that are intended to be immutable after initialization, ensure they can only be set once or are hardcoded.


### `I-02` — Hardcoded `launchTime`  *(Severity: Informational · Status: Unresolved)*

The `launchTime` is a hardcoded constant set in the constructor. While this ensures immutability, it removes any flexibility to adjust the launch schedule. In the event of unforeseen delays, market volatility, or critical issues discovered pre-launch, the contract's tax and trading restrictions tied to `launchTime` cannot be modified without redeployment (7.8 Operations).

**Recommendation:** For future deployments or similar contracts, consider making critical timestamps like `launchTime` configurable by the owner within a specific window, or through a governance mechanism, to allow for greater operational flexibility in response to real-world events. If immutability is the desired design, ensure thorough pre-launch testing and planning.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x05ae...b455`](https://bscscan.com/address/0x05ae9ac4878f18d9ae11f804079cfffd0844b455) |
| **Network** | BNB Chain |
| **Price** | $2.0420 |
| **24h Volume** | $613.1K |
| **Liquidity** | $911.8K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 15d |
| **Top-10 Holders** | 96.0% of supply |
| **Buy / Sell Tax** | 0.0% / 5.0% |
| **24h Transactions** | 781 buys / 387 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6a8f760e1bb2a17806940cc0c08c81b117d61ae0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/momentum-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
