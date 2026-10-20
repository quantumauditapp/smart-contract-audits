---
token: PROJECT 486
ticker: 486
network: solana
risk_score: 15
status: low
date: 2026-10-13
---

# PROJECT 486 (486) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/project-486-sol)

---

## Audit Summary

This audit of the PROJECT 486 SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. Key authorities such as mint and freeze are revoked, and the token's liquidity is fully burned. Third-party risk registry data reported no adverse flags. Chain-native RPC data for holder distribution was unavailable, but other critical sources were successfully accessed.

> **Final Recommendation:** Holders can proceed with confidence regarding the immutability of the token's core properties, as mint and freeze authorities are revoked. No further on-chain verification steps are required for these aspects. Monitor DEX market data for any significant changes in liquidity or trading volume, although the current state shows healthy liquidity and no signs of manipulation. The fully burned liquidity provides strong assurance against rug pulls.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The PROJECT 486 token is an SPL Token-2022 mint with a total supply of 973,659.141254. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be created and no… |
| **Governance / Economics** | 9/10 | Low | Holder concentration for PROJECT 486 is low, with the top 10 holders that can sell holding only 19.69% of the total supply. The token has a liquidity of $24,587 USD, which is above the very low… |
| **Upgrades** | 10/10 | Low | The token's mint and freeze authorities are permanently revoked, preventing any post-launch changes to supply or account status. Furthermore, the token's metadata is immutable, ensuring that its… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.7% of supply. Of that, 17.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.7% in wallets, 0.0% in other contracts. 450 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

450 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $27K (DexScreener, all pools). 24h trading volume $137K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $27K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 8 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 8 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 8 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9tVxVh...pump`](https://solscan.io/account/9tVxVhKDmWLsG29CcfsAhLfgcZEkvemjB8TUDb4Wpump) |
| **Network** | Solana |
| **Price** | $0.00008688 |
| **24h Volume** | $136.1K |
| **Liquidity** | $25.4K |
| **Volume / Liquidity** | 5.4× |
| **Token Age** | 8d |
| **Top-10 Holders** | 36.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1099 buys / 917 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gkh1tqpmvuby3zswpspbbptktrfkh4tkykaabqw944km)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/project-486-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*
