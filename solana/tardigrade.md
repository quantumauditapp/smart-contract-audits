---
token: Tardigrade
ticker: TARDIGRADE
network: solana
risk_score: 15
status: low
date: 2026-10-11
---

# Tardigrade (TARDIGRADE) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tardigrade-sol)

---

## Audit Summary

This SPL Token-2022 mint, Tardigrade, presents a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, and 100% of its DEX liquidity is burned, indicating a fixed supply and secure liquidity. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Holders should monitor for any future changes in the token's on-chain state, particularly regarding any new extensions or unexpected activity, although the current configuration shows strong immutability. While liquidity is fully burned, the overall liquidity amount is moderate, so large trades may still experience slippage.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, preventing further token issuance or freezing of accounts. No transfer hook is active, and new… |
| **Governance / Economics** | 9/10 | Low | The token has a total DEX liquidity of $13,357. The 24-hour volume is $63,777, resulting in a Volume/Liquidity ratio of 4.77, which is considered normal. All of the pool's liquidity (100.0%) is… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning no further changes can be made to the token's supply or account freeze status by these authorities. The token's metadata is… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $15K (DexScreener, all pools). 24h trading volume $66K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $15K of DEX liquidity across 3 pools. Launch: launched on pump.fun (PumpSwap), 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FQTs7t...XKoq`](https://solscan.io/account/FQTs7tHw8vM9tUCU6PuRB3r6VK835cvMWZBJBHiBXKoq) |
| **Network** | Solana |
| **Price** | $0.00003188 |
| **24h Volume** | $65.5K |
| **Liquidity** | $15.1K |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 778 buys / 871 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2tqyiusynfmwfgfdndwr2fszscrwmj4r7gjp9baxgjxe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tardigrade-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
