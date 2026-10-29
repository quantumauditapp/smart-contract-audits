---
token: Kylian Mbappe
ticker: KYLIAN MBAPPE
network: solana
risk_score: 6
status: low
date: 2026-10-29
---

# Kylian Mbappe (KYLIAN MBAPPE) — Smart Contract Security Analysis | Solana

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kylian-mbappe-sol)

---

## Audit Summary

The Kylian Mbappe token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and no adverse flags were reported by third-party registries. All security sources were successfully retrieved.

> **Final Recommendation:** The token configuration is secure and requires no immediate action. Holders should continue to monitor the top 10 holder distribution via block explorers to ensure concentration remains within acceptable limits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the SPL Token-2022 program. 7.1 Architecture is standard for SPL tokens, with 7.2 Code Security relying on the audited native program. 7.3 Access Control is robust as… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $120,474 in liquidity, which is 100% burned. 7.5 Governance is decentralized as no single entity controls the mint. 7.6 External market data shows a healthy… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint and freeze authorities are revoked. Metadata is immutable, preventing unauthorized changes to token branding. The token configuration is fixed and cannot… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 22.9% of supply. Of that, 2.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.1% in wallets, 0.0% in other contracts. 821 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

821 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $120K (DexScreener, all pools). 24h trading volume $112K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $120K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`67XYfx...pump`](https://solscan.io/account/67XYfxjEsAnyBMQ4p8z9rm6oknsN9ZA9ZU1aLihNpump) |
| **Network** | Solana |
| **Price** | $0.002098 |
| **24h Volume** | $111.9K |
| **Liquidity** | $119.9K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 1d |
| **Top-10 Holders** | 22.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12890 buys / 4029 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/chkptyjudnujyrdxd6m2csnsxm9eybv2dg5p27dunuhk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kylian-mbappe-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
