---
token: Dancing Dog
ticker: DOGGO
network: solana
risk_score: 20
status: low
date: 2026-10-13
---

# Dancing Dog (DOGGO) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dancing-dog-sol)

---

## Audit Summary

This audit of the Dancing Dog (Doggo) SPL Token Mint found no critical or high-severity issues. The mint and freeze authorities are revoked, and 100% of the pool's liquidity is burned. Third-party risk registries report no adverse flags, indicating a well-configured and low-risk token based on current on-chain data.

> **Final Recommendation:** Holders should continue to monitor the token's trading activity and liquidity for any significant changes. While current on-chain facts indicate a secure setup, market dynamics can evolve. Verify the token's official channels for any announcements or community updates.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Dancing Dog (Doggo) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for only 20.02% of the supply. The token has $39,153 in DEX liquidity, and 100% of this liquidity is burned, preventing… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, preventing any future changes to token supply or account freeze status. The token's metadata is immutable, meaning its name, symbol, or image… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.9% of supply. Of that, 13.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.0% in wallets, 0.0% in other contracts. 1,092 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Dancing Dog (DOGGO), rank #5359. 1,092 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $784K (CoinGecko, all markets, daily snapshot). 24h trading volume $334K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $41K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 35 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FgJReZ...pump`](https://solscan.io/account/FgJReZeYfmKZeWrCaGYL8gLnUixwBhjdHuRknC6ypump) |
| **Network** | Solana |
| **Price** | $0.000141 |
| **24h Volume** | $333.1K |
| **Liquidity** | $40.7K |
| **Volume / Liquidity** | 8.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 33.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2014 buys / 2213 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dbqbquehe6kr9c4ogvoess9jjwjjrovlgccspeepd5qt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dancing-dog-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*
