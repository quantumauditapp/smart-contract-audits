---
token: unpooled
ticker: UNPOOLED
network: solana
risk_score: 20
status: low
date: 2026-11-03
---

# unpooled (UNPOOLED) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/unpooled-sol)

---

## Audit Summary

The unpooled (UNPOOLED) token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data is currently unavailable from on-chain sources.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may not reflect organic market demand. Monitor the token on block explorers to ensure no unexpected changes occur in the token's metadata or extension state, although the current configuration is immutable.

Verify the current circulating supply and holder distribution via a block explorer to ensure that the lack of concentration data does not mask significant whale activity. Do not rely solely on DEX volume metrics for valuation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active extensions like transfer hooks or default frozen states. 7.1 Architecture is standard for SPL tokens, and 7.3 Access Control is robust as… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show $15,919 in liquidity, which is fully burned and inaccessible to any creator. 7.5 Governance is decentralized due to the lack of mint authority. However, 7.6 External market… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints do not support proxy-based logic updates. Metadata is immutable, and extension settings such as transfer fees are not upgradable. The token configuration… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 58.46, exceeding the 20x threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Perform independent analysis of trade history to distinguish between organic volume and automated wash trading before committing capital.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 12 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FxQ5Gb...pump`](https://solscan.io/account/FxQ5GbqCBxNHDpFTpiL9RDVHiP58ar5nMkR3eMwepump) |
| **Network** | Solana |
| **Price** | $0.00002936 |
| **24h Volume** | $925.7K |
| **Liquidity** | $13.1K |
| **Volume / Liquidity** | 70.5× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12107 buys / 9293 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/e1fm1y9d6hnxt9ftehkaurkjaeejby42dfzv39axczds)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/unpooled-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
