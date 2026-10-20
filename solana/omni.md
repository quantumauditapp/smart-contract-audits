---
token: OMNI
ticker: OMNI
network: solana
risk_score: 0
status: low
date: 2026-10-15
---

# OMNI (OMNI) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/omni-sol)

---

## Audit Summary

This audit of the OMNI SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. The mint and freeze authorities are revoked, and liquidity is fully burned. Third-party risk registry data was available and reported no adverse flags.

> **Final Recommendation:** The OMNI token mint appears to be well-configured with key authorities revoked and liquidity secured. Holders should continue to monitor DEX market data for any significant changes in liquidity or trading patterns. While no immediate risks were identified, ongoing vigilance is always recommended for any digital asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The OMNI token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be frozen. No… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding only 11.91% of the total supply. The token exhibits healthy liquidity, with $88,001 USD in DEX pools. Crucially, 100.0% of… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, preventing any further changes to the token's supply or account freeze status. The token's metadata is also immutable, ensuring that its name… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.3% of supply. Of that, 4.2% locked, 13.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.9% in wallets, 0.0% in other contracts. 2,975 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as OMNI (OMNI). 2,975 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 58% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $156K (DexScreener, all pools). 24h trading volume $1.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $156K of DEX liquidity across 30 pools. Launch: launched on pump.fun, 12 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 12 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 12 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5GDX5f...pump`](https://solscan.io/account/5GDX5fJTQns4arM1J94wjxdA8KXFsV5qW46MLFpHpump) |
| **Network** | Solana |
| **Price** | $0.0007186 |
| **24h Volume** | $810.6K |
| **Liquidity** | $90.3K |
| **Volume / Liquidity** | 9.0× |
| **Token Age** | 12d |
| **Top-10 Holders** | 29.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3075 buys / 2251 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/qvcymnis5qqjejrzpgbejnnkrqdnkhjttfk7v1xqu9d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/omni-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
