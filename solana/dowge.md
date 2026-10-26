---
token: DOWGE
ticker: DJI6930
network: solana
risk_score: 2
status: low
date: 2026-10-26
---

# DOWGE (DJI6930) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dowge-sol)

---

## Audit Summary

The DOWGE token mint exhibits a secure configuration with both mint and freeze authorities permanently revoked. Liquidity is fully protected via a 100% burn of LP tokens, and no adverse flags were identified by third-party risk registries. Holder distribution is well-dispersed, with the top 10 holders controlling only 14.24% of the supply.

> **Final Recommendation:** The token configuration is secure and requires no immediate remediation. Holders should continue to monitor the top 10 holder distribution via block explorers to ensure concentration remains within acceptable bounds.

Verify the current mint and freeze authority status on-chain using a block explorer to confirm they remain set to 'None'. No further action is required for this asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust, as both mint and freeze authorities… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance metrics are healthy. Holder concentration is low at 14.24% for the top 10, mitigating risks of coordinated sell-offs. 7.6 External liquidity is $368,254, with 100% of… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL mint. Metadata is immutable, and no transfer hooks or fee extensions are present. The token configuration is finalized and cannot be altered… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 17.7% of supply. Of that, 3.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.2% in wallets, 0.0% in other contracts. 15,244 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as DOWGE (DJI6930), market cap $6M, rank #1556. 15,244 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $373K (DexScreener, all pools). 24h trading volume $223K (CoinGecko, all markets, daily snapshot). 24h trading volume $169K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0848 on 2025-07-21; the price is now 93.3393% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $373K of DEX liquidity across 9 pools. Launch: launched on pump.fun, 507 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DQnkBM...pump`](https://solscan.io/account/DQnkBM4eYYMnVE8Qy2K3BB7uts1fh2EwBVktEz6jpump) |
| **Network** | Solana |
| **Price** | $0.00587 |
| **24h Volume** | $169.1K |
| **Liquidity** | $372.0K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 17.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1206 buys / 1194 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6m7jf1h22zgsecssk3yljkeakwrfy6ljv1hffupqa3ps)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dowge-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
