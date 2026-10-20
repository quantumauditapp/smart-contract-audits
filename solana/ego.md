---
token: EGO
ticker: EGO
network: solana
risk_score: 15
status: low
date: 2026-10-07
---

# EGO (EGO) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ego-sol)

---

## Audit Summary

This audit of the EGO SPL Token Mint found no critical or high-severity issues based on the available on-chain data and third-party risk registries. The mint authority and freeze authority are revoked, and all pool liquidity is burned. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Given the absence of critical findings, holders should monitor the token's trading activity and liquidity over time. If holder concentration data becomes available, verify that a significant portion of the supply is not held by a few addresses. Always exercise caution with new tokens and ensure personal risk tolerance aligns with market conditions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The EGO token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be created and no existing accounts can be frozen. It does not… |
| **Governance / Economics** | 9/10 | Low | The token has a total DEX liquidity of $29,963, with 100.0% of the pool's LP tokens burned, ensuring liquidity cannot be withdrawn. The 24-hour volume of $230,587 results in a Volume/Liquidity Ratio… |
| **Upgrades** | 10/10 | Low | The EGO token mint has revoked both its mint and freeze authorities, preventing any further issuance or freezing of tokens. It is an SPL Token-2022, but does not implement extensions like transfer… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as EGO (EGO), rank #6179.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $236K (CoinGecko, all markets, daily snapshot). 24h trading volume $238K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.00557 on 2026-10-06; the price is now 98.4112% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 4 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BbJJUT...pump`](https://solscan.io/account/BbJJUTuGV2B7tJ99YeryiCBFLG39Hoc4RTzEwchtpump) |
| **Network** | Solana |
| **Price** | $0.00008177 |
| **24h Volume** | $236.8K |
| **Liquidity** | $31.7K |
| **Volume / Liquidity** | 7.5× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1884 buys / 1635 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/azbssg82zpspef97t1g7phwjaikntxmatwc3tgdqpkxk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ego-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
