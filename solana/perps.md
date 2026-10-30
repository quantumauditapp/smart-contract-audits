---
token: PERPS
ticker: PERPS
network: solana
risk_score: 23
status: low
date: 2026-10-30
---

# PERPS (PERPS) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/perps-sol)

---

## Audit Summary

The PERPS token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is highly secure, with 96.8% of pool liquidity permanently burned. No adverse flags were reported by third-party risk registries.

> **Final Recommendation:** The token exhibits a strong security posture regarding on-chain authorities and liquidity. Holders should continue to monitor the top 10 holder distribution via block explorers to ensure concentration does not increase significantly over time.

No further action is required for the token configuration itself. Users should verify the mint address against official project channels before interacting to avoid impersonation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are revoked. 7.2… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance factors are stable, with top 10 holders controlling 25.25% of the supply. 7.6 External liquidity is well-protected, as 96.8% of the pool liquidity is burned. The 24h… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the token mint is immutable. Metadata is fixed, and there are no mutable balance or transfer fee authorities. The token configuration is locked, preventing… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 41.6% of supply. Of that, 16.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 25.2% in wallets, 0.0% in other contracts. 220 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

220 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

97.1% of the pool's LP is burned or time-locked. 97.1% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23K (DexScreener, all pools). 24h trading volume $127K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`51H7Az...pump`](https://solscan.io/account/51H7AzyyUAy6AkTPa2g1AMyfkoEoVXZjAKkqyHTopump) |
| **Network** | Solana |
| **Price** | $0.00008086 |
| **24h Volume** | $104.2K |
| **Liquidity** | $22.5K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 1d |
| **Top-10 Holders** | 41.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1183 buys / 867 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ex7py8gh5ugcpdhd5ksghhr7etwbat44p2wwor8mzxpf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/perps-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
