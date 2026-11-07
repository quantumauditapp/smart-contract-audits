---
token: XTO
ticker: XTO
network: solana
risk_score: 0
status: low
date: 2026-11-07
---

# XTO (XTO) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-sol-b5de)

---

## Audit Summary

The XTO token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and metadata is immutable. Holder distribution data was unavailable, and a third-party registry flagged high holder correlation, which should be monitored.

> **Final Recommendation:** The token exhibits strong security properties regarding authority revocation and liquidity safety. Users should independently verify the current holder distribution using block explorers to assess the impact of the reported high holder correlation.

Monitor the token's market activity for signs of coordinated sell-offs given the third-party registry warning. No further technical action is required as the mint is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust as both… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $274,213 in liquidity, which is 100% burned and inaccessible to the creator. 7.5 Governance and 7.6 External factors are influenced by a third-party registry… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is locked, preventing unauthorized changes to the token's identity. No upgradeable extensions are present. |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — High Holder Correlation Flag  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by related entities.

**Recommendation:** Review the top holder addresses on a block explorer to determine if the concentration poses a risk to market stability.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $273K (DexScreener, all pools). 24h trading volume $265K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $273K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ZAEP4x...pump`](https://solscan.io/account/ZAEP4x2UzVcXErhQnzppj35HZu4WSTiyzd1fkdcpump) |
| **Network** | Solana |
| **Price** | $0.01189 |
| **24h Volume** | $264.6K |
| **Liquidity** | $273.1K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 22h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 23498 buys / 2505 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/agubzhxetnwqjuj2pegcrr3zdd4ampzidmwqx3j3fvwb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-sol-b5de)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
