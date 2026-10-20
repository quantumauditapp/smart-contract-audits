---
token: Super Intelligence
ticker: SI
network: solana
risk_score: 8
status: low
date: 2026-10-01
---

# Super Intelligence (SI) — Smart Contract Security Analysis | Solana

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/super-intelligence-sol-463d)

---

## Audit Summary

This audit of the Super Intelligence (SI) SPL Token Mint found no critical or high-severity issues based on the available on-chain data and deterministic rules. Key authorities like mint and freeze are revoked, and no risky Token-2022 extensions are active. However, data on holder concentration and pool liquidity locking status was unavailable, which prevents a complete assessment of economic risks.

> **Final Recommendation:** Given the unavailable data on holder concentration and pool liquidity locking, it is recommended to monitor these aspects closely. Verify on-chain that a significant portion of the liquidity is burned or locked for a substantial period. Additionally, observe the distribution of tokens among the top holders to assess potential market impact from large sell-offs.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | This token is implemented using the spl-token-2022 program, indicating adherence to modern Solana token standards. A significant strength is the revocation of both the mint authority and freeze… |
| **Governance / Economics** | 7/10 | Low | The token exhibits substantial DEX liquidity at $329,825, which supports active trading. The 24-hour volume is $2,842,994, with a Volume/Liquidity Ratio of 8.62, indicating a relatively active market… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's core parameters cannot be altered by an external key. The token's metadata is immutable, ensuring its name, symbol, and… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Super Intelligence (SI).

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $821K (DexScreener, all pools). 24h trading volume $26.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $22.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $821K of DEX liquidity across 16 pools. Launch: launched on pump.fun (PumpSwap), 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9aqmJj...aqjj`](https://solscan.io/account/9aqmJjCnnMQv42TXLk921ceUkN35nea2QP969n1caqjj) |
| **Network** | Solana |
| **Price** | $0.007059 |
| **24h Volume** | $2.81M |
| **Liquidity** | $339.0K |
| **Volume / Liquidity** | 8.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6086 buys / 4850 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/21bzhy2krovkgtyz8hfoetki2134mg2jywgc49uv5pyi)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/super-intelligence-sol-463d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
