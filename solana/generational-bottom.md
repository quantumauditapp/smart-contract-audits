---
token: Generational Bottom
ticker: BOTTOM
network: solana
risk_score: 24
status: low
date: 2026-11-04
---

# Generational Bottom (BOTTOM) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/generational-bottom-sol)

---

## Audit Summary

The BOTTOM token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio suggesting potential wash trading, and third-party registry data indicates high holder concentration. Holder distribution data was unavailable from the RPC source.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may indicate artificial market activity. Monitor the top holder wallets for potential sell-side pressure given the concentration warnings from third-party registries.

Verify the current supply and holder distribution via block explorers to ensure the concentration levels align with your risk tolerance before executing large trades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the spl-token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is maintained by the… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance risks are present due to high holder concentration reported by third-party registries. 7.6 External market data shows $17,569 in liquidity, which is fully burned… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL tokens do not use proxy patterns. 7.8 Operations are secure as metadata is immutable and no authority exists to modify token parameters or account states. |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 22.67, exceeding the 20x threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading activity for signs of automated wash trading and account for potential liquidity gaps during high volatility.


### `M-01` — High Holder Concentration  *(Severity: Medium · Status: Unresolved)*

Third-party registry data indicates high ownership concentration among the top 10 holders, including single-wallet dominance.

**Recommendation:** Assess the risk of price manipulation or sudden sell-offs by large holders before entering a position.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $406K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 6 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9m8kNF...pump`](https://solscan.io/account/9m8kNFcVwtSqHdGDHjK6yCMLxYBjdCECCZ7zEThcpump) |
| **Network** | Solana |
| **Price** | $0.00005297 |
| **24h Volume** | $398.2K |
| **Liquidity** | $17.5K |
| **Volume / Liquidity** | 22.8× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3242 buys / 2142 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2uumgshnvxbmz4s4e6gnhk2dntoajggdhje5bh2vqotf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/generational-bottom-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
