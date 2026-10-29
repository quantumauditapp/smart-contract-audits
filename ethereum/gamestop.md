---
token: GameStop
ticker: GME
network: ethereum
risk_score: 33
status: low
date: 2026-10-29
---

# GameStop (GME) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gamestop-eth)

---

## Audit Summary

The GME token is a standard ERC-20 implementation with added transfer taxes, transaction limits, and bot-blocking capabilities. While ownership has been renounced, effectively locking the owner-restricted functions, the taxWallet remains a privileged role capable of modifying fees and executing token swaps. The contract architecture is straightforward, but the presence of centralized control over economic parameters via the taxWallet introduces moderate risk.

> **Final Recommendation:** Investors should be aware that the taxWallet retains the ability to adjust fees and trigger liquidity swaps, which directly impacts the token's economic utility. Since ownership is renounced, the current configuration of limits and bot lists is permanent and cannot be modified by the original deployer.

We recommend that the taxWallet role be transferred to a multi-signature wallet or a time-locked contract to mitigate the risk of a single point of failure. Users should monitor the taxWallet address for any unexpected changes to fee structures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract follows standard ERC-20 patterns with 7.1 Architecture and 7.2 Code Security adhering to common practices. 7.3 Access Control is split between renounced ownership and an active taxWallet… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic parameters such as transfer taxes are adjustable by the taxWallet. 7.5 Governance is non-existent as ownership is renounced, preventing further changes to limits or bot lists. The… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to the taxWallet's ability to trigger swaps and rescue tokens. The lack of upgradeability ensures the logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 2 Medium · ⚪ 7 Informational_

### `CP-05` — Centralized Control Over Swap Mechanism  *(Severity: Medium · Status: Unresolved)*

The taxWallet can trigger the manualSwap function, which executes token sales and ETH distribution. This allows the controller to influence the token's liquidity and fee distribution process.

**Recommendation:** Consider automating the swap process based on contract balance thresholds rather than relying on manual triggers.


### `CP-07` — Adjustable Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The taxWallet can call reduceFee to modify the buy and sell tax percentages. This allows the controller to change the economic cost of trading the token at any time.

**Recommendation:** Implement a timelock or a maximum fee cap to prevent sudden, drastic changes to the tax structure.


### `CP-06` — Bot List Functionality (Dormant)  *(Severity: Informational · Status: Unresolved)*

The contract contains functions to add or remove addresses from a bot list. Since ownership is renounced, these functions are effectively disabled and cannot be called by anyone.

**Recommendation:** No action required as the functions are unreachable.


### `CP-08` — Transaction and Wallet Limits (Dormant)  *(Severity: Informational · Status: Unresolved)*

The removeLimits function allows for the removal of transaction and wallet size restrictions. Since ownership is renounced, this function is effectively disabled.

**Recommendation:** No action required as the function is unreachable.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.8% of supply. Of that, 2.2% burned, 12.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.4% in wallets, 12.2% in other contracts. 11,452 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GME (Ethereum) (GME), market cap $2M, rank #2329. 11,452 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $777K (DexScreener, all pools). 24h trading volume $10K (CoinGecko, all markets, daily snapshot). 24h trading volume $42K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.000413 on 2024-12-12; the price is now 98.6792% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $777K of DEX liquidity across 2 pools. Launch: 899 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc56c...12b8`](https://etherscan.io/address/0xc56c7a0eaa804f854b536a5f3d5f49d2ec4b12b8) |
| **Network** | Ethereum |
| **Price** | $0.00000771 |
| **24h Volume** | $42.5K |
| **Liquidity** | $776.9K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 37.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 80 buys / 25 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2aeee741fa1e21120a21e57db9ee545428e683c9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gamestop-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
