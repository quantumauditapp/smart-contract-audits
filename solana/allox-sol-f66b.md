---
token: AlloX
ticker: ALLOX
network: solana
risk_score: 39
status: medium
date: 2026-10-23
---

# AlloX (ALLOX) — Smart Contract Security Analysis | Solana

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/allox-sol-f66b)

---

## Audit Summary

AlloX is a standard SPL token with revoked mint and freeze authorities, mitigating direct supply and confiscation risks. However, the token exhibits extreme wash-trading signals and high holder concentration, with 100% of liquidity currently unlocked and withdrawable by anonymous parties. Third-party registry data indicates significant risk regarding LP management.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and high wash-trading volume. Monitor the liquidity pool for sudden withdrawals by anonymous providers.

Verify the current holder distribution via block explorers to ensure that the top 10 wallets are not controlled by a single entity. Avoid large positions until liquidity is demonstrably locked or burned by the project team.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the standard spl-token program (7.1 Architecture). Access control is secure as both mint and freeze authorities are revoked (7.3 Access Control). No Token-2022 extensions are… |
| **Governance / Economics** | 4/10 | Medium | Holder concentration is high, with the top 10 holders controlling 81.11% of supply (7.4 Economic). The volume/liquidity ratio of 203.36 indicates severe wash-trading (7.6 External). Liquidity is… |
| **Upgrades** | 8/10 | Low | The token does not support upgrades (7.7 Upgrades). Metadata is immutable, preventing branding changes (7.8 Operations). Authority revocation is permanent (7.3 Access Control). |

## Security Findings

_🟠 3 High · 🟡 1 Medium · ⚪ 6 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell control 81.11% of the total supply. This concentration allows for significant price manipulation and potential for a coordinated sell-off.

**Recommendation:** Monitor the top 10 holder wallets for large transfers to exchanges or liquidity pools.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume to liquidity ratio is 203.36, which is significantly above the threshold of 20, indicating artificial trade volume.

**Recommendation:** Exercise caution when relying on volume metrics for liquidity assessment.


### `H-03` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked. The liquidity is held by anonymous wallets that can withdraw it at any time, potentially resulting in a total loss of liquidity for traders.

**Recommendation:** Verify if the project team intends to lock liquidity via a recognized third-party locker service.


### `M-01` — Flagged by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

Third-party risk registries have flagged the token due to a large amount of unlocked liquidity and a low number of liquidity providers.

**Recommendation:** Review the project's official communication channels for transparency regarding liquidity management.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.3% of supply. Of that, 10.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.3% in wallets, 80.8% in other contracts. 2,496 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,496 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $284K (DexScreener, all pools). 24h trading volume $57.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $284K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Edt7HR...5yNa`](https://solscan.io/account/Edt7HRHSYbPwgmvjN7yjoikvH5M7hFdNcr78uFSd5yNa) |
| **Network** | Solana |
| **Price** | $0.00001789 |
| **24h Volume** | $57.05M |
| **Liquidity** | $284.0K |
| **Volume / Liquidity** | 200.9× |
| **Token Age** | 8h |
| **Top-10 Holders** | 91.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 27138 buys / 24596 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/a8jwdkn5tpfplpc6lmoj8dpjzgzbrexdkyawvj3adxs5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/allox-sol-f66b)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
