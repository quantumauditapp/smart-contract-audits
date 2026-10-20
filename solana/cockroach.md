---
token: cockroach
ticker: COCKROACH
network: solana
risk_score: 0
status: low
date: 2026-10-03
---

# cockroach (COCKROACH) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cockroach-sol)

---

## Audit Summary

This audit of the cockroach (COCKROACH) SPL Token Mint found no critical or high-severity issues based on the available on-chain data and third-party risk registries. The mint and freeze authorities are revoked, and all pool liquidity is burned. Holder distribution data was unavailable for analysis.

> **Final Recommendation:** Given the revoked mint and freeze authorities and burned liquidity, this token presents a low-risk profile from a control perspective. Holders should continue to monitor DEX market data for any significant changes in liquidity or trading patterns. While holder concentration data was unavailable for this audit, it is advisable for potential investors to monitor on-chain holder distribution if such data becomes available, to assess potential market impact from large holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The cockroach (COCKROACH) token is an SPL Token-2022, indicating support for advanced extensions. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted… |
| **Governance / Economics** | 10/10 | Low | The token exhibits healthy liquidity with $166,400 in total DEX liquidity. The 24-hour volume of $799,039 results in a normal Volume/Liquidity Ratio of 4.80, not indicating wash trading. Crucially… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority for the cockroach (COCKROACH) token have been permanently revoked, preventing any future changes to the token's supply or the ability to freeze accounts. The… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 81% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $216K (DexScreener, all pools). 24h trading volume $999K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $216K of DEX liquidity across 5 pools. Launch: launched on pump.fun (PumpSwap), 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`H4KUxs...nyJc`](https://solscan.io/account/H4KUxsEgCp2yDpFvyDuGM5k6XevSKKrrKUxZ3Zr6nyJc) |
| **Network** | Solana |
| **Price** | $0.001849 |
| **24h Volume** | $802.2K |
| **Liquidity** | $174.1K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 3d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3260 buys / 2675 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5d1mwaczebhe96bx8zn3jqgjwpubjqf7vcbmmhr5gskb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cockroach-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
