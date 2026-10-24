---
token: Hercules Cat
ticker: HCAT
network: solana
risk_score: 20
status: low
date: 2026-10-24
---

# Hercules Cat (HCAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hercules-cat-sol)

---

## Audit Summary

Hercules Cat (HCAT) is a Token-2022 asset with both mint and freeze authorities successfully revoked. The liquidity pool is fully burned, preventing rug pulls via liquidity withdrawal. However, the high volume-to-liquidity ratio suggests potential wash trading activity. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should monitor the high volume-to-liquidity ratio, as this often indicates artificial trading activity rather than organic demand. Since the liquidity is burned, the risk of a liquidity-removal rug pull is mitigated, but market volatility remains a factor.

Verify the current supply and holder distribution using a block explorer to ensure that no single entity holds a majority of the circulating supply, as concentration data was not available during this audit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). 7.2 Code Security is maintained by the absence of active extensions like transfer hooks or default frozen states. 7.3 Access Control is… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $25,034 in liquidity, which is fully burned and immutable. 7.5 Governance is decentralized due to the lack of administrative authorities. 7.6 External market data… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints are immutable. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is finalized and cannot be altered by the… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 56.34, which significantly exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; perform independent analysis of trade frequency and wallet diversity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $48K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $48K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3AQmLm...pump`](https://solscan.io/account/3AQmLmBUKGGenieXnkNh1QGoFC1sSTkbdoiEU2Cxpump) |
| **Network** | Solana |
| **Price** | $0.0003115 |
| **24h Volume** | $1.32M |
| **Liquidity** | $48.1K |
| **Volume / Liquidity** | 27.4× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 24803 buys / 7621 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5va867jsgvxqqjfgt1gjkqp2gmq9muwrydieedkrrm4m)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hercules-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
