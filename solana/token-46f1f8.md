---
token: ᑓହꚡई
ticker: ᑓହꚡई
network: solana
risk_score: 22
status: low
date: 2026-11-03
---

# ᑓହꚡई (ᑓହꚡई) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-46f1f8-sol)

---

## Audit Summary

The token ᑓହꚡई utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the source.

> **Final Recommendation:** Investors should exercise caution due to the high volume-to-liquidity ratio, which is a strong indicator of artificial trading volume. Monitor the token's market activity on decentralized exchanges before committing capital.

Verify the current supply and holder distribution using a block explorer to ensure the token's economic health aligns with your risk tolerance. Since holder concentration data was unavailable, perform manual due diligence on the top token accounts if liquidity depth changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is built on the SPL Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully secured as 100% of LP tokens are burned (7.4 Economic). However, the 24h volume-to-liquidity ratio of 81.84 indicates highly suspicious trading activity (7.6 External). Holder… |
| **Upgrades** | 10/10 | Low | The mint configuration is immutable (7.7 Upgrades). There are no upgrade paths for the token program or its extensions. Metadata is locked and cannot be modified by any party. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 81.84, which significantly exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading patterns for signs of manipulation and avoid relying on volume as a metric for liquidity depth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $16K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $16K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7kYXsF...pump`](https://solscan.io/account/7kYXsF59Cc3HBjL1mW5y9eutEWYh3dTUuvBvnNV7pump) |
| **Network** | Solana |
| **Price** | $0.0000359 |
| **24h Volume** | $1.12M |
| **Liquidity** | $15.8K |
| **Volume / Liquidity** | 70.5× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12864 buys / 8676 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/froantqxue1rheuvzvxnmmyhvtrzrjwea149ikrl7lgb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-46f1f8-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
