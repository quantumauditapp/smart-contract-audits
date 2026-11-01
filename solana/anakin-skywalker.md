---
token: Anakin Skywalker
ticker: ANAKIN
network: solana
risk_score: 17
status: low
date: 2026-11-01
---

# Anakin Skywalker (ANAKIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anakin-skywalker-sol)

---

## Audit Summary

The Anakin Skywalker token (ExxzYBTt3jwU5MUxuw2F4toYbTLdFwThSjyaCn6Xpump) utilizes the Token-2022 program with all critical authorities (Mint and Freeze) successfully revoked. While liquidity is fully burned, the high volume-to-liquidity ratio suggests potential wash trading activity. No third-party risk registry flags were identified.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for potential coordinated sell-offs given the 15.59% concentration. Due to the high volume-to-liquidity ratio, exercise caution regarding price volatility and slippage when executing large trades.

Verify the current holder distribution via block explorers to ensure no single entity has accumulated a controlling interest. Treat the token as a high-volatility asset given the trading patterns observed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the spl-token-2022 program. 7.1 Architecture is standard for SPL tokens with no active extensions like transfer hooks. 7.3 Access Control is robust as both Mint and Freeze… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic analysis shows 15.59% concentration among the top 10 holders. 7.6 External market data indicates $98,152 in liquidity, which is fully burned and immutable. However, the 26.21… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. Metadata is immutable (metadata_mutable: False), and no upgradable extensions are configured. The token configuration is… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 26.21, exceeding the 20x threshold, which is a strong indicator of artificially inflated trade volume.

**Recommendation:** Perform independent analysis of trade frequency and order book depth before committing capital.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 22.9% of supply. Of that, 7.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.6% in wallets, 0.0% in other contracts. 2,638 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,638 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 66% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $125K (DexScreener, all pools). 24h trading volume $3.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $125K of DEX liquidity across 30 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ExxzYB...pump`](https://solscan.io/account/ExxzYBTt3jwU5MUxuw2F4toYbTLdFwThSjyaCn6Xpump) |
| **Network** | Solana |
| **Price** | $0.0008001 |
| **24h Volume** | $2.53M |
| **Liquidity** | $82.3K |
| **Volume / Liquidity** | 30.7× |
| **Token Age** | 2d |
| **Top-10 Holders** | 22.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16269 buys / 13256 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hja61kefsawrt3dw9p15mlh6u5maqgzgbe51ngg7bytt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anakin-skywalker-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
