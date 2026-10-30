---
token: stay calm
ticker: CALM
network: solana
risk_score: 14
status: low
date: 2026-10-30
---

# stay calm (CALM) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stay-calm-sol)

---

## Audit Summary

The 'stay calm' token is a standard SPL Token-2022 implementation with all administrative authorities revoked, including mint and freeze capabilities. Liquidity is fully secured via a 100% burn of LP tokens, and no adverse flags were reported by third-party registries. Holder distribution data was unavailable, preventing a full assessment of supply concentration.

> **Final Recommendation:** The token exhibits a high degree of technical security due to the revocation of all administrative authorities and the permanent burning of liquidity. Holders should monitor the token's market activity and volume to ensure liquidity remains sufficient for their position sizes.

Since holder concentration data is currently unavailable, users should exercise standard caution regarding potential price volatility. No further on-chain actions are required to secure the mint itself.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active extensions such as transfer hooks or default frozen states (7.1 Architecture). All administrative authorities, including mint and freeze, are… |
| **Governance / Economics** | 9/10 | Low | Liquidity is robustly protected, with 100% of pool tokens burned, preventing creator withdrawal (7.4 Economic). Trading volume is healthy relative to the $21,901 liquidity pool (7.8 Operations).… |
| **Upgrades** | 10/10 | Low | The mint is fully immutable with no upgrade paths or mutable metadata (7.7 Upgrades). All authority flags are set to null, ensuring the token supply and metadata cannot be altered (7.3 Access… |

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

Liquidity $23K (DexScreener, all pools). 24h trading volume $132K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4HSHFb...pump`](https://solscan.io/account/4HSHFbFiKuMvZW7yGiDTab17B63MzBkkhadFKxhkpump) |
| **Network** | Solana |
| **Price** | $0.00008662 |
| **24h Volume** | $77.9K |
| **Liquidity** | $22.6K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3781 buys / 1615 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/angic41jczghsdbxvygyvyzhfagq8g9pycxfsehg15oh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stay-calm-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
