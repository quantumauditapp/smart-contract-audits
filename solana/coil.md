---
token: COIL
ticker: COIL
network: solana
risk_score: 27
status: low
date: 2026-10-24
---

# COIL (COIL) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coil-sol)

---

## Audit Summary

The COIL token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. No adverse flags were reported by third-party registries.

> **Final Recommendation:** Investors should monitor the high volume-to-liquidity ratio, as it may indicate artificial market activity rather than organic demand. Given the lack of administrative control, the token's supply and transfer mechanics are fixed and cannot be altered by the original deployer.

Verify the current holder distribution via block explorers to ensure no single entity holds a majority stake that could impact market stability. No further on-chain action is required to secure the token, as all critical authorities have been renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program, ensuring modern extension support. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are revoked. 7.2 Code… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows 25.37% concentration among the top 10 holders. 7.6 External market data indicates $31,449 in liquidity, which is fully burned, preventing rug pulls. However, the 26.07… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints are immutable once authorities are revoked. 7.8 Operations are secure, as metadata is immutable and no upgradeable extensions are present. |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 26.07, exceeding the threshold of 20, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; perform independent analysis of trade frequency and order book depth.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.1% of supply. Of that, 16.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 25.4% in wallets, 0.0% in other contracts. 730 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

730 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $30K (DexScreener, all pools). 24h trading volume $763K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30K of DEX liquidity across 30 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Bdmz1B...pump`](https://solscan.io/account/Bdmz1BAj5B2YbYVdMyZexWbjX33kfhNonHGDtQjipump) |
| **Network** | Solana |
| **Price** | $0.0001265 |
| **24h Volume** | $744.6K |
| **Liquidity** | $29.9K |
| **Volume / Liquidity** | 24.9× |
| **Token Age** | 3d |
| **Top-10 Holders** | 42.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11579 buys / 7853 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bdfcdxti8jfckiohtytkcbfy2axemmqouv6j9bolj2kj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coil-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
