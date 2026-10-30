---
token: United Dividend Trust Fund
ticker: UDTF
network: solana
risk_score: 0
status: low
date: 2026-10-30
---

# United Dividend Trust Fund (UDTF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-sol-b37f)

---

## Audit Summary

The United Dividend Trust Fund (UDTF) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and there are no active transfer hooks or mutable metadata risks. While a third-party registry flags high holder correlation, the on-chain configuration demonstrates a high degree of decentralization and security.

> **Final Recommendation:** The token exhibits a strong security posture with no critical or high-severity findings. Holders should continue to monitor the third-party registry for updates regarding holder correlation, though the current on-chain state provides no mechanism for the developer to manipulate balances or freeze assets.

Verify the current supply and authority status periodically using a block explorer to ensure that no unexpected state changes have occurred, although the current revocation status is permanent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are set to null.… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance metrics are stable, with top 10 holders controlling only 0.93% of the supply. 7.6 External liquidity is healthy at $332,589, with 100% of the pool's LP tokens… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not utilize proxy patterns. The token metadata and balance-mutating authorities are immutable, preventing post-launch changes to the token's core… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — High Holder Correlation Flag  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be held by related entities.

**Recommendation:** Conduct independent analysis of wallet transaction history to determine if the concentration poses a risk of coordinated market manipulation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 2.0% of supply. Of that, 1.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.9% in wallets, 0.0% in other contracts. 3,010 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,010 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $333K (DexScreener, all pools). 24h trading volume $145K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $333K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`qmBj1V...pump`](https://solscan.io/account/qmBj1VPb9BL1nDJ3tvEfEn17BR2ZoXECn89yVr5pump) |
| **Network** | Solana |
| **Price** | $0.01666 |
| **24h Volume** | $145.2K |
| **Liquidity** | $333.0K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 2d |
| **Top-10 Holders** | 2.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 50256 buys / 2508 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9fcgtjjfknrequax7juxeqtz5p5wzwzjjeyp41qlwdee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-sol-b37f)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
