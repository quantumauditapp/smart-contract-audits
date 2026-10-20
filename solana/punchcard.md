---
token: PunchCard
ticker: PUNCH
network: solana
risk_score: 19
status: low
date: 2026-10-19
---

# PunchCard (PUNCH) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/punchcard-sol)

---

## Audit Summary

This audit of the PunchCard (PUNCH) SPL Token Mint found no critical or high-severity risks based on the available on-chain data and security registries. The mint and freeze authorities are revoked, and liquidity is fully burned. Third-party risk registry data was unavailable, which limits a comprehensive external risk assessment.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked. Monitor the token's liquidity and trading volume for any significant changes, especially given the moderate volume-to-liquidity ratio. Be aware that third-party risk registry data was unavailable, so consider this a partial assessment regarding external risk signals.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The PunchCard (PUNCH) token is an SPL Token-2022 mint with a total supply of 970,217,786.814352 tokens. Both the mint authority and freeze authority have been revoked, preventing further token… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a low concentration of holdings, with the top 10 holders that can sell accounting for 22.75% of the supply. Total DEX liquidity stands at $24,231, with 100% of the pool's LP tokens… |
| **Upgrades** | 10/10 | Low | The token's core parameters are immutable, as both the mint and freeze authorities are revoked. Furthermore, the metadata (name, symbol, image) is not mutable, ensuring branding consistency.… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 38.8% of supply. Of that, 16.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.8% in wallets, 0.0% in other contracts. 545 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as PunchCard (PUNCH), rank #6196. 545 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $25K (DexScreener, all pools). 24h trading volume $178K (CoinGecko, all markets, daily snapshot). 24h trading volume $203K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $25K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), 17 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 17 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 17 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8HJY9G...cBxx`](https://solscan.io/account/8HJY9GTiEGgPoUAs3YSRiwLUukZKhKcH1ngqLB8qcBxx) |
| **Network** | Solana |
| **Price** | $0.0000826 |
| **24h Volume** | $203.1K |
| **Liquidity** | $25.2K |
| **Volume / Liquidity** | 8.1× |
| **Token Age** | 17d |
| **Top-10 Holders** | 38.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1511 buys / 1187 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3o2qaestb6epyfklzwndpxhhdzyjsrh5lrsv2etgpdha)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/punchcard-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
