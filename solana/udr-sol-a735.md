---
token: UDR
ticker: UDR
network: solana
risk_score: 0
status: low
date: 2026-10-22
---

# UDR (UDR) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/udr-sol-a735)

---

## Audit Summary

The UDR token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully secured via 100% burning of LP tokens, mitigating risks of rug pulls. Holder distribution data was unavailable, preventing a full assessment of concentration risks.

> **Final Recommendation:** The token is technically sound with no active administrative authorities. Users should monitor the token on-chain using block explorers to verify that no new authorities have been introduced if the token program were to support future extensions.

Given the lack of holder distribution data, investors should exercise caution regarding potential concentration and perform their own due diligence on the top holder accounts before committing significant capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or complex extensions… |
| **Governance / Economics** | 10/10 | Low | Liquidity is highly secure with 100% of LP tokens burned, preventing withdrawal by the creator (7.4 Economic). The volume/liquidity ratio of 0.54 indicates healthy, non-wash-traded activity (7.6… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). All authority flags are set to null, ensuring no future administrative changes can be made to the mint or… |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — Holder Distribution Data Unavailable  *(Severity: Low · Status: Unresolved)*

The current on-chain data does not provide the distribution of token holdings among the top accounts.

**Recommendation:** Monitor the top holder accounts via block explorers to identify potential concentration risks before trading.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $721K (DexScreener, all pools). 24h trading volume $391K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $721K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AHd33G...pump`](https://solscan.io/account/AHd33GVtEEngDGYvZHWqsQe5q43T2weW4gFrk1Tpump) |
| **Network** | Solana |
| **Price** | $0.07164 |
| **24h Volume** | $391.4K |
| **Liquidity** | $721.3K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 27180 buys / 628 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/j1tu7c5yelg8tfvjmf6vwkpjhyyucazynwekgqnfkkr9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/udr-sol-a735)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
