---
token: PunkStrategy
ticker: PNKSTR
network: ethereum
risk_score: 92
status: critical
date: 2026-09-02
---

# PunkStrategy (PNKSTR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 92/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/punkstrategy-eth)

---

## Audit Summary

The PunkStrategy contract is designed to manage CryptoPunks on Uniswap V4, acting as an ERC20 token and a strategy for buying, re-listing, and burning its own tokens. The contract leverages established Solady libraries and interacts with well-known protocols like Uniswap V4 and CryptoPunks. However, the audit identified a critical centralization risk where the owner can drain all contract funds. High-severity issues include potential reentrancy patterns due to state updates after external calls and significant trust placed in the configurable Uniswap V4 hook address. Medium-severity concerns involve the lack of slippage protection in token swaps and liquidity provision, exposing the contract to MEV and unfavorable trade execution.

> **Final Recommendation:** Prioritize addressing the critical centralization risk by implementing a multi-signature wallet for the owner role or removing the `transferEther` function if not strictly necessary for protocol operation. Re-evaluate the sequence of state updates in `buyPunkAndRelist` to ensure all state changes occur before external calls, even with reentrancy guards in place. Implement robust slippage control for all Uniswap V4 swap operations to protect against MEV and ensure favorable trade execution. Carefully vet and secure the Uniswap V4 hook contract, considering its significant privileges and callback capabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes robust Solady libraries for secure operations (7.2 Code Security) and implements reentrancy guards for critical functions (7.2 Code Security). It interacts with established… |
| **Governance / Economics** | 1/10 | High | The contract's economic model involves accumulating fees, buying CryptoPunks, re-listing them, and burning its own ERC20 tokens. The owner has extensive control over critical parameters and funds… |
| **Upgrades** | 4/10 | Medium | The PunkStrategy contract is not designed with an upgradeability pattern (7.7 Upgrades). It is deployed as a standard, non-upgradeable contract. This means that once deployed, its logic cannot be… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 2 Low_

### `C-01` — Centralized Control and Fund Drain Risk  *(Severity: Critical · Status: Unresolved)*

The `transferEther(address _to, uint256 _amount)` function, callable only by the contract owner, allows the owner to transfer any amount of ETH from the contract's balance to an arbitrary address. This capability presents a critical centralization risk, as a malicious or compromised owner could drain all funds held by the contract, including accumulated fees and liquidity, leading to a complete loss of user assets and protocol insolvency (7.3 Access Control, 7.4 Economic).

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the owner role to require multiple approvals for critical operations like `transferEther`. Alternatively, remove the `transferEther` function if direct owner-initiated ETH transfers are not an essential part of the protocol's intended operation. If necessary, restrict its use to specific, auditable scenarios with clear purpose.


### `H-01` — Reentrancy Pattern in `buyPunkAndRelist` (State Update After External Calls)  *(Severity: High · Status: Unresolved)*

The `buyPunkAndRelist` function performs multiple external calls to `punksContract.buyPunk`, `punksContract.offerPunkForSale`, and `SafeTransferLib.forceSafeTransferETH(msg.sender, reward)` before updating the critical state variable `currentFees` (`currentFees -= totalRequired;`). While the function is protected by `nonReentrant` and `SafeTransferLib` mitigates direct reentrancy from `msg.sender`, the pattern of updating state after multiple external calls is inherently risky. If any of the external calls were to have an unexpected reentrant behavior or if a subsequent call (e.g., to `hookAddress` in another function) could be triggered before `currentFees` is updated, it could lead to an…

**Recommendation:** Adhere to the Checks-Effects-Interactions pattern. Update all relevant state variables (`currentFees`) *before* making any external calls. This ensures that the contract's state is consistent even if an external call re-enters or reverts unexpectedly. For example, decrement `currentFees` immediately after the `if (currentFees < totalRequired)` check and before calling `punksContract.buyPunk`.


### `H-02` — Uniswap V4 Hook Trust and Potential Exploits  *(Severity: High · Status: Unresolved)*

The `hookAddress` is set by the owner in `loadLiquidity` and is integrated into the Uniswap V4 `PoolKey`. This means the `hookAddress` will receive callbacks from Uniswap V4 during various pool operations (e.g., swaps, liquidity changes). A malicious or buggy hook contract could exploit these callbacks to manipulate the pool state, cause reentrancy issues, or perform sandwich attacks/MEV. Additionally, the `hookAddress` can call `addFees()`, allowing it to deposit ETH into the contract. This introduces a significant trust assumption on the `hookAddress` and its implementation, posing a risk to the strategy's integrity and funds (7.6 External, 7.4 Economic).

