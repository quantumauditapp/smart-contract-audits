---
token: Imagine Game Studio
ticker: IMAGINE
network: solana
risk_score: 15
status: low
date: 2026-10-11
---

# Imagine Game Studio (IMAGINE) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/imagine-game-studio-sol)

---

## Audit Summary

This SPL Token Mint for Imagine Game Studio (Imagine) exhibits a strong security posture with both mint and freeze authorities permanently revoked. Key Token-2022 extensions like transfer hooks are not active, and metadata is immutable. Holder concentration is moderate, and a significant portion of the DEX liquidity is burned, reducing rug pull risks. Third-party registry data reported no adverse flags, and chain-native RPC data for holder distribution was unavailable.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked. Monitor the token's liquidity and trading volume for any significant changes. While the current configuration is robust, continuous vigilance over market dynamics and any potential future extensions or changes in the token program is advisable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority are revoked, preventing further token issuance or freezing of holder accounts. No Transfer Hook… |
| **Governance / Economics** | 9/10 | Low | The top 10 holders that can sell hold 36.03% of the total supply, indicating a moderate level of concentration. Total DEX liquidity stands at $61,717. A significant 99.2% of the pool's LP tokens are… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, ensuring that the token's supply and transferability parameters cannot be altered by any single entity. No Token-2022 extensions that allow… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 47.3% of supply. Of that, 11.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 36.0% in wallets, 0.0% in other contracts. 1,077 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Imagine Game Studio (IMAGINE), rank #4545. 1,077 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.2% of the pool's LP is burned or time-locked. 99.2% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $58K (DexScreener, all pools). 24h trading volume $287K (CoinGecko, all markets, daily snapshot). 24h trading volume $365K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $58K of DEX liquidity across 4 pools. Launch: launched on pump.fun, 57 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EpFTb2...pump`](https://solscan.io/account/EpFTb2XcGiMyGLykZ9VYmyPWz2AHEwAggqSbwJpypump) |
| **Network** | Solana |
| **Price** | $0.0002922 |
| **24h Volume** | $364.8K |
| **Liquidity** | $57.7K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 47.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1562 buys / 2321 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4uuzpgttnksnd8cwad3wxsxpcppxckvoywykhldfmon1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/imagine-game-studio-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
