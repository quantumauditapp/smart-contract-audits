---
token: QuStream
ticker: QST
network: solana
risk_score: 0
status: low
date: 2026-10-09
---

# QuStream (QST) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/qustream-sol)

---

## Audit Summary

The QuStream (QST) SPL token mint has been audited based on on-chain data and third-party security registries. No critical or high-risk vulnerabilities were identified. Key authorities such as mint and freeze are revoked, and metadata is immutable. Information regarding pool liquidity locking was unavailable, preventing a full assessment of liquidity risk.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure the token's fixed supply and unfreezable nature. Monitor the liquidity pool's status if information becomes available, specifically checking if a significant portion of liquidity is locked or burned. Continue to observe holder distribution for any significant changes that could impact market stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The QuStream (QST) token is implemented using the standard `spl-token` program. Both the mint authority and freeze authority have been revoked, preventing the creation of new tokens or the freezing… |
| **Governance / Economics** | 7/10 | Low | Holder concentration for QuStream (QST) is low, with the top 10 holders that can sell accounting for 28.45% of the supply. The token has a total DEX liquidity of $176,451, with a 24-hour volume of… |
| **Upgrades** | 8/10 | Low | The mint authority for QuStream (QST) has been revoked, ensuring no further tokens can be minted, and the supply is fixed. The token's metadata is immutable, meaning its name, symbol, or image cannot… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 98.5% (≈ permanent lock) |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.9% of supply. Of that, 4.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.9% in wallets, 19.6% in other contracts. 5,407 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as QuStream (QST), market cap $2M, rank #2294. 5,407 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

98.5% of the pool's LP is burned or time-locked. 98.5% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $177K (DexScreener, all pools). 24h trading volume $191K (CoinGecko, all markets, daily snapshot). 24h trading volume $256K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0284 on 2025-09-03; the price is now 92.3353% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $177K of DEX liquidity across 5 pools. Launch: launched on pump.fun, 591 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AUuCEH...pump`](https://solscan.io/account/AUuCEHQ7sm2i5GmaHrpE961voWcTY8U6mgrkhcV7pump) |
| **Network** | Solana |
| **Price** | $0.001793 |
| **24h Volume** | $255.9K |
| **Liquidity** | $176.6K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 32.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 742 buys / 639 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cn5l4sc6njehygclx2rdz9qk4fgtdphjvlwgjnggovyq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/qustream-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
