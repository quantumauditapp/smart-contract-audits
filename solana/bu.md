---
token: Bu
ticker: BU
network: solana
risk_score: 31
status: low
date: 2026-10-29
---

# Bu (BU) — Smart Contract Security Analysis | Solana

> **Risk Score: 31/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bu-sol)

---

## Audit Summary

The Bu token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully burned, preventing rug-pulls via liquidity withdrawal, though the token suffers from very low liquidity relative to trading volume. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should be aware of the low liquidity environment, which may lead to significant slippage during large trades. Monitor the token's price stability and volume trends on DEX platforms before executing large orders.

Verify the token mint address directly on a block explorer to ensure it matches the address audited here. No further on-chain action is required regarding authority management as the mint is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $8,507 in liquidity, which is below the $10,000 threshold, resulting in a High liquidity risk. 7.5 Governance is decentralized due to the revocation of minting rights.… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL tokens do not use proxy patterns. Metadata and balance-mutating authorities are disabled, ensuring the token's core parameters are immutable. The configuration… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $8,507. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $227K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 7 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Bnxttv...Buuu`](https://solscan.io/account/Bnxttv7gQHYP1n9JyXuiATWKtxxJPc6sJJzeRFVBuuu) |
| **Network** | Solana |
| **Price** | $0.00001772 |
| **24h Volume** | $81.6K |
| **Liquidity** | $9.4K |
| **Volume / Liquidity** | 8.7× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1457 buys / 1017 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7kxk9aucjdcnabhfku4qjacz82rj9rmt6uwsctcjkl9f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
