---
token: Arcades
ticker: ARCADES
network: solana
risk_score: 22
status: low
date: 2026-10-15
---

# Arcades (ARCADES) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/arcades-sol)

---

## Audit Summary

This audit of the Arcades (ARCADES) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. The mint authority and freeze authority are revoked, and liquidity is fully locked. Third-party registry data reported no adverse flags, and key Token-2022 extensions are not active. Sources succeeded for chain-native RPC (mint state), on-chain security registry, third-party risk registry, and DEX market data.

> **Final Recommendation:** Given the current state, no immediate critical actions are required. Holders should continue to monitor the token's trading activity and liquidity for any significant changes. Verify on-chain that the mint and freeze authorities remain revoked to ensure the supply and transferability are fixed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Arcades token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, preventing further token creation or account freezing. There is no transfer hook… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding 23.80% of the supply. Total DEX liquidity is $18,494, and 100.0% of the pool's LP tokens are burned, ensuring liquidity… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's core parameters cannot be altered by an administrative key. No Token-2022 extensions like transfer hooks or default… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 45.6% of supply. Of that, 21.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.8% in wallets, 0.0% in other contracts. 639 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Arcades (ARCADES), rank #6719. 639 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $157K (CoinGecko, all markets, daily snapshot). 24h trading volume $181K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 4 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`jq4yKh...pump`](https://solscan.io/account/jq4yKhqGNzWCQhgQYB89CDEYQYjLHGcvDy9WNJHpump) |
| **Network** | Solana |
| **Price** | $0.00004771 |
| **24h Volume** | $181.0K |
| **Liquidity** | $18.4K |
| **Volume / Liquidity** | 9.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | 45.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1575 buys / 1768 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7unbbhwbpamyaaupvajqkbvuy3ayzvwerviqjrudh5om)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/arcades-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
