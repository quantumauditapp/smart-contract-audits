---
token: ChickPot
ticker: CHICKPOT
network: solana
risk_score: 15
status: low
date: 2026-11-04
---

# ChickPot (CHICKPOT) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chickpot-sol)

---

## Audit Summary

The ChickPot token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully burned, ensuring the pool cannot be drained by the creator. However, the high volume-to-liquidity ratio suggests potential wash trading activity, and holder concentration data is currently unavailable.

> **Final Recommendation:** Investors should monitor the token's market activity, as the high volume-to-liquidity ratio may indicate artificial trading patterns. Since holder concentration data is unavailable, users should exercise caution regarding potential whale activity that could impact price stability.

Verify the current mint and freeze authority status on-chain using a block explorer to ensure they remain set to null. No further administrative actions are required for the token contract itself.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the audited… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is supported by 100% burned liquidity, preventing rug-pulls via withdrawal. 7.5 Governance is decentralized due to authority revocation. 7.6 External market data indicates a… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints are immutable once initialized. Metadata is immutable as per the fact block. No further administrative changes can be made to the token's core… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 21.40, exceeding the threshold of 20, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; perform independent analysis of trade frequency and order book depth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $88K (DexScreener, all pools). 24h trading volume $1.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $88K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8B6ZZA...pump`](https://solscan.io/account/8B6ZZAC2FQ7AJrZPz7veXJrod5t2MG1C5MZBLNbUpump) |
| **Network** | Solana |
| **Price** | $0.001059 |
| **24h Volume** | $1.90M |
| **Liquidity** | $87.7K |
| **Volume / Liquidity** | 21.6× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16329 buys / 13938 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4japu7rxq26g4a56uqy73n3faef5uzypv7nx28hwuckv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chickpot-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
