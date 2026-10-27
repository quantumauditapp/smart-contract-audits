---
token: America Party
ticker: AP
network: ethereum
risk_score: 4
status: low
date: 2026-10-27
---

# America Party (AP) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 4/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/america-party-eth)

---

## Audit Summary

The contract is a standard ERC-20 token with additional tax, anti-whale, and blacklisting features. Ownership has been successfully renounced, effectively disabling all privileged administrative functions. The code is standard and follows common patterns for this type of token.

> **Final Recommendation:** The contract is immutable and secure for users as the owner cannot modify parameters. Users should be aware that the token includes transfer fees and potential blacklisting logic that was set prior to renouncement.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements standard ERC-20 functionality with robust transfer logic. 7.1 Architecture is straightforward, utilizing OpenZeppelin-like patterns. 7.2 Code Security is generally high… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance aspects are currently fixed. Since ownership is renounced, no further changes to fees or limits can be made. 7.6 External dependencies are limited to standard DEX… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable and immutable. No upgrade path exists for the current implementation. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.4% (≈ permanent lock) |
| **LP Locked** | 99.4% — Null Address |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 9 Informational_

### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $112K (DexScreener, all pools). 24h trading volume $1K (CoinGecko, all markets, daily snapshot). 24h trading volume $52K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.041 on 2025-07-07; the price is now 99.5377% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `CD-01` — Rounding Loss from Division  *(Severity: Low · Status: Unresolved)*

The _transfer function performs division before multiplication, which can lead to minor precision loss in fee calculations.

**Recommendation:** Perform all multiplications before divisions to maintain precision.


### `CP-02` — Privileged Balance Manipulation (Dormant)  *(Severity: Informational · Status: Unresolved)*

The airdropToWallets function allows the owner to move tokens between addresses. This is now impossible as ownership is renounced.

**Recommendation:** No action required as the function is inaccessible.


### `CP-05` — Privileged Transfer Control (Dormant)  *(Severity: Informational · Status: Unresolved)*

Various functions allow the owner to toggle trading or swap settings. These are now permanently locked in their current state.

**Recommendation:** No action required as the functions are inaccessible.


### `CP-06` — Privileged Blacklisting (Dormant)  *(Severity: Informational · Status: Unresolved)*

The owner could previously blacklist addresses from trading. This functionality is now disabled.

**Recommendation:** No action required as the function is inaccessible.


### `CP-07` — Privileged Fee Modification (Dormant)  *(Severity: Informational · Status: Unresolved)*

The owner could modify buy/sell fees. These fees are now fixed.

**Recommendation:** No action required as the functions are inaccessible.


### `CP-08` — Privileged Limit Modification (Dormant)  *(Severity: Informational · Status: Unresolved)*

The owner could change max transaction or wallet limits. These are now fixed.

**Recommendation:** No action required as the functions are inaccessible.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.2% of supply. Of that, 22.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.2% in wallets, 10.2% in other contracts. 4,963 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as America Party (AP), rank #4734. 4,963 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.4% of the pool's LP is burned or time-locked. 99.4% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $112K of DEX liquidity across 3 pools. Launch: 507 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe60e...07f4`](https://etherscan.io/address/0xe60e9bd04ccc0a394f1fdf29874e35a773cb07f4) |
| **Network** | Ethereum |
| **Price** | $0.00025 |
| **24h Volume** | $50.2K |
| **Liquidity** | $104.7K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 42.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 70 buys / 60 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x6d3835560bd69c094db31f4a471fb947eae93179)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/america-party-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
