---
token: United States Dividend Fund🌟
ticker: USDF
network: solana
risk_score: 1
status: low
date: 2026-10-30
---

# United States Dividend Fund🌟 (USDF) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-sol-cbad)

---

## Audit Summary

The USDF token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. Liquidity is fully secured via a 100% burn of LP tokens, mitigating withdrawal risks. Holder distribution data was unavailable, and a third-party registry flagged high holder correlation, which warrants caution regarding potential concentration.

> **Final Recommendation:** Monitor the token's holder distribution using on-chain explorers to identify potential concentration risks, as third-party registries have flagged high holder correlation. 

Verify that no new minting or freezing events occur by checking the mint account state on-chain, although the current revoked status makes this highly unlikely.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust as… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $195,602 in liquidity, which is 100% burned and permanently locked. 7.5 Governance is decentralized by the lack of mint authority. 7.6 External signals indicate… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is non-mutable, preventing branding changes. No upgrade paths exist for the token program logic. |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — High Holder Correlation Flagged  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by a small group of related entities.

**Recommendation:** Perform independent analysis of the top token accounts to assess the risk of coordinated sell-offs.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $195K (DexScreener, all pools). 24h trading volume $116K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.005658 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $195K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Uaq1Ss...pump`](https://solscan.io/account/Uaq1SsS8uNgsEGjowfU8QYno4dRAzk7E78neTRnpump) |
| **Network** | Solana |
| **Price** | $0.005658 |
| **24h Volume** | $116.0K |
| **Liquidity** | $194.6K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20053 buys / 649 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ewww1kwwcurpxnhcgszsbb6ng4oabxqxijwa8nslnjxz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-sol-cbad)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
