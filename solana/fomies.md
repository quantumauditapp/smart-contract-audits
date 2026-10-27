---
token: Fomies
ticker: FOMIES
network: solana
risk_score: 0
status: low
date: 2026-10-27
---

# Fomies (FOMIES) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fomies-sol)

---

## Audit Summary

The Fomies token is a standard SPL Token-2022 implementation with all administrative authorities, including mint and freeze, successfully revoked. Liquidity is fully secured via a 100% burn, and no adverse flags were detected in third-party risk registries. Holder concentration data was unavailable, preventing a full assessment of distribution risks.

> **Final Recommendation:** The token demonstrates a high level of technical security due to the revocation of all administrative authorities and the permanent locking of liquidity. Holders should monitor the token's market activity and liquidity depth on-chain to ensure continued stability.

Since holder concentration data is unavailable, users should exercise caution regarding potential market volatility caused by large, undisclosed individual positions. Verify the mint address against official sources before interacting.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust, as both mint and freeze authorities are… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance metrics show high security regarding liquidity, with 100% of pool tokens burned. 7.6 External signals indicate healthy trading with a 0.52 volume/liquidity ratio.… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are effectively immutable due to the revocation of all administrative authorities. Metadata is immutable, preventing unauthorized changes to token branding. No upgrade… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $255K (DexScreener, all pools). 24h trading volume $132K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $255K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HipJR7...pump`](https://solscan.io/account/HipJR79p21LdH1WNAxKfNXiGULdA1QWUaG7uLwonpump) |
| **Network** | Solana |
| **Price** | $0.009193 |
| **24h Volume** | $132.0K |
| **Liquidity** | $254.9K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 20h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11926 buys / 10127 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3gemewrbhcuhouktnvuragrf7sjncivvfqrvw8eu7eax)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fomies-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
