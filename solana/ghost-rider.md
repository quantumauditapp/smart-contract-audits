---
token: GHOST RIDER
ticker: GHOST
network: solana
risk_score: 13
status: low
date: 2026-11-04
---

# GHOST RIDER (GHOST) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ghost-rider-sol)

---

## Audit Summary

The GHOST RIDER token is a standard SPL-2022 mint with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, and no malicious extensions are active. Holder concentration data was unavailable, and a third-party registry flagged high holder correlation, which should be monitored.

> **Final Recommendation:** Investors should monitor the token's holder distribution using block explorers to assess the impact of the flagged 'high holder correlation'. Since the mint and freeze authorities are revoked and liquidity is burned, the primary remaining risk is market-driven concentration rather than technical manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.8… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance factors are supported by $42,001 in liquidity, which is 100% burned. 7.6 External signals indicate high holder correlation, though specific concentration data is… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL mint. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is fixed and cannot be altered by the… |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — High Holder Correlation Flag  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be held by related wallets.

**Recommendation:** Perform periodic checks on top holder wallet activity to identify potential coordinated sell-off risks.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $42K (DexScreener, all pools). 24h trading volume $127K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $42K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`42qKoG...pump`](https://solscan.io/account/42qKoGmEPTRJsa5jWrYwpydL8RkBwMvg2ykYVoerpump) |
| **Network** | Solana |
| **Price** | $0.0002507 |
| **24h Volume** | $126.8K |
| **Liquidity** | $41.8K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1820 buys / 1825 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9sprpcpexeosec37remxg5s1asa1ovcqs8kganwjcuxt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ghost-rider-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
