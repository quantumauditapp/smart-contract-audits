---
token: American Dividend Protocol
ticker: ADP
network: solana
risk_score: 0
status: low
date: 2026-11-07
---

# American Dividend Protocol (ADP) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-dividend-protocol-sol-fb32)

---

## Audit Summary

The American Dividend Protocol (ADP) token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating rug-pull risks associated with creator withdrawals. Holder distribution data is currently unavailable, and a third-party registry flags high holder correlation, which may indicate potential concentration risks.

> **Final Recommendation:** Investors should monitor the token's holder distribution as it becomes available to assess the impact of the flagged high holder correlation. Since the mint and freeze authorities are revoked, the token's supply and transfer mechanics are fixed and cannot be altered by the original deployer.

Verify the current liquidity pool status on-chain to confirm the burn transaction. Users should exercise caution regarding the high holder correlation signal by observing market depth and price impact before executing large trades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 10/10 | Low | Liquidity is robust at $260,427 with 100% of LP tokens burned, preventing creator withdrawal (7.4 Economic). Trading activity shows a healthy volume/liquidity ratio of 0.62 (7.6 External). Holder… |
| **Upgrades** | 10/10 | Low | The mint is immutable with metadata and authority settings locked (7.7 Upgrades). There are no upgradeable components or proxy patterns present (7.8 Operations). The token configuration is static and… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by a small number of entities.

**Recommendation:** Monitor on-chain holder distribution once data becomes available to identify potential concentration risks.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $259K (DexScreener, all pools). 24h trading volume $159K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $259K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9cE1m9...pump`](https://solscan.io/account/9cE1m9UhUULcBdb1gFwanMTAmnCwiK5PyPM54Wcpump) |
| **Network** | Solana |
| **Price** | $0.01075 |
| **24h Volume** | $159.4K |
| **Liquidity** | $259.4K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 27763 buys / 699 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/94fnc55datwtamqc54mzv2mkyz5yynqvxoblj2pdwfqh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-dividend-protocol-sol-fb32)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
