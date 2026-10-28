---
token: ChimpX AI
ticker: $CHIMP
network: solana
risk_score: 15
status: low
date: 2026-10-28
---

# ChimpX AI ($CHIMP) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chimpx-ai-sol)

---

## Audit Summary

The ChimpX AI token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating risks of rug pulls. Holder distribution data was unavailable, and third-party registries flagged high holder correlation, which may indicate potential concentration risks.

> **Final Recommendation:** Investors should monitor the token's holder distribution once on-chain data becomes available to assess the impact of the flagged high holder correlation. Given the lack of transparency in current holder concentration, position sizing should be conservative.

Verify the mint and freeze authority status periodically via block explorers to ensure no unexpected state changes occur. As the token is new, ensure all trades are executed through reputable DEX interfaces to avoid potential routing issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the standard spl-token program (7.1 Architecture). Access control is robust as both mint and freeze authorities are set to null (7.3 Access Control). No advanced extensions like… |
| **Governance / Economics** | 9/10 | Low | Liquidity is healthy at $27,925 with a stable volume-to-liquidity ratio of 1.87 (7.4 Economic). 100% of pool liquidity is burned, ensuring it cannot be withdrawn (7.5 Governance). While holder… |
| **Upgrades** | 10/10 | Low | The token mint is immutable (7.7 Upgrades). Metadata is not mutable, preventing branding changes post-launch. There are no upgradeable components or proxy patterns in the SPL token standard. |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — High Holder Correlation Flagged  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by a small group of related wallets.

**Recommendation:** Monitor on-chain holder distribution once data becomes available to evaluate the risk of coordinated sell-offs.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $25K (DexScreener, all pools). 24h trading volume $57K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $25K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AHKcbf...g6Xb`](https://solscan.io/account/AHKcbfroL4aYLcmK6iPwYJieGYUZZmeB917FZYjbg6Xb) |
| **Network** | Solana |
| **Price** | $0.00009712 |
| **24h Volume** | $48.4K |
| **Liquidity** | $24.8K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 10h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 327 buys / 265 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7egjpe2ciqzy4c2keakyuh7ktgopafceshjgdz39qzqq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chimpx-ai-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
