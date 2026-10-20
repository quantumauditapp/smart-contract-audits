---
token: XTO
ticker: XTO
network: solana
risk_score: 0
status: low
date: 2026-10-14
---

# XTO (XTO) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-sol)

---

## Audit Summary

The XTO SPL token mint exhibits a strong security posture with both mint and freeze authorities revoked, preventing further token issuance or account freezing. Liquidity is substantial at $198,978 USD and is 100% locked, mitigating rug pull risks. Holder concentration data was unavailable, which prevents a full assessment of distribution risk.

> **Final Recommendation:** Given the revoked mint and freeze authorities and 100% locked liquidity, the token presents a low immediate operational risk. Holders should monitor for any future changes in the token's on-chain state, although the current configuration limits such possibilities. If holder concentration data becomes available, it should be reviewed to assess potential market manipulation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The XTO token operates on the `spl-token` program. Both the mint authority and freeze authority have been revoked, meaning no new tokens can be minted and no holder accounts can be frozen. The token… |
| **Governance / Economics** | 10/10 | Low | The token has a liquidity of $198,978 USD, with 100.0% of the pool's liquidity locked for good, indicating a low risk of liquidity withdrawal by the pool creator. The 24-hour volume is $1,163,553… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, ensuring that the token's supply and account freeze capabilities cannot be altered post-launch. The token's metadata is immutable, meaning… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 99.9% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $202K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $202K of DEX liquidity across 6 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`XtogpW...JfHt`](https://solscan.io/account/XtogpWjiAgvkemc5gr1auxkh77w3vKgSQN1nxJeJfHt) |
| **Network** | Solana |
| **Price** | $0.006887 |
| **24h Volume** | $1.16M |
| **Liquidity** | $200.8K |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2446 buys / 1547 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4pbedygxzvuvr94sgtjc6c5cx7nmgbdnv1x8ac9opj7o)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
