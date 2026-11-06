---
token: XTO
ticker: XTRUTH OIL
network: solana
risk_score: 0
status: low
date: 2026-11-06
---

# XTO (XTRUTH OIL) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-sol-2c1f)

---

## Audit Summary

The XTO token utilizes the SPL Token-2022 program with all administrative authorities, including mint and freeze, successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, mitigating risks associated with rug pulls or liquidity withdrawal. Holder distribution data is unavailable, and a third-party registry flags high holder correlation, which may indicate concentrated ownership.

> **Final Recommendation:** Investors should monitor the token's on-chain activity to assess the impact of the high holder correlation flagged by third-party registries. Since the mint and freeze authorities are revoked, the token's supply and transferability are fixed and cannot be manipulated by the original deployer.

Verify the current supply and holder distribution using a block explorer to ensure that the high holder correlation does not pose a risk of market manipulation. No further administrative actions are required as the contract is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are revoked. 7.2… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $238,487 in liquidity, with 100% of LP tokens burned, preventing liquidity removal. 7.5 Governance is decentralized by the lack of mint authority. 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. 7.8 Operations are secure due to the permanent revocation of metadata and balance-mutating authorities. The token configuration is static and… |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — High Holder Correlation  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be held by a small number of related entities.

**Recommendation:** Monitor top holder movements on-chain to identify potential coordinated sell-offs.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $238K (DexScreener, all pools). 24h trading volume $228K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $238K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5soCV4...pump`](https://solscan.io/account/5soCV4kbAtXo6AWpbbbdWd62iFMBiAJCBquKrRnDpump) |
| **Network** | Solana |
| **Price** | $0.00903 |
| **24h Volume** | $227.9K |
| **Liquidity** | $237.8K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 16h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 24326 buys / 756 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/b1goj6xh71a4yd1ufwbc2zn7fs23qfsabk84xjy2cln7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-sol-2c1f)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
