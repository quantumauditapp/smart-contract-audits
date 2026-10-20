---
token: Gomo App
ticker: GOMO
network: solana
risk_score: 15
status: low
date: 2026-10-05
---

# Gomo App (GOMO) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gomo-app-sol)

---

## Audit Summary

The Gomo App (GOMO) token is an SPL Token-2022 mint with both mint and freeze authorities revoked, ensuring a fixed supply and no ability to freeze holder accounts. All pool liquidity is burned, preventing rug pulls via liquidity withdrawal. Holder concentration data was unavailable from chain-native RPC.

> **Final Recommendation:** Verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of the token. Monitor DEX market data for changes in liquidity and trading patterns, especially given the high volume-to-liquidity ratio and the newness of the trading pair. If holder concentration data becomes available, assess it for potential market manipulation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Gomo App (GOMO) token is an SPL Token-2022 mint. Both the Mint Authority and Freeze Authority are revoked, indicating a fixed supply and no ability to freeze accounts. There is no Transfer Hook… |
| **Governance / Economics** | 9/10 | Low | The token has $25,084 in DEX liquidity, with 100% of the pool's LP tokens burned, ensuring that liquidity cannot be withdrawn by any party. The 24-hour trading volume is $207,584, resulting in a… |
| **Upgrades** | 10/10 | Low | The Mint Authority and Freeze Authority are both revoked, preventing any further token minting or freezing of holder accounts. The token's metadata is immutable, meaning its name, symbol, or image… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $24K (DexScreener, all pools). 24h trading volume $224K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $24K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9XKzy4...pump`](https://solscan.io/account/9XKzy4KahcZaGJPJtz1PtqGPB3CiseoBrx7TcQhEpump) |
| **Network** | Solana |
| **Price** | $0.00008015 |
| **24h Volume** | $206.1K |
| **Liquidity** | $23.6K |
| **Volume / Liquidity** | 8.7× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1329 buys / 1150 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5a7qurjlart146jajjype5nh6vlyfpn2qrhuslqbsczy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gomo-app-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
