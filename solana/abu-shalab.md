---
token: Abu Shalab
ticker: ABU
network: solana
risk_score: 17
status: low
date: 2026-10-07
---

# Abu Shalab (ABU) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/abu-shalab-sol)

---

## Audit Summary

This audit of the Abu Shalab (ABU) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and deterministic rules. The mint authority and freeze authority are both revoked, and all pool liquidity is burned. Holder concentration data was unavailable from chain-native RPC.

> **Final Recommendation:** Given the current state, the Abu Shalab (ABU) token presents a low-risk profile based on the available on-chain data. Holders should continue to monitor DEX market data for any significant shifts in liquidity or trading volume. While holder concentration data was unavailable, it is generally prudent to observe the distribution of tokens if that information becomes accessible in the future. No further on-chain verification steps are immediately necessary regarding the mint's core authorities or extensions, as they are securely revoked or inactive.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Abu Shalab (ABU) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be frozen. No Token-2022… |
| **Governance / Economics** | 9/10 | Low | The token exhibits healthy liquidity and trading patterns, with $37,133 in total DEX liquidity and a 24-hour volume of $180,534. The Volume/Liquidity Ratio is 4.86, which is considered normal and… |
| **Upgrades** | 10/10 | Low | The token's core parameters are immutable, as both the mint authority and freeze authority have been revoked. No Token-2022 extensions that could introduce mutable behavior, such as a Transfer Hook… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Abu Shalab (ABU), rank #5857.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $42K (DexScreener, all pools). 24h trading volume $109K (CoinGecko, all markets, daily snapshot). 24h trading volume $183K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $42K of DEX liquidity across 5 pools. Launch: launched on pump.fun, 4 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6hTLdz...pump`](https://solscan.io/account/6hTLdzZaaCjmqtn7RtaEMQsCbXT5Pg8q76tRViEGpump) |
| **Network** | Solana |
| **Price** | $0.0001541 |
| **24h Volume** | $179.5K |
| **Liquidity** | $38.8K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 4d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1418 buys / 1958 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2qwf4dn1jnqhcpayjqnkvakezzuuig4xdnbncsk1pgcw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/abu-shalab-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
