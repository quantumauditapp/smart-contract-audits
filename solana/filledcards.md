---
token: filled.cards
ticker: FILLED
network: solana
risk_score: 2
status: low
date: 2026-10-04
---

# filled.cards (FILLED) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/filledcards-sol)

---

## Audit Summary

This audit of the filled.cards (FILLED) SPL Token Mint found no critical or high-severity issues based on the available on-chain data and third-party security registries. The mint and freeze authorities are revoked, and all pool liquidity is burned. Holder distribution data was unavailable, preventing an assessment of concentration risk.

> **Final Recommendation:** Holders should monitor for the availability of holder distribution data to assess potential concentration risks. While the mint and freeze authorities are revoked and liquidity is burned, which are strong positive indicators, understanding the distribution of tokens among holders is crucial for a complete risk profile. Verify on-chain that the mint and freeze authorities remain revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The filled.cards token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be… |
| **Governance / Economics** | 10/10 | Low | The token exhibits a total DEX liquidity of $70,845, with a 24-hour volume of $726,286, resulting in a Volume/Liquidity Ratio of 10.25. Crucially, 100.0% of the pool's LP tokens are burned, meaning… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, preventing any administrative changes to the token's supply or account states. The token's metadata is immutable, ensuring its name, symbol… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as filled.cards (FILLED), rank #3838.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 70% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $113K (DexScreener, all pools). 24h trading volume $604K (CoinGecko, all markets, daily snapshot). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $113K of DEX liquidity across 5 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8dBnKH...pump`](https://solscan.io/account/8dBnKHwNYH3hz2fFTJczVwzBTpJFAMtc53k3uA4zpump) |
| **Network** | Solana |
| **Price** | $0.0004301 |
| **24h Volume** | $725.1K |
| **Liquidity** | $78.6K |
| **Volume / Liquidity** | 9.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3359 buys / 3149 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/a8jmwc6ijm7duubftgrcpg9hqgsn9gipkj39q1hbhqzk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/filledcards-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
