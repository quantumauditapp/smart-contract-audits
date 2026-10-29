---
token: Houseworming
ticker: HOUSEWORM
network: solana
risk_score: 17
status: low
date: 2026-10-29
---

# Houseworming (HOUSEWORM) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/houseworming-sol)

---

## Audit Summary

The Houseworming (HOUSEWORM) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating rug-pull risks associated with creator withdrawals. Holder concentration data is currently unavailable, and the high volume-to-liquidity ratio suggests potential wash-trading activity.

> **Final Recommendation:** Investors should monitor the token's market activity, as the high volume-to-liquidity ratio may indicate artificial trading patterns. Since holder concentration data is unavailable, users should exercise caution regarding potential whale activity that could impact price stability.

Verify the current supply and authority status periodically using a block explorer to ensure no unexpected changes have occurred. Given the lack of holder distribution data, consider limiting exposure to a size that accounts for potential high slippage during periods of low liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are set to null.… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is supported by 100% of pool liquidity being burned, preventing creator withdrawal. 7.5 Governance is decentralized by the revocation of minting rights. However, 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints are immutable once authorities are revoked. 7.8 Operations are secure; metadata is immutable, and no upgradeable extensions are configured. The… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 24.01, exceeding the 20x threshold, which is a strong indicator of artificially inflated trade volume.

**Recommendation:** Monitor trading activity for organic volume and be aware that price action may not reflect genuine market demand.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $73K (DexScreener, all pools). 24h trading volume $1.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $73K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9Khzhy...pump`](https://solscan.io/account/9KhzhyM1BwgW6myZRcqdzQvemKjVrjck8kaevTkMpump) |
| **Network** | Solana |
| **Price** | $0.0007186 |
| **24h Volume** | $1.91M |
| **Liquidity** | $73.3K |
| **Volume / Liquidity** | 26.1× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 64201 buys / 22916 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5aw8omknbwwtecnwl2wwsca4bmaatvezoryc7eujjoat)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/houseworming-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
