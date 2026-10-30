---
token: locked inu
ticker: INU
network: solana
risk_score: 13
status: low
date: 2026-10-30
---

# locked inu (INU) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/locked-inu-sol)

---

## Audit Summary

The token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully locked, mitigating risks of rug-pulls via liquidity withdrawal. Third-party registry data indicates single-holder ownership, though holder distribution data was unavailable for verification.

> **Final Recommendation:** Investors should monitor the 'single holder' signal identified by the third-party registry, as this may indicate high concentration risk despite the lack of on-chain distribution data. Verify the current holder distribution using block explorers to assess the impact of this concentration on market volatility.

Since liquidity is fully locked, the primary risk remains market-driven price action rather than protocol-level manipulation. Ensure all future interactions are conducted through verified DEX interfaces to avoid malicious swap routing.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic stability is supported by 100% locked liquidity, preventing creator withdrawal. 7.5 Governance is centralized according to third-party registry signals, though specific holder… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints do not utilize proxy patterns. 7.8 Operations are secure as metadata is immutable and authority-related extensions are not upgradable. The token… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Single Holder Ownership  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry flags the token as having single-holder ownership, which may lead to significant price manipulation or liquidity crunches.

**Recommendation:** Monitor on-chain holder distribution to assess the concentration of supply and potential impact on market liquidity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $57K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Gztz15...qvK1`](https://solscan.io/account/Gztz15EVRR9GyBVcVQy2aCpX5JhY5SsUtoW1G1M5qvK1) |
| **Network** | Solana |
| **Price** | $0.00005408 |
| **24h Volume** | $57.2K |
| **Liquidity** | $13.0K |
| **Volume / Liquidity** | 4.4× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 342 buys / 264 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cq1q84oxsukvemn1gawgfnydgnk8mdfbfufs44eyqynk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/locked-inu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
