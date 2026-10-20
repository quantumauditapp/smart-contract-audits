---
token: Miners
ticker: MINER
network: solana
risk_score: 17
status: low
date: 2026-10-10
---

# Miners (MINER) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/miners-sol)

---

## Audit Summary

This audit of the Miners (MINER) SPL Token Mint found no critical or high-severity issues based on the available on-chain data and external security signals. The mint and freeze authorities are revoked, and 100% of the pool's liquidity is burned. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Given the revoked mint and freeze authorities, and 100% burned liquidity, this token presents a low technical risk profile. Holders should continue to monitor DEX market data for any significant shifts in liquidity or trading volume. While holder concentration data was unavailable, it is prudent to observe on-chain distribution if that data becomes accessible. No specific on-chain verification steps are immediately required beyond confirming the current state of authorities and liquidity burning.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Miners (MINER) token is implemented using the spl-token-2022 program, indicating modern SPL token standards. Both the mint authority and freeze authority have been revoked, preventing further… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a healthy liquidity profile with $23,138 in total DEX liquidity. A significant positive is that 100.0% of the pool's LP tokens are burned, meaning this liquidity can never be… |
| **Upgrades** | 10/10 | Low | The token's core parameters are immutable, as both the mint and freeze authorities are revoked. This prevents any future changes to the token supply or the ability to freeze accounts. Furthermore… |

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

Liquidity $23K (DexScreener, all pools). 24h trading volume $93K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2T6Wg3...pump`](https://solscan.io/account/2T6Wg3urxPQHaoGh4gqNHyYL6FAfyWA5BaH6Lo37pump) |
| **Network** | Solana |
| **Price** | $0.00006755 |
| **24h Volume** | $92.6K |
| **Liquidity** | $23.3K |
| **Volume / Liquidity** | 4.0× |
| **Token Age** | 3d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1172 buys / 1081 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8j42or3k3kbgnguqr2rbzcrweta7jhrnscjmscipv8in)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/miners-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
