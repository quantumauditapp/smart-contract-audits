---
token: The Sheeple Flock
ticker: SHEEPLE
network: solana
risk_score: 40
status: medium
date: 2026-10-23
---

# The Sheeple Flock (SHEEPLE) — Smart Contract Security Analysis | Solana

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-sheeple-flock-sol)

---

## Audit Summary

The Sheeple Flock (SHEEPLE) is a Token-2022 asset with revoked mint and freeze authorities, ensuring supply stability and preventing account freezing. Liquidity is fully locked, and no high-risk flags were identified by third-party registries. The primary risks are a 3% transfer fee and mutable metadata.

> **Final Recommendation:** Investors should account for the 3% transfer fee when calculating swap slippage and profit margins. As metadata is mutable, verify the token name and symbol against official project channels before executing transactions.

Monitor the transfer fee authority if the project team intends to finalize the fee structure. No further on-chain action is required for liquidity safety, as the pool is fully locked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the SPL Token-2022 program, which supports advanced extensions. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are revoked. 7.2 Code… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance metrics show healthy distribution, with the top 10 holders controlling 24.16% of supply. 7.6 External liquidity is stable at $68,846, with 100% of pool liquidity… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades and 7.8 Operations are limited by the immutable nature of the mint. While the mint and freeze authorities are revoked, the transfer fee configuration is currently marked as upgradable.… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 3.0% · upgradeable |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable, meaning the branding can be altered by the authority at any time.

**Recommendation:** Verify metadata against official project sources before interacting with the token.


### `L-01` — Transfer Fee Active  *(Severity: Low · Status: Unresolved)*

The token implements a 3% (300 bps) transfer fee on every transaction.

**Recommendation:** Factor the 3% fee into all trading and liquidity provision calculations.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.9% of supply. Of that, 9.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.3% in wallets, 5.9% in other contracts. 453 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as The Sheeple Flock (SHEEPLE), rank #3558. 453 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $69K (DexScreener, all pools). 24h trading volume $64K (CoinGecko, all markets, daily snapshot). 24h trading volume $53K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $69K of DEX liquidity across 2 pools. Launch: 37 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`TVvnJT...rCq4`](https://solscan.io/account/TVvnJTedD3WgAPede2xUmRjweJqNdhCEgyjtKv3rCq4) |
| **Network** | Solana |
| **Price** | $0.0007085 |
| **24h Volume** | $52.9K |
| **Liquidity** | $68.6K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 33.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1711 buys / 737 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/akm2ua4zjwkcjq3dkiv2wmeik1b1a9tauxowjf3c94wr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-sheeple-flock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
