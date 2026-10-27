---
token: Jean Phil
ticker: JEANPHIL
network: solana
risk_score: 0
status: low
date: 2026-10-27
---

# Jean Phil (JEANPHIL) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jean-phil-sol-362d)

---

## Audit Summary

The Jean Phil (JEANPHIL) token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. The token exhibits low holder concentration and high liquidity security, as 100% of the pool liquidity is burned. A third-party risk registry flags this token as a 'Copycat token', which is the primary risk factor identified.

> **Final Recommendation:** The token is technically secure regarding on-chain authorities. Users should exercise caution due to the 'Copycat token' classification from third-party registries, which suggests the project may lack unique utility or original branding. Verify the token mint address against official project channels before trading.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust, as… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance metrics are stable, with the top 10 holders controlling only 3.24% of the supply. 7.6 External liquidity is healthy at ~$299k with a 100% burn rate, ensuring no… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL mint. Metadata is immutable, and no authority exists to modify token parameters or account states. The token configuration is finalized. |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Flagged as Copycat Token  *(Severity: Low · Status: Unresolved)*

An independent third-party risk registry classifies this token as a copycat, indicating it may be mimicking another project's identity.

**Recommendation:** Perform thorough due diligence on the project's legitimacy and official sources before interacting.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 4.5% of supply. Of that, 1.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.2% in wallets, 0.0% in other contracts. 2,412 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,412 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $297K (DexScreener, all pools). 24h trading volume $143K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $297K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9X7Hpz...pump`](https://solscan.io/account/9X7HpzDX6GKJo2xr1ygEFSeMGNdBwZr6Abc2qajBpump) |
| **Network** | Solana |
| **Price** | $0.01258 |
| **24h Volume** | $143.3K |
| **Liquidity** | $297.4K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 4.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 29767 buys / 1093 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8umhcx6viamldqwqrvg8dcltx9xevsjkrs9skmphsopn)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jean-phil-sol-362d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
