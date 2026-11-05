---
token: inu
ticker: INU
network: solana
risk_score: 24
status: low
date: 2026-11-05
---

# inu (INU) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/inu-sol-a662)

---

## Audit Summary

The token 'inu' utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, the high volume-to-liquidity ratio suggests potential wash trading. Holder concentration data is currently unavailable from on-chain sources.

> **Final Recommendation:** Investors should monitor the token for sustained organic volume, as the current high ratio relative to liquidity is a common indicator of artificial trading activity. Since liquidity is burned, the pool is safe from creator withdrawal, but market depth remains limited.

Verify the current supply and holder distribution using a block explorer to ensure no single wallet controls a majority of the circulating supply before entering a position.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $16,378 in liquidity, which is fully burned and immutable. 7.5 Governance is decentralized due to revoked authorities. However, 7.6 External signals indicate a… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints are immutable once authorities are revoked. 7.8 Operations are stable; metadata is immutable, and no balance-mutating authorities exist. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour trading volume is 21.99x the total liquidity, exceeding the 20x threshold. This pattern is strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; verify if volume is driven by organic interest or automated trading bots.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $441K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 20 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Bid8i1...pump`](https://solscan.io/account/Bid8i1ocWssjRmKh2kcUfHxD1K6Sk7E5pV2PSVdepump) |
| **Network** | Solana |
| **Price** | $0.00005009 |
| **24h Volume** | $345.4K |
| **Liquidity** | $17.2K |
| **Volume / Liquidity** | 20.1× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4696 buys / 3511 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2uk2pcpqfbcxrkkrs6ib71ak5q2loy3rzqbyvzsnysik)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/inu-sol-a662)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
