---
token: Anakin Coin
ticker: ANAKIN
network: solana
risk_score: 17
status: low
date: 2026-11-02
---

# Anakin Coin (ANAKIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anakin-coin-sol)

---

## Audit Summary

Anakin Coin is a Token-2022 asset with both mint and freeze authorities successfully revoked, providing strong protection against supply inflation and account freezing. The project exhibits high trading volume relative to its liquidity, suggesting potential wash trading, though liquidity is fully burned. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the token's trading activity, as the high volume-to-liquidity ratio may indicate artificial market activity. Since holder concentration data is unavailable, users should exercise caution regarding potential whale influence on price stability.

Verify the current mint and freeze authority status on a block explorer to confirm they remain set to null. Ensure that any future interactions with the token are conducted through reputable decentralized exchanges.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or default frozen states. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.1 Architecture is… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic indicators show $150,157 in liquidity, which is fully burned, ensuring 7.5 Governance and liquidity safety. However, 7.6 External market data indicates a volume/liquidity ratio of 29.39… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is non-mutable, and extension configurations are locked. No further administrative changes can be performed on the mint account. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 29.39, which exceeds the 20x threshold, indicating potential wash trading or artificially inflated volume.

**Recommendation:** Monitor trading patterns and exercise caution regarding the token's actual market demand.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $152K (DexScreener, all pools). 24h trading volume $4.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $152K of DEX liquidity across 5 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8s4bNq...pump`](https://solscan.io/account/8s4bNqEztH1JP7mkU747uMr7AckCQdiV47FDqYnDpump) |
| **Network** | Solana |
| **Price** | $0.003028 |
| **24h Volume** | $4.33M |
| **Liquidity** | $152.0K |
| **Volume / Liquidity** | 28.5× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 51480 buys / 21206 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hcgpz2exv8sfcmvq9fjpbd71brljvzutd2avvv86gwbk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anakin-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
