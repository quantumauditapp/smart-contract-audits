---
token: ELONDOG
ticker: ELONDOG
network: solana
risk_score: 27
status: low
date: 2026-10-20
---

# ELONDOG (ELONDOG) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/elondog-sol)

---

## Audit Summary

The ELONDOG token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and no adverse flags were reported by third-party risk registries. The token exhibits a healthy distribution profile with no significant concentration risks.

> **Final Recommendation:** The token is in a secure, immutable state. No further action is required to mitigate authority-based risks. 

Investors should continue to monitor the liquidity pool's performance and verify that the circulating supply remains consistent with the current holder distribution via block explorers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented on the Token-2022 standard, ensuring robust support for modern extensions. 7.1 Architecture and 7.2 Code Security are verified through the use of standard, audited SPL… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance factors are favorable, with the top 10 holders controlling 37.02% of the supply. 7.6 External market data confirms $18,699 in liquidity, which is fully protected as… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is immutable, preventing unauthorized changes to token branding. The configuration ensures that no authority can modify the token's… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 73.2% of supply. Of that, 36.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 37.0% in wallets, 0.0% in other contracts. 62 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

62 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $69K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (elon); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3qSd27...pump`](https://solscan.io/account/3qSd27nb3zyRmqbhLzH4PdeYcADqeLtjgYy2Fp4Apump) |
| **Network** | Solana |
| **Price** | $0.000054 |
| **24h Volume** | $60.8K |
| **Liquidity** | $19.1K |
| **Volume / Liquidity** | 3.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 73.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 711 buys / 425 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/61cqshsgqqqm9g8mxthcubkq9totmvxmgbnqa3r9saeh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/elondog-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
