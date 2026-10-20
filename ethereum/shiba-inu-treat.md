---
token: Shiba Inu Treat
ticker: TREAT
network: ethereum
risk_score: 31
status: low
date: 2026-10-03
---

# Shiba Inu Treat (TREAT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 31/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/shiba-inu-treat-eth)

---

## Audit Summary

The Treat contract is an ERC-20 token with burnable functionality. The audit identified one medium-severity issue related to the contract's ability to receive Ether without a mechanism for withdrawal, leading to potential loss of funds if Ether is accidentally sent to the contract.

> **Final Recommendation:** It is recommended to implement a mechanism to handle accidental Ether transfers, such as a `receive()` or `fallback()` function that either reverts or allows a designated owner to withdraw funds. For future deployments, consider adding a `withdrawETH` function if the contract is intended to interact with Ether. Ensure all external interactions are thoroughly tested to prevent unintended fund transfers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Treat contract implements a standard ERC-20 token with burnable functionality, providing basic token operations such as transfer, approval, and burning. The architecture is straightforward… |
| **Governance / Economics** | 1/10 | High | The Treat contract functions as a basic ERC-20 token and does not incorporate any specific governance mechanisms or complex economic models (7.5 Governance, 7.4 Economic). Its design is limited to… |
| **Upgrades** | 8/10 | Low | The Treat contract is not designed as an upgradeable proxy contract (7.7 Upgrades). This means its logic is immutable once deployed, eliminating risks associated with upgrade mechanisms such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CD-01` — ETH can be received but never withdrawn  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH and has no way to send it out. Functions: constructor.

**Recommendation:** Review the flagged functions; the static analyser reported this as `locked-ether`.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x3a94…9323 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 83% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 68.3% of supply. What remains: 17.0% in wallets, 51.3% in other contracts. 4,400 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Shiba Inu Treat (TREAT), market cap $1M, rank #2833. 4,400 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $52K (DexScreener, all pools). 24h trading volume $162K (CoinGecko, all markets, daily snapshot). 24h trading volume $43K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0195 on 2025-01-25; the price is now 98.836% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $52K of DEX liquidity across 16 pools. Launch: 626 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa02c...99f4`](https://etherscan.io/address/0xa02c49da76a085e4e1ee60a6b920ddbc8db599f4) |
| **Network** | Ethereum |
| **Price** | $0.0002415 |
| **24h Volume** | $36.1K |
| **Liquidity** | $43.3K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 68.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 177 buys / 129 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x21d7f10712d222b66106ce0ad9c7a8e5434347b2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/shiba-inu-treat-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
