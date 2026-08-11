---
token: HandlPay
ticker: HANDL
network: base
risk_score: 28
status: medium
date: 2026-08-11
---

# HandlPay (HANDL) — Smart Contract Security Analysis | Base

> **Risk Score: 28/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/handlpay-base)

---

## Audit Summary

This audit covers the HandlToken and HANDLSwap contracts. The HandlToken is an OFT-compliant ERC-20 token with Ownable access control. The HANDLSwap contract provides a simple fixed-price exchange between HANDL and USDC, managed by a single administrator. Key findings include significant centralization risks in the swap contract, a potential for decimal mismatch in swap calculations, and a lack of user slippage protection. The contracts are generally well-structured, but the high degree of administrative control introduces a single point of failure.

> **Final Recommendation:** It is strongly recommended to decentralize or enhance the security of the `admin` role in the HANDLSwap contract, ideally by implementing a multi-signature wallet or a time-locked governance mechanism for critical functions like price setting and fund withdrawals. Additionally, explicitly document and verify the decimal precision assumptions for HANDL and USDC within the swap calculations to prevent potential trading errors. Consider adding user-facing slippage protection to improve user experience and safety.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The technical architecture (7.1) of both contracts is straightforward. The HandlToken leverages OpenZeppelin's Ownable and LayerZero's OFT for standard and cross-chain functionality. The HANDLSwap… |
| **Governance / Economics** | 6/10 | Medium | The economic model (7.4) of the HANDLSwap contract is a simple fixed-price exchange, entirely controlled by an administrator. The governance (7.5) is highly centralized, with a single `admin` address… |
| **Upgrades** | 9/10 | Low | Neither the HandlToken nor the HANDLSwap contract implements any upgrade mechanism (7.7). Both contracts are designed to be immutable once deployed. This eliminates upgrade-related risks such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 48.1% |
| **Top-3 Unlocked** | ⚠️ 90.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control and Single Point of Failure in HANDLSwap  *(Severity: High · Status: Unresolved)*

The HANDLSwap contract grants extensive control to a single `admin` address, set immutably during deployment. This administrator can unilaterally set the swap price (`setPrice`), pause all trading activities (`setPaused`), and withdraw all HANDL and USDC tokens held by the contract (`withdrawHANDL`, `withdrawUSDC`). This high degree of centralization (7.3, 7.5, 7.8) creates a significant single point of failure. A compromise of the admin's private key could lead to complete loss of funds, arbitrary price manipulation, and denial of service for all users.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `admin` role to require multiple approvals for critical operations. For less time-sensitive actions like price updates, consider adding a timelock mechanism to allow users to react to impending changes. Explore options for progressive decentralization of control over time.


### `M-01` — Potential Decimal Mismatch Risk in Swap Calculations  *(Severity: Medium · Status: Unresolved)*

The `buyHANDL` and `sellHANDL` functions perform arithmetic operations involving `1e18` and `usdcPerHandl` to calculate swap amounts. While these calculations are mathematically sound for specific decimal assumptions (e.g., HANDL 18 decimals, USDC 6 decimals, and `usdcPerHandl` representing the price in 6-decimal USDC), these assumptions are not explicitly stated or enforced in the code (7.2). If `usdcPerHandl` is set with an incorrect decimal precision relative to USDC, or if USDC itself does not have 6 decimals, trades could result in incorrect token amounts being exchanged, leading to user losses or contract insolvency.

**Recommendation:** Explicitly document the expected decimal precision for HANDL, USDC, and `usdcPerHandl` in the contract's NatSpec comments. Consider adding a mechanism to verify or enforce the decimal places of the underlying ERC-20 tokens, if possible, or ensure robust off-chain procedures for setting `usdcPerHandl` correctly. Implement comprehensive unit tests covering various decimal scenarios.


### `L-01` — Lack of Slippage Protection for Users  *(Severity: Low · Status: Unresolved)*

The `buyHANDL` and `sellHANDL` functions execute swaps at the current `usdcPerHandl` price without any user-defined slippage tolerance (7.4). While the price is fixed by the admin, an admin could theoretically change the price between a user's transaction submission and its inclusion in a block. Without slippage protection, users could receive fewer tokens than expected if the price changes unfavorably, or their transaction could revert if the price moves too much.

**Recommendation:** Consider adding an optional `minHandlAmount` or `maxUsdcAmount` parameter to the `buyHANDL` and `sellHANDL` functions, respectively. This would allow users to specify their acceptable slippage, ensuring they do not receive significantly less than expected or pay significantly more due to price changes or front-running (though less critical with an admin-set price).


### `I-01` — Hardcoded Chain ID for Initial Minting  *(Severity: Informational · Status: Unresolved)*

The `HandlToken` constructor includes a condition `if(block.chainid == 137)` to mint initial tokens only on Polygon (chain ID 137). This design choice (7.1) means that if the contract is deployed on any other chain, the initial minting to `msg.sender` will not occur. While this is likely an intentional deployment strategy for a multi-chain token, it's a hardcoded dependency.

**Recommendation:** Ensure this hardcoded chain ID aligns with the intended deployment strategy across all target networks. If initial minting is desired on other chains, the condition would need to be adjusted or removed, or a separate minting mechanism implemented post-deployment.


### `I-02` — No Emergency Stop for Admin Fund Withdrawals  *(Severity: Informational · Status: Unresolved)*

The `HANDLSwap` contract includes a `setPaused` function to halt trading, but the `withdrawHANDL` and `withdrawUSDC` functions, which allow the admin to drain funds, are not subject to the `whenNotPaused` modifier (7.8). This means that even if the contract is paused due to an emergency, the admin retains the ability to withdraw all funds. While the admin is trusted, this could be a concern if the admin key is compromised during a pause event.

**Recommendation:** Consider whether `withdrawHANDL` and `withdrawUSDC` should also be subject to a `whenNotPaused` modifier, or if a separate, more secure withdrawal mechanism (e.g., requiring a multi-sig or timelock) should be implemented, especially for large amounts. This would provide an additional layer of protection even if the admin key is compromised.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3bbc...4425`](https://basescan.org/address/0x3bbcb624cb9a1f73163a886f460f47603e5e4425) |
| **Network** | Base |
| **Price** | $0.002844 |
| **24h Volume** | $71.1K |
| **Liquidity** | $53.4K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 69.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1319 buys / 882 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x186696a647c554c7dbea30e295259aa46d40effc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/handlpay-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
