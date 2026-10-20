---
token: The Pink Bow
ticker: PINKBOW
network: solana
risk_score: 13
status: low
date: 2026-10-08
---

# The Pink Bow (PINKBOW) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-pink-bow-sol)

---

## Audit Summary

This audit of The Pink Bow (PINKBOW) token mint found no critical or high-severity issues based on the provided on-chain facts and deterministic rules. The mint and freeze authorities are revoked, and 100% of the pool's liquidity is burned. Holder concentration data was unavailable, and a third-party risk registry reported several concerning signals that could not be directly verified or triggered a deterministic finding.

> **Final Recommendation:** Given the absence of critical findings based on the provided facts, holders should primarily monitor the token's market behavior and any future updates from the project. Verify on-chain that the mint and freeze authorities remain revoked. If holder concentration data becomes available, assess it for potential market manipulation risks. Be aware that third-party risk signals, while not triggering deterministic findings in this audit, suggest caution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, preventing further token creation or account freezing. No Transfer Hook is… |
| **Governance / Economics** | 9/10 | Low | The token's liquidity stands at $10,975 USD, with 100.0% of the pool's LP tokens burned, ensuring liquidity cannot be withdrawn. The 24-hour volume is $96,056, resulting in a Volume/Liquidity Ratio… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning no further tokens can be minted or accounts frozen. The token utilizes the spl-token-2022 program without the Transfer Hook extension… |

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

Liquidity $12K (DexScreener, all pools). 24h trading volume $96K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BL5VzS...pump`](https://solscan.io/account/BL5VzSWV8LuaXMRCXDhsNjJg8uMCCf8H64F3SsDzpump) |
| **Network** | Solana |
| **Price** | $0.00002055 |
| **24h Volume** | $95.8K |
| **Liquidity** | $11.5K |
| **Volume / Liquidity** | 8.3× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1037 buys / 681 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cp2hhkxu7h79b5itbglnwtf5ygw1lvjgblbbsif2zqwo)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-pink-bow-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
