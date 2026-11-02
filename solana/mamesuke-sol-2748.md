---
token: Mamesuke
ticker: 豆助
network: solana
risk_score: 24
status: low
date: 2026-11-02
---

# Mamesuke (豆助) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mamesuke-sol-2748)

---

## Audit Summary

The Mamesuke token is a Token-2022 asset with both mint and freeze authorities successfully revoked, providing a baseline level of trust regarding supply and transfer control. However, the token exhibits extreme wash-trading indicators and very low liquidity, which poses a significant risk to market exit. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise extreme caution due to the high volume-to-liquidity ratio, which suggests artificial trading activity. Before interacting, verify the current liquidity depth on a block explorer to ensure slippage remains within acceptable bounds for your position size.

Monitor the token's market activity for sustained, organic volume. Since holder concentration data is unavailable, avoid large capital allocations that could be trapped by the low liquidity environment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Security is bolstered by the revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or default frozen… |
| **Governance / Economics** | 7/10 | Low | Liquidity is severely constrained at $2,217 (7.4 Economic). The 24-hour volume of $1,590,731 relative to liquidity results in a ratio of 717.43, indicating high-probability wash trading (7.6… |
| **Upgrades** | 10/10 | Low | The mint is immutable with no upgradeable components (7.7 Upgrades). Metadata and transfer fee configurations are locked (7.8 Operations). No further administrative changes are possible due to the… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,217. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity constraints in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 717.43x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity is often used to create a false impression of market demand.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Ei19qk...pump`](https://solscan.io/account/Ei19qkvBM3amMyrveNLqKSPB1ESMEUQ6MrqDYwZVpump) |
| **Network** | Solana |
| **Price** | $0.0001504 |
| **24h Volume** | $1.45M |
| **Liquidity** | $31.5K |
| **Volume / Liquidity** | 46.1× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 35916 buys / 10204 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2ims9erzyr885hpjakxpy5fdlfnjjdcf5x95rqg38spn)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mamesuke-sol-2748)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
