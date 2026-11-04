---
token: george
ticker: GEORGE
network: solana
risk_score: 22
status: low
date: 2026-11-04
---

# george (GEORGE) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/george-sol)

---

## Audit Summary

The token 'george' utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should monitor the token's market activity, as the high volume-to-liquidity ratio is a strong indicator of artificial trading volume. Verify that the token's utility aligns with its current market behavior before committing capital.

Regularly check the mint address on a block explorer to ensure no unexpected changes occur to the token's immutable status, although current settings prevent such modifications.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are set to null (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully secured with 100% of LP tokens burned (7.4 Economic). However, the 24h volume-to-liquidity ratio of 121.80 indicates significant wash-trading activity (7.8 Operations). Holder… |
| **Upgrades** | 10/10 | Low | The mint is immutable regarding metadata and authority settings (7.7 Upgrades). No upgrade paths exist for the token program or transfer logic. The configuration is permanent (7.3 Access Control). |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume is 121.80x the total liquidity, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as the reported volume may not represent genuine market demand.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $2.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Hbpjmu...pump`](https://solscan.io/account/Hbpjmu51QXzwojmtvnzzFtwpgYdP8SUwxTTDACGxpump) |
| **Network** | Solana |
| **Price** | $0.00006127 |
| **24h Volume** | $2.47M |
| **Liquidity** | $21.4K |
| **Volume / Liquidity** | 115.5× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 23593 buys / 21316 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/b1t63lntnyainfqwml7aoj3xekcfr7cokf7nhgmvh8jq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/george-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
