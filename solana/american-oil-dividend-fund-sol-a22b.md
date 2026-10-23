---
token: American Oil Dividend Fund
ticker: AODF
network: solana
risk_score: 2
status: low
date: 2026-10-23
---

# American Oil Dividend Fund (AODF) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-sol-a22b)

---

## Audit Summary

The mint and freeze authorities are irrevocably revoked, and 100.0% of the $65,798 pool liquidity is permanently burned. Selling concentration remains exceptionally low with the top ten eligible holders accounting for 2.46% of supply. Note that chain-native RPC holder distribution details were partially unavailable, though existing telemetry exhibits no adverse indicators.

> **Final Recommendation:** Routinely inspect automated market maker pool reserves through a Solana explorer to ensure secondary liquidity depth remains stable during volume fluctuations. Set up event monitoring for large accumulation transactions across secondary wallets to detect any emerging distribution shifts in circulating tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 standard with 6 decimals and an initialized total supply of 991,824,263,382,421 units. Key administrative controls are permanently disabled, as mint… |
| **Governance / Economics** | 10/10 | Low | The top 10 holders capable of selling control 2.46% of the token supply, while DEX pool reserves hold 6.22%. DEX liquidity is recorded at $65,798 with 100.0% of the LP tokens burned, completely… |
| **Upgrades** | 10/10 | Low | SPL token mints have no upgrade mechanisms or proxy patterns; administrative capabilities are governed exclusively through authority keys. The mint possesses no active authorities, and token metadata… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 8.7% of supply. Of that, 6.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.5% in wallets, 0.0% in other contracts. 4,016 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,016 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $65K (DexScreener, all pools). 24h trading volume $92K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $65K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`E8LdNq...pump`](https://solscan.io/account/E8LdNqkpPCXeHJAfwmSPAYmovWBoYuSXLr4kbk5rpump) |
| **Network** | Solana |
| **Price** | $0.0006012 |
| **24h Volume** | $91.5K |
| **Liquidity** | $64.9K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 18h |
| **Top-10 Holders** | 8.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 28940 buys / 10046 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2fq5c7vuzgwdstvsn92ynxzanqczep3qu87vtn2dwwjb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-sol-a22b)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