**Recommendation:** Thoroughly audit and secure the `hookAddress` contract. Implement strict access controls and validation within the hook contract to prevent malicious actions. Consider making the `hookAddress` immutable after initialization or subject to a robust governance process for changes. Ensure the hook contract's logic is minimal and only performs necessary operations to reduce the attack surface.


### `M-01` — Price Manipulation/Sandwich Attack Risk in `_buyAndBurnTokens`  *(Severity: Medium · Status: Unresolved)*

The `_buyAndBurnTokens` function executes a `swapExactTokensForTokens` on Uniswap V4 to swap ETH for PNKSTR tokens. The `amountOutMinimum` parameter for this swap is implicitly set to `0` (or not specified with a minimum), meaning there is no slippage protection. This vulnerability allows an attacker to front-run the transaction by artificially increasing the PNKSTR price, letting the contract buy at an inflated price, and then back-run to profit from the price difference. This 'sandwich attack' would result in the contract receiving fewer PNKSTR tokens for the same ETH amount, reducing the effectiveness of the token burn (7.2 Code Security, 7.4 Economic).

**Recommendation:** Implement a reasonable `amountOutMinimum` parameter for the `swapExactTokensForTokens` call in `_buyAndBurnTokens`. This minimum should be calculated based on the expected amount of PNKSTR tokens to be received, allowing for a small, acceptable slippage tolerance. This will protect the contract from significant losses due to price manipulation.


### `M-02` — Lack of Slippage Control in `_loadLiquidity` Initialization  *(Severity: Medium · Status: Unresolved)*

The `_loadLiquidity` function initializes a Uniswap V4 pool with fixed `liquidity` and `startingPrice`. While `amount0Max` and `amount1Max` are used, the `multicall` for `modifyLiquidities` does not include a transaction-level deadline. If the transaction to initialize liquidity is delayed or front-run, the actual price at execution might deviate significantly from the `startingPrice`, leading to an unfavorable liquidity provision ratio or potential loss of funds if the `amountMax` values are insufficient for the desired `liquidity` at the current market price (7.2 Code Security, 7.4 Economic).

**Recommendation:** Consider adding a `deadline` parameter to the `posm.multicall` function itself, or ensure that the `block.timestamp + 60` deadline within `modifyLiquidities` is sufficient and that the `startingPrice` is carefully chosen to reflect current market conditions at the time of deployment. For production systems, dynamic price fetching and slippage control are crucial for liquidity provision.


### `L-01` — Fixed `reward` and `priceMultiplier` Parameters  *(Severity: Low · Status: Unresolved)*

The `reward` (0.01 ETH) and `priceMultiplier` (2000) parameters are fixed values set in the constructor and can only be updated by the owner. While owner control allows for adjustments, these fixed values might not remain optimal under varying market conditions. A static `reward` could become disproportionately high or low relative to gas costs or Punk values, and a fixed `priceMultiplier` might lead to Punks being listed at uncompetitive prices (too high to sell, or too low missing profit), impacting the strategy's efficiency and profitability over time (7.4 Economic).

**Recommendation:** Consider implementing a more dynamic mechanism for adjusting `reward` and `priceMultiplier`, perhaps based on market conditions, governance proposals, or a time-weighted average. If owner control is maintained, ensure a robust process for parameter updates, potentially involving a time-lock or multi-signature approval to prevent hasty or malicious changes.


### `L-02` — `loadingLiquidity` State Variable Redundancy  *(Severity: Low · Status: Unresolved)*

The `loadingLiquidity` boolean state variable is set to `true` at the beginning of the `_loadLiquidity` function and `false` at its conclusion. This variable is only used within this internal function and is not checked anywhere else in the contract to prevent re-entry or concurrent calls. Since `_loadLiquidity` is called only by `loadLiquidity` (which is `onlyOwner`), and `loadLiquidity` is not `nonReentrant`, this variable does not provide any additional security or reentrancy protection. Its current usage appears redundant (7.2 Code Security).

**Recommendation:** Remove the `loadingLiquidity` state variable as it does not serve a functional security purpose. If its intent was to prevent re-entry, the `nonReentrant` modifier should be applied to `loadLiquidity` if concurrent calls are a concern, though `onlyOwner` already limits this significantly. If it's for internal state tracking, consider if it's truly necessary or if local variables suffice.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc506...3edf`](https://etherscan.io/address/0xc50673edb3a7b94e8cad8a7d4e0cd68864e33edf) |
| **Network** | Ethereum |
| **Price** | $0.007698 |
| **24h Volume** | $56.5K |
| **Liquidity** | $1.33M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 40.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 54 buys / 76 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xbdb0f9c31367485f85e691f638345f3de673a78effaff71ce34bc7ff1d54fddc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/punkstrategy-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
