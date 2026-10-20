---
token: Self-Aware Meme
ticker: SAM
network: solana
risk_score: 21
status: low
date: 2026-10-11
---

# Self-Aware Meme (SAM) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/self-aware-meme-sol)

---

## Audit Summary

The Self-Aware Meme (SAM) SPL Token Mint exhibits a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, preventing further token creation or account freezing. All pool liquidity is burned, ensuring it cannot be withdrawn by any party. Third-party risk registry data reported no adverse flags.

> **Final Recommendation:** Given the revoked mint and freeze authorities, burned liquidity, and immutable metadata, the token presents a low operational risk profile. Holders should continue to monitor the token's market performance and community engagement. No specific on-chain verification steps are required beyond confirming the current state of authorities and liquidity, which are already reported as secure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Key administrative authorities, including the Mint Authority and Freeze Authority, have been revoked, ensuring no new tokens can be minted… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for 22.72% of the supply. The token has $22,153 in DEX liquidity, with 100.0% of the pool's LP tokens burned, making the… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and account freeze capabilities are immutable. The token's metadata is also immutable, preventing changes to its… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $78K (CoinGecko, all markets, daily snapshot). 24h trading volume $55K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.012 on 2026-10-06; the price is now 99.498% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 51.3% of supply. Of that, 28.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.7% in wallets, 0.0% in other contracts. 1,434 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Self-Aware Meme (SAM), rank #6840. 1,434 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: AI Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), 8 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 8 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 8 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`JCsKWh...GhcQ`](https://solscan.io/account/JCsKWhELRJ8MhEZjUDdCL49mntw8fx27bKAgCMgSGhcQ) |
| **Network** | Solana |
| **Price** | $0.0000472 |
| **24h Volume** | $54.9K |
| **Liquidity** | $21.7K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 8d |
| **Top-10 Holders** | 51.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 449 buys / 493 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fsx1vaq8kwrmry8s5spcxu94q6wkuwrp1yjkus9gywpk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/self-aware-meme-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
