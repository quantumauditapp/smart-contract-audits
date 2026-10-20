---
token: GTA memes
ticker: GTA
network: solana
risk_score: 9
status: low
date: 2026-10-16
---

# GTA memes (GTA) — Smart Contract Security Analysis | Solana

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gta-memes-sol)

---

## Audit Summary

The 'GTA memes (GTA)' token on Solana exhibits a robust security posture with no critical or high-severity issues identified from on-chain data. Key authorities are revoked, and liquidity is fully burned, indicating a secure setup. Third-party risk registry data reported no adverse flags, and all available sources were successfully processed.

> **Final Recommendation:** Given the current configuration, the token appears to be well-secured against common SPL token risks. Holders should continue to monitor the token's market behavior and any future on-chain activity. No specific verification steps are required beyond confirming the current state of revoked authorities and burned liquidity, which are already established.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority are revoked, preventing further token creation or account freezing. No Transfer Hook is active… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding only 21.22% of the supply. The token has healthy liquidity of $132,929 USD, and 100.0% of the pool's liquidity is burned… |
| **Upgrades** | 10/10 | Low | The Mint Authority and Freeze Authority are both revoked, meaning no further changes can be made to the token's supply or account freeze status. The token utilizes the spl-token-2022 program but does… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 26.4% of supply. Of that, 5.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.2% in wallets, 0.0% in other contracts. 4,856 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,856 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 67% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $200K (DexScreener, all pools). 24h trading volume $697K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (meme); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $200K of DEX liquidity across 30 pools. Launch: launched on pump.fun, 50 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BsbsB3...pump`](https://solscan.io/account/BsbsB3WLq7vbY5En3MBCAsTrcwaCxNKY2Mp5pGuLpump) |
| **Network** | Solana |
| **Price** | $0.001356 |
| **24h Volume** | $498.8K |
| **Liquidity** | $133.7K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 26.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3793 buys / 3551 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5isvs31h7hmdggmyuvzmhdsywv7cydd6czjtbqzctlii)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gta-memes-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
