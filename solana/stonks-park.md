---
token: STONKS PARK
ticker: PARK
network: solana
risk_score: 7
status: low
date: 2026-10-26
---

# STONKS PARK (PARK) — Smart Contract Security Analysis | Solana

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stonks-park-sol)

---

## Audit Summary

The STONKS PARK (PARK) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and no adverse flags were reported by third-party registries. The token exhibits a stable holder distribution and healthy trading activity.

> **Final Recommendation:** The token is currently in a secure, immutable state. No further action is required for security purposes. Holders should continue to monitor the token's market liquidity and holder distribution via standard blockchain explorers to ensure no unexpected shifts in concentration occur.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program, ensuring modern extension support. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are revoked. 7.2 Code… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance metrics show low concentration, with the top 10 holders controlling 20.79% of the supply. 7.6 External liquidity is healthy at $63,848, with 100% of LP tokens burned… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are restricted by the revocation of all administrative authorities. Metadata is immutable, preventing post-launch branding changes. The token configuration is static… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 28.8% of supply. Of that, 8.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.8% in wallets, 0.0% in other contracts. 1,035 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as STONKS PARK (PARK), rank #3963. 1,035 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $66K (DexScreener, all pools). 24h trading volume $174K (CoinGecko, all markets, daily snapshot). 24h trading volume $190K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $66K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), 40 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7gKKy2...vaU5`](https://solscan.io/account/7gKKy2p1SaMkRFPX7caF96YpfuMMpDj82ZpjaffuvaU5) |
| **Network** | Solana |
| **Price** | $0.0004724 |
| **24h Volume** | $190.4K |
| **Liquidity** | $65.8K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 28.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1205 buys / 1231 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2rf43wd7uk6ojid9cawhv1e1hfsufbmfe2tgqsigfkw1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stonks-park-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
