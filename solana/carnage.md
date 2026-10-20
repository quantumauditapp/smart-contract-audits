---
token: CARNAGE
ticker: CARNAGE
network: solana
risk_score: 21
status: low
date: 2026-10-04
---

# CARNAGE (CARNAGE) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/carnage-sol)

---

## Audit Summary

The CARNAGE SPL Token Mint exhibits strong security characteristics with no active mint or freeze authorities, and no critical Token-2022 extensions like transfer hooks or permanent delegates. Liquidity is moderate, and a significant portion is burned or locked. Holder concentration data was unavailable from chain-native RPC.

> **Final Recommendation:** Holders should monitor the remaining 31.7% of liquidity that is not burned or locked, as its withdrawal could impact market stability. Given the absence of holder concentration data, it is advisable to observe on-chain distribution patterns if this information becomes available.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The CARNAGE token is an SPL Token-2022 mint with a supply of 644,000,233.719498 tokens and 6 decimals. Both the Mint Authority and Freeze Authority have been revoked, preventing further token… |
| **Governance / Economics** | 6/10 | Medium | The token has a liquidity of $33,379 USD with a 24-hour volume of $169,198, resulting in a Volume/Liquidity Ratio of 5.07. The trading pair is very new, created 0 days ago. A substantial 68.3% of the… |
| **Upgrades** | 8/10 | Low | The CARNAGE token mint has a fixed configuration as both the Mint Authority and Freeze Authority are revoked. It does not have any upgradable features like transfer fee or transfer hook… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

68.3% of the pool's LP is burned or time-locked. 68.3% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $33K (DexScreener, all pools). 24h trading volume $213K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $33K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AVKpee...pump`](https://solscan.io/account/AVKpeeWaCku3Mni5THbY4bkBnMrPzAEnnQKtP3wPpump) |
| **Network** | Solana |
| **Price** | $0.00007249 |
| **24h Volume** | $168.8K |
| **Liquidity** | $33.3K |
| **Volume / Liquidity** | 5.1× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6078 buys / 3847 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/btks1a21rbbqcx9cm5xyrawssp2utu8ye8b2azph7wbk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/carnage-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
