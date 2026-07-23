---
token: Build On BNB
ticker: BOB
network: bsc
risk_score: 60
status: high
date: 2026-07-23
---

# Build On BNB (BOB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 60/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/build-on-bnb-bsc)

---

## Audit Summary

The Build On BNB (BOB) token contract is an ERC-20 implementation with custom tokenomics including taxes, max transaction limits, and an anti-bot transfer delay. The audit identified a critical vulnerability related to uninitialized trading parameters combined with renounced ownership, which could render the token untradable. High-severity issues include the absence of a `receive()` function, potentially locking ETH. Economic risks stem from fixed high initial taxes and an immutable tax wallet. The contract is not upgradeable, making any post-deployment fixes impossible without redeployment.

> **Final Recommendation:** Address the critical issue of uninitialized trading and liquidity parameters by ensuring `uniswapV2Router`, `uniswapV2Pair`, `tradingOpen`, and `swapEnabled` are properly set in the constructor or via a one-time initialization function callable before ownership renunciation. Implement a `receive()` or `fallback()` function to securely handle incoming ETH from swap operations. Reconsider the use of `SafeMath` for Solidity 0.8+ to reduce bytecode size. Evaluate the implications of renounced ownership on the immutability of high initial taxes and the fixed tax wallet, ensuring these parameters align with long-term project goals and do not create unmanageable situations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The contract utilizes `SafeMath` for arithmetic, although it's redundant in Solidity 0.8+. A critical vulnerability exists where core trading and liquidity parameters (`uniswapV2Router`… |
| **Governance / Economics** | 5/10 | Medium | The tokenomics feature high initial buy/sell taxes (22%) that reduce over time, along with max transaction and wallet size limits. With ownership renounced, these parameters are immutable, preventing… |
| **Upgrades** | 7/10 | Low | The contract is not designed with any upgradeability mechanisms, as indicated by `is_proxy: false` (7.7 Upgrades). This means the contract's logic is immutable once deployed. While this eliminates… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Unmanageable Trading & Liquidity Setup After Ownership Renunciation  *(Severity: Critical · Status: Unresolved)*

The contract relies on `uniswapV2Router`, `uniswapV2Pair`, `tradingOpen`, and `swapEnabled` for its core trading and liquidity functions. These variables are not initialized in the provided constructor. If their setter functions are `onlyOwner` and ownership has been renounced (as indicated by `ownership_renounced: true`), these critical parameters can never be set. This would render the token untradable and prevent liquidity provision, effectively bricking the token's functionality.

**Recommendation:** Ensure all critical trading and liquidity parameters (`uniswapV2Router`, `uniswapV2Pair`, `tradingOpen`, `swapEnabled`) are initialized within the constructor or through a dedicated, one-time initialization function that is called immediately after deployment and before ownership is renounced.


### `H-01` — Missing `receive()`/`fallback()` Function  *(Severity: High · Status: Unresolved)*

The contract is designed to interact with Uniswap for swapping tokens to ETH and potentially adding liquidity. If the contract itself is the recipient of ETH during these operations (e.g., `swapExactTokensForETHSupportingFeeOnTransferTokens` sends ETH to the contract), a `receive()` or `fallback()` function is required to accept the ETH. Without such a function, incoming ETH will be locked in the router or revert the transaction, leading to loss of funds or operational failure.

**Recommendation:** Implement a `receive() external payable` function to allow the contract to accept incoming ETH. This is crucial for the proper functioning of the swap and liquidity mechanisms.


### `M-01` — Fixed and High Initial Taxes  *(Severity: Medium · Status: Unresolved)*

The contract implements high initial buy/sell taxes (22%). While these taxes are designed to reduce to 0% over time, the initial high rate can deter early adoption and trading. With ownership renounced, these tax parameters are immutable, meaning the initial high tax phase cannot be adjusted or removed by an owner, regardless of market conditions or community feedback.

**Recommendation:** Consider if the initial tax rates are appropriate for the project's long-term goals, especially given their immutability. If flexibility is desired, an owner-controlled mechanism to adjust these parameters would be necessary, but this conflicts with renounced ownership. Ensure the community is fully aware of the fixed tax structure.


### `M-02` — Fixed Tax Wallet Address  *(Severity: Medium · Status: Unresolved)*

The `_taxWallet` address is set in the constructor and cannot be changed after deployment. If this address becomes compromised, inaccessible, or the intended recipient changes (e.g., due to a multi-sig upgrade or a new treasury address), all collected taxes will be sent to an unrecoverable or incorrect address. With ownership renounced, this address cannot be updated.

**Recommendation:** If the project requires flexibility for the tax wallet, consider implementing an owner-controlled function to update the `_taxWallet` address. However, this would require ownership not to be renounced. If ownership remains renounced, ensure the `_taxWallet` is a highly secure, multi-signature controlled address that is intended for permanent use.


### `L-01` — `tx.origin` Usage for Anti-Bot Measure  *(Severity: Low · Status: Unresolved)*

The `_holderLastTransferTimestamp` mechanism uses `tx.origin` to enforce a transfer delay, intended as an anti-bot measure. While `tx.origin` is generally discouraged in smart contracts due to potential phishing attack vectors if used for access control, in this specific context, it's used for an anti-bot measure. However, it means that if a contract calls `transfer`, the `tx.origin` will be the EOA that initiated the transaction, not the contract itself, which might have unintended side effects for complex interactions.

**Recommendation:** While the risk is low in this specific implementation, it's generally recommended to use `msg.sender` for all address-related checks to avoid `tx.origin` related complexities and potential misunderstandings. If the anti-bot logic specifically requires `tx.origin`, ensure its implications are fully understood and documented.


### `I-01` — Redundant SafeMath Library  *(Severity: Informational · Status: Unresolved)*

The contract uses the `SafeMath` library for arithmetic operations. However, Solidity version `^0.8.8` includes built-in overflow and underflow checks by default, making the `SafeMath` library redundant. This adds unnecessary bytecode to the contract and slightly increases deployment and transaction gas costs without providing additional security benefits.

**Recommendation:** Remove the `SafeMath` library and its `using SafeMath for uint256;` directive. Rely on Solidity's native overflow/underflow protection for `uint256` operations in version 0.8.0 and higher.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5136...560e`](https://bscscan.com/address/0x51363f073b1e4920fda7aa9e9d84ba97ede1560e) |
| **Network** | BNB Chain |
| **Price** | $0.00000002 |
| **24h Volume** | $143.3K |
| **Liquidity** | $1.10M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 622 buys / 716 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x3c79593e01a7f7fed5d0735b16621e2d52a6bc58)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/build-on-bnb-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-23*
