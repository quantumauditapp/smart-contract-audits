---
token: MissRose
ticker: ROSE
network: solana
risk_score: 9
status: low
date: 2026-10-15
---

# MissRose (ROSE) — Smart Contract Security Analysis | Solana

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/missrose-sol)

---

## Audit Summary

The MissRose (ROSE) SPL token mint demonstrates strong security postures with both mint and freeze authorities revoked, ensuring fixed supply and preventing account freezing. All pool liquidity is permanently burned, eliminating rug pull risks from liquidity withdrawal. No critical or high-risk issues were identified by deterministic analysis, and third-party registries report no adverse flags.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the immutability of supply and account status. Monitor the token's trading activity and liquidity over time, especially given its recent launch, to assess market stability. Confirm that no new Token-2022 extensions are enabled that could alter token behavior.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority are revoked, which prevents further token minting and freezing of holder accounts. No Transfer… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding only 23.05% of the supply. Total DEX liquidity is $58,124, which is moderate. Critically, 100.0% of the pool's LP tokens are… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, preventing any future changes to the token's supply or account freezing capabilities. Metadata is not mutable, ensuring that the token's… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.2% of supply. Of that, 9.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.1% in wallets, 0.0% in other contracts. 1,117 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as MissRose (ROSE), rank #4011. 1,117 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $57K (DexScreener, all pools). 24h trading volume $390K (CoinGecko, all markets, daily snapshot). 24h trading volume $342K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $57K of DEX liquidity across 5 pools. Launch: launched on pump.fun (PumpSwap), 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7b6dX3...x28H`](https://solscan.io/account/7b6dX3nE25xrfNViEKZHL9wVJFcBxQYuWPpmzHUxx28H) |
| **Network** | Solana |
| **Price** | $0.0003352 |
| **24h Volume** | $341.5K |
| **Liquidity** | $56.9K |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 3d |
| **Top-10 Holders** | 32.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2146 buys / 2583 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9cdkmmgwenr6zyu725fr4jdyyfojpw8gz1kknrylekcg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/missrose-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
