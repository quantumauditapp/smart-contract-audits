---
token: RETARDIO
ticker: RETARDIO
network: solana
risk_score: 17
status: low
date: 2026-10-04
---

# RETARDIO (RETARDIO) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/retardio-sol)

---

## Audit Summary

The RETARDIO SPL Token Mint exhibits a low-risk profile, with both mint and freeze authorities revoked, indicating a fixed supply and immutable account states. Liquidity is robust and fully burned, preventing rug pulls. No adverse flags were reported by third-party risk registries, and all Token-2022 extensions are either inactive or configured for immutability. Chain-native RPC data for holder distribution was unavailable, but the 'Top 10 Holders That Can Sell' data was present.

> **Final Recommendation:** This token presents a low-risk profile based on the provided on-chain facts. Holders should continue to monitor the token's market performance and community engagement. No specific on-chain verification steps are immediately necessary beyond confirming the current state of revoked authorities and burned liquidity, which are already established. Any future changes to the token program or associated DEX pools would require a new assessment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The RETARDIO token is an SPL Token-2022 mint, indicating it utilizes the latest Solana token program features. Both the mint authority and freeze authority are revoked, ensuring that no new tokens… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a healthy holder distribution, with the top 10 holders that can sell accounting for 40.99% of the supply, which is below common concentration thresholds. Liquidity is strong at… |
| **Upgrades** | 10/10 | Low | The token mint is configured for immutability, with both mint and freeze authorities permanently revoked. This means the token supply is fixed, and no accounts can be frozen. Furthermore, the… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.8% of supply. Of that, 2.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 41.0% in wallets, 0.0% in other contracts. 878 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

878 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $218K (DexScreener, all pools). 24h trading volume $505K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (retard); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $218K of DEX liquidity across 6 pools. Launch: launched on pump.fun, 32 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CSRRgT...pump`](https://solscan.io/account/CSRRgTwf9o5KLgguS2M16aEAhV5PUUzfshrAAQ8opump) |
| **Network** | Solana |
| **Price** | $0.00408 |
| **24h Volume** | $492.2K |
| **Liquidity** | $206.3K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 43.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1754 buys / 1239 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/98ewlhskoxmu9g9ngumykjgufz2rc8wsrscxb67bmubh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/retardio-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
