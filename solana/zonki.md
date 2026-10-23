---
token: zonki
ticker: ZONKI
network: solana
risk_score: 27
status: low
date: 2026-10-23
---

# zonki (ZONKI) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zonki-sol)

---

## Audit Summary

The zonki token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. All third-party risk registry data was successfully retrieved and shows no adverse flags.

> **Final Recommendation:** Investors should monitor the high volume-to-liquidity ratio, as it may indicate artificial market activity rather than organic demand. Verify the current market price against the order book before executing large trades to mitigate slippage risks.

Since the mint and freeze authorities are revoked, the token supply is fixed and holder accounts cannot be frozen. No further on-chain action is required to secure the token's administrative state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are revoked.… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows 23.44% concentration among top holders. 7.6 External market data indicates $28,012 in liquidity, which is fully burned, ensuring 7.5 Governance and liquidity safety.… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL mint. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is static and cannot be altered by the… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 47.76, which significantly exceeds the 20 threshold, indicating a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; perform independent analysis of trade frequency and order book depth.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.1% of supply. Of that, 13.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.4% in wallets, 0.0% in other contracts. 1,024 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,024 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $36K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $36K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2hPYWv...pump`](https://solscan.io/account/2hPYWv4SydoBYmiecpqVi1AdTDSM4xeHbKeBDBQMpump) |
| **Network** | Solana |
| **Price** | $0.0001718 |
| **24h Volume** | $1.15M |
| **Liquidity** | $36.3K |
| **Volume / Liquidity** | 31.6× |
| **Token Age** | 6h |
| **Top-10 Holders** | 37.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12012 buys / 21214 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hqxwqv7ubzdj2fppxvvrokw8bykcg5rpje1aa1t5npem)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zonki-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
