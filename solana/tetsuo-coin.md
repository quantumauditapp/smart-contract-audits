---
token: Tetsuo Coin
ticker: TETSUO
network: solana
risk_score: 0
status: low
date: 2026-10-10
---

# Tetsuo Coin (TETSUO) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tetsuo-coin-sol)

---

## Audit Summary

The Tetsuo Coin (TETSUO) SPL token mint exhibits a robust security posture based on available on-chain data. Both the mint and freeze authorities are permanently revoked, preventing further token issuance or account freezing. Holder concentration is low, and DEX liquidity is moderate with normal trading patterns. Specific details regarding the locking of pool liquidity were not fully available from all sources.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked. While current data indicates a secure configuration, continuous monitoring of DEX liquidity and trading volume is advisable. Be aware that specific details on pool liquidity locking were not fully available and should be independently confirmed if this is a critical factor for investment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the standard `spl-token` program. Key authorities, including the mint authority and freeze authority, are both revoked, ensuring no new tokens can be minted and no… |
| **Governance / Economics** | 7/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding only 11.24% of the total supply. The token has moderate DEX liquidity of $167,343 USD, with a 24-hour volume of $56,351 USD… |
| **Upgrades** | 8/10 | Low | The token's core parameters are immutable due to the revocation of both mint and freeze authorities. The metadata is also immutable, meaning the token name, symbol, or image cannot be changed… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $171K (DexScreener, all pools). 24h trading volume $50K (CoinGecko, all markets, daily snapshot). 24h trading volume $56K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0646 on 2025-01-11; the price is now 99.6628% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 49.6% of supply. Of that, 38.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.2% in wallets, 0.0% in other contracts. 13,349 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Tetsuo Coin (TETSUO), rank #4774. 13,349 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.9% of the pool's LP is burned or time-locked. 99.9% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $171K of DEX liquidity across 15 pools. Launch: 677 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8i51XN...9tE8`](https://solscan.io/account/8i51XNNpGaKaj4G4nDdmQh95v4FKAxw8mhtaRoKd9tE8) |
| **Network** | Solana |
| **Price** | $0.0002182 |
| **24h Volume** | $56.0K |
| **Liquidity** | $167.2K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 49.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 463 buys / 457 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2kb3i5ulkhucjuwq3poxhpuggqbwywttk5eg9e5wnlg6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tetsuo-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
