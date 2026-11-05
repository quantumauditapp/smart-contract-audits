---
token: XTO
ticker: XTO
network: solana
risk_score: 0
status: low
date: 2026-11-05
---

# XTO (XTO) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-sol-e11a)

---

## Audit Summary

The XTO token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating risks of rug pulls. Holder distribution data is unavailable, and third-party registries flag high holder correlation, which may indicate potential concentration risks.

> **Final Recommendation:** Investors should monitor the token's holder distribution via block explorers as data becomes available to assess potential concentration risks. Given the high holder correlation flagged by third-party registries, exercise caution regarding potential coordinated market movements.

Verify the current supply and authority status directly on-chain using a block explorer to confirm the revoked status of mint and freeze authorities before executing large trades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring supply immutability and preventing account freezing (7.3 Access Control). No… |
| **Governance / Economics** | 10/10 | Low | Liquidity is robust at $198,009 with 100% of LP tokens burned, preventing creator withdrawal (7.4 Economic). Trading volume is healthy relative to liquidity, suggesting normal market activity (7.8… |
| **Upgrades** | 10/10 | Low | The mint is immutable with no upgrade paths for metadata or transfer logic (7.7 Upgrades). Metadata is non-mutable, preventing branding changes post-launch (7.6 External). |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

Third-party risk registries have flagged the token for high holder correlation, which may indicate that a significant portion of the supply is controlled by a small number of entities.

**Recommendation:** Monitor on-chain holder distribution to identify potential concentration risks and evaluate the impact of large wallet movements on market stability.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $198K (DexScreener, all pools). 24h trading volume $327K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $198K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CuLwxY...pump`](https://solscan.io/account/CuLwxYSGRfcV4vmNcDEFzTHQTNHA6BfKSzRpYYQapump) |
| **Network** | Solana |
| **Price** | $0.006223 |
| **24h Volume** | $326.7K |
| **Liquidity** | $197.5K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12986 buys / 8668 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bmdzr6hyldxxendgguvbtwjx73sycssbvguvhpqzwuhd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-sol-e11a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
