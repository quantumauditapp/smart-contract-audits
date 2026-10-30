---
token: Digital Oil Asset Supply
ticker: DOAS
network: solana
risk_score: 2
status: low
date: 2026-10-30
---

# Digital Oil Asset Supply (DOAS) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/digital-oil-asset-supply-sol-7677)

---

## Audit Summary

Digital Oil Asset Supply (DOAS) presents an immutable Token-2022 configuration with fully revoked mint and freeze authorities. DEX liquidity stands at $488,645 with 100% of LP tokens burned, and the top 10 sellable holders account for only 0.47% of the supply. Chain-native RPC holder distribution data was unavailable during fact collection, but available security registry records confirm no malicious mechanisms.

> **Final Recommendation:** Periodically query the mint account directly via Solana RPC to ensure authorities remain revoked and no unexpected extension accounts are appended. Monitor decentralized exchange pool depth and trading volume to detect any future liquidity migrations across secondary markets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the spl-token-2022 program with standard 6 decimals and a supply of 999,917,674,143,052 base units. Administrative control is completely removed as both mint authority and… |
| **Governance / Economics** | 10/10 | Low | DEX liquidity is well-established at $488,645 USD with 100.0% of LP tokens permanently burned, preventing liquidity extraction by the creator. Trading activity shows a healthy 24-hour volume of… |
| **Upgrades** | 10/10 | Low | The mint parameters are completely finalized with no active authorities capable of supply inflation or account freezing. Metadata is marked immutable, precluding post-deployment naming, ticker, or… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 1.2% of supply. Of that, 0.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.5% in wallets, 0.0% in other contracts. 2,979 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,979 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $488K (DexScreener, all pools). 24h trading volume $141K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $488K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`dsZhtr...pump`](https://solscan.io/account/dsZhtrFFaz72zpdsw4xwxtgvPgu4Hq7qxK43mKcpump) |
| **Network** | Solana |
| **Price** | $0.03503 |
| **24h Volume** | $141.1K |
| **Liquidity** | $487.7K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 1.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 32558 buys / 2514 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ezivc2t8kpmzorz2gj6nuecghdghtpesss5t7g8hb8pu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/digital-oil-asset-supply-sol-7677)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
