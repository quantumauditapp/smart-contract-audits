---
token: Baby BFT
ticker: BBFT
network: bsc
risk_score: 75
status: high
date: 2026-10-11
---

# Baby BFT (BBFT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/baby-bft-bsc)

---

## Audit Summary

The BBFT token is an ERC-20 standard token with additional configurable transfer mechanisms. The contract's ownership has been renounced, meaning many powerful administrative functions are now dormant and cannot be called. However, a designated 'treasuryaddress' retains significant control over certain operational parameters, including the ability to influence transfer rules, adjust swap thresholds, and manage treasury funds. This audit identified several medium and low-severity findings related to the active controls held by the 'treasuryaddress'.

> **Final Recommendation:** Token holders should be fully aware of the active powers retained by the `treasuryaddress` despite the renounced ownership. It is crucial to understand the implications of the `treasuryaddress`'s ability to influence transfer rules, adjust swap thresholds, and manage treasury funds. Ensure the `treasuryaddress` is a highly trusted and secure entity, as its actions directly impact the token's operational dynamics and economic parameters. For long-term stability, consider transparent communication regarding any changes made by the `treasuryaddress` to maintain community trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The BBFT contract implements the ERC-20 standard, providing core token functionalities like `transfer` and `balanceOf`. The technical architecture includes mechanisms to control token transfers… |
| **Governance / Economics** | 1/10 | High | The governance and economic model of the BBFT token is significantly shaped by the renounced ownership (7.5 Governance). This means that functions like `updateMaxBuyAmount`, `updateSellFee`, and… |
| **Upgrades** | 6/10 | Medium | The BBFT contract is not implemented as a proxy and therefore does not support upgradeability (7.7 Upgrades). This means the contract's logic is immutable once deployed, providing certainty that its… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `CP-05` — Treasury Address Can Influence Transfer Rules Related to Swaps  *(Severity: Medium · Status: Unresolved)*

The `treasuryaddress` has the ability to call the `manualSwap()` function. This function can temporarily activate or deactivate certain swap-related transfer rules by setting an internal 'swapping' flag. While the `owner` role, which could control other transfer switches like `enableTrading` and `removeLimits`, has been renounced, the `treasuryaddress` still retains this specific control over swap-related transfers.

**Recommendation:** Token holders should be aware that the `treasuryaddress` can influence how tokens are processed during swaps by using the `manualSwap()` function. It is important to trust the entity controlling the `treasuryaddress` to manage this responsibly and transparently.


### `CP-07` — Treasury Address Can Influence Token Fees for Treasury Operations  *(Severity: Medium · Status: Unresolved)*

The `treasuryaddress` can call the `manualSwap()` function, which has the capability to influence the amount of tokens collected for the treasury (referred to as `tokensForTreasury`). This effectively allows the `treasuryaddress` to adjust a portion of the fees or taxes applied to certain transactions that contribute to the treasury. While the `owner` role, which could directly update `buyFee` and `sellFee`, has been renounced, the `treasuryaddress` retains this indirect control over treasury-related fees.

**Recommendation:** Token holders should understand that the `treasuryaddress` can affect the amount of tokens directed to the treasury through the `manualSwap()` function. Transparency from the `treasuryaddress` regarding its use of this function is recommended.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x08f8…e52d — holds 99.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 90% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Treasury Address Can Change Swap Thresholds  *(Severity: Low · Status: Unresolved)*

The `treasuryaddress` has the ability to call the `updateSwapThreshold(uint256 newAmount)` function. This function allows the `treasuryaddress` to change the `swapTokensAtAmount` value, which dictates the minimum amount of tokens that must be accumulated before an automatic swap is triggered. While the `owner` role, which could control other limits like `maxWalletAmount`, `maxSellAmount`, and `maxBuyAmount`, has been renounced, the `treasuryaddress` still controls this specific operational threshold.

**Recommendation:** Token holders should be aware that the `treasuryaddress` controls the `swapTokensAtAmount` threshold, which influences the token's liquidity management. The `treasuryaddress` should be a trusted entity that manages this parameter in the best interest of the token ecosystem.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 45.5% of supply. Of that, 3.2% burned, 2.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 40.1% in wallets, 0.0% in other contracts. 22,707 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Baby BFT (BBFT), market cap $2M, rank #2450. 22,707 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $93K (DexScreener, all pools). 24h trading volume $36K (CoinGecko, all markets, daily snapshot). 24h trading volume $52K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.00794 on 2025-10-08; the price is now 97.6328% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 5% on sell. Market: $93K of DEX liquidity across 2 pools. Launch: 462 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfb69...5769`](https://bscscan.com/address/0xfb69e2d3d673a8db9fa74ffc036a8cf641255769) |
| **Network** | BNB Chain |
| **Price** | $0.0001866 |
| **24h Volume** | $48.5K |
| **Liquidity** | $84.0K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 45.5% of supply |
| **Buy / Sell Tax** | 4.0% / 5.0% |
| **24h Transactions** | 481 buys / 267 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xfea962de14d0119edcc0d7cb3bf952ca00feb9d7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/baby-bft-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
