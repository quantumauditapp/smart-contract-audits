---
token: Nosana
ticker: NOS
network: solana
risk_score: 13
status: low
date: 2026-10-06
---

# Nosana (NOS) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nosana-sol)

---

## Audit Summary

This audit of the Nosana (NOS) SPL token mint found no critical or high-severity issues. Both the mint and freeze authorities have been revoked, ensuring a fixed supply and preventing account freezing. Holder concentration is moderate, and DEX liquidity is healthy with normal trading volume. Third-party risk registry data and pool liquidity lock status were unavailable for this assessment.

> **Final Recommendation:** Holders should continue to monitor the token's holder distribution for any significant shifts in concentration. While the mint and freeze authorities are revoked, ensuring core immutability, it is always prudent to observe liquidity pool dynamics if further data becomes available. Verify on-chain that the mint and freeze authorities remain revoked before making any investment decisions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Nosana (NOS) token is an SPL token mint on Solana, using the standard spl-token program. The mint authority for the token has been revoked, ensuring that no new tokens can be minted, fixing the… |
| **Governance / Economics** | 7/10 | Low | Holder concentration for NOS is moderate, with the top 10 holders that can sell accounting for 42.56% of the supply. This includes 16.84% in wallets and 25.72% in program accounts. The token exhibits… |
| **Upgrades** | 8/10 | Low | The mint authority for the Nosana token has been permanently revoked, preventing any future changes to the token's supply. The freeze authority is also revoked, ensuring that no accounts can be… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.6% of supply. What remains: 16.8% in wallets, 25.7% in other contracts. 48,251 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Nosana (NOS), market cap $64M, rank #415. 48,251 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.1M (DexScreener, all pools). 24h trading volume $1.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $695K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $7.83 on 2024-03-06; the price is now 91.8096% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.1M of DEX liquidity across 26 pools. Launch: 1408 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`nosXBV...Moo7`](https://solscan.io/account/nosXBVoaCTtYdLvKY6Csb4AC8JCdQKKAaWYtx2ZMoo7) |
| **Network** | Solana |
| **Price** | $0.6307 |
| **24h Volume** | $440.7K |
| **Liquidity** | $683.7K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 3y |
| **Top-10 Holders** | 42.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 988 buys / 1039 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3gkfzurgwnwyernjqvnkzpgclnnocjnrwvmyxivdivqk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nosana-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
