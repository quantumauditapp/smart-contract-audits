---
token: National American Dividend Fund
ticker: NADF
network: solana
risk_score: 0
status: low
date: 2026-11-05
---

# National American Dividend Fund (NADF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/national-american-dividend-fund-sol)

---

## Audit Summary

The National American Dividend Fund (NADF) utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating risks of rug pulls. Holder distribution data was unavailable, and a third-party registry flagged high holder correlation, which warrants caution regarding potential market manipulation.

> **Final Recommendation:** Investors should monitor the token's market activity for signs of coordinated sell-offs due to the high holder correlation reported by third-party registries. Since holder distribution data is currently unavailable, users should exercise caution when entering large positions.

Verify the current supply and authority status periodically using a block explorer to ensure no unexpected changes occur. Given the lack of transfer hooks and immutable metadata, the token's technical behavior is predictable and transparent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are set to null. 7.2 Code Security is standard for the… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $141,753 in liquidity, which is 100% burned. 7.5 Governance is limited as the token lacks on-chain voting mechanisms. 7.6 External signals indicate high holder… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. 7.8 Operations are secure due to immutable metadata and the inability to mutate balances or transfer fees post-launch. |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by a small group of entities.

**Recommendation:** Monitor on-chain movements of the largest accounts to assess the risk of coordinated sell-offs.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $142K (DexScreener, all pools). 24h trading volume $131K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $142K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`S3Xvet...pump`](https://solscan.io/account/S3XvetF2rGnzXwZSy2Mgv2PWjCzd823i9Ne6Ut6pump) |
| **Network** | Solana |
| **Price** | $0.003004 |
| **24h Volume** | $130.6K |
| **Liquidity** | $141.6K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 10h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 31629 buys / 1178 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9bgc5i21umtdjhkrkgrcyykvgj8jm5xbd2pvjszxvas2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/national-american-dividend-fund-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
