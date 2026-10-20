---
token: AlloX
ticker: ALLOX
network: solana
risk_score: 29
status: low
date: 2026-10-20
---

# AlloX (ALLOX) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/allox-sol)

---

## Audit Summary

AlloX is a standard SPL token with both mint and freeze authorities successfully revoked. However, the token exhibits high-risk economic indicators, specifically a volume-to-liquidity ratio suggesting wash trading and 100% of pool liquidity remaining unlocked. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the high volume-to-liquidity ratio and the lack of locked liquidity. Monitor the pool for sudden liquidity removal, as the current configuration allows the creator to withdraw all funds.

Verify the current liquidity status on-chain before executing any trades. Avoid large positions that cannot be exited due to the potential for high slippage and the risk of liquidity being drained by the pool creator.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the SPL… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic analysis reveals a volume/liquidity ratio of 139.41, significantly exceeding the 20x threshold for wash-trading suspicion. 7.6 External signals indicate 100% of pool liquidity is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. 7.8 Operations are stable as metadata is immutable and no balance-mutating authorities exist. The token configuration is fixed and cannot be… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 139.41, which is significantly above the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation and account for high slippage.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

100% of the pool's liquidity is unlocked and potentially withdrawable by the pool creator.

**Recommendation:** Treat the pool as removable; verify if the creator intends to lock or burn the liquidity.


### `M-01` — Low LP Provider Count  *(Severity: Medium · Status: Unresolved)*

Third-party registry signals indicate a low number of liquidity providers, increasing the risk of price volatility.

**Recommendation:** Assess the depth of the order book before trading.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $316K (DexScreener, all pools). 24h trading volume $43.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $316K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2Afp3H...DRRS`](https://solscan.io/account/2Afp3Hfy36Z9BuXTbqJrpR8PfVwDPqcBpwoAibYEDRRS) |
| **Network** | Solana |
| **Price** | $0.00001561 |
| **24h Volume** | $43.93M |
| **Liquidity** | $315.7K |
| **Volume / Liquidity** | 139.2× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 21866 buys / 19766 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/dvk7sscqcefbfc3sng2avcvbe5rtecxxceoc9ib2re3p)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/allox-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
