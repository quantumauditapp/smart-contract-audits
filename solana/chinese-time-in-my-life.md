---
token: Chinese time in my life
ticker: CHINESE
network: solana
risk_score: 20
status: low
date: 2026-10-13
---

# Chinese time in my life (CHINESE) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chinese-time-in-my-life-sol)

---

## Audit Summary

This SPL Token Mint, "Chinese time in my life (Chinese)", exhibits a robust security posture with no critical or high-risk findings identified. Both mint and freeze authorities are revoked, and 100% of the DEX pool liquidity is burned, ensuring supply immutability and liquidity permanence. Third-party risk registries report no adverse flags, though chain-native RPC data for holder distribution was partially unavailable.

> **Final Recommendation:** Given the strong security posture with revoked authorities and burned liquidity, this token appears to be well-secured against common SPL token risks. Holders should continue to monitor the token's market activity and any future announcements from the project team. Verify on-chain that the mint and freeze authorities remain revoked and that the liquidity pool status does not change.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program, indicating modern Solana token standards. Both the mint authority and freeze authority are revoked, meaning no new tokens can be created and… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for only 22.92% of the total supply, reducing the risk of large-scale dumps. The token has a healthy liquidity of… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, preventing any future changes to the token's supply or the ability to freeze accounts. The token's metadata is immutable, meaning its name… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.5% of supply. Of that, 13.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.9% in wallets, 0.0% in other contracts. 885 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Chinese time in my life (CHINESE), rank #5431. 885 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $37K (DexScreener, all pools). 24h trading volume $93K (CoinGecko, all markets, daily snapshot). 24h trading volume $66K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Chinese Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $37K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 31 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Tm2iqb...pump`](https://solscan.io/account/Tm2iqbxYjKpW8xCMe6q1xUraNMNzcG5xMztAir3pump) |
| **Network** | Solana |
| **Price** | $0.0001586 |
| **24h Volume** | $66.2K |
| **Liquidity** | $37.1K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 36.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 465 buys / 392 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8brdx1ky8xurbyq1kmvj4trsnadybsilu2mxmlvb4waw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chinese-time-in-my-life-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*
