---
token: National Oil Dividend Fund
ticker: NODF
network: solana
risk_score: 2
status: low
date: 2026-10-29
---

# National Oil Dividend Fund (NODF) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/national-oil-dividend-fund-sol-cb00)

---

## Audit Summary

The National Oil Dividend Fund (NODF) utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via 100% burning of LP tokens, and metadata is immutable. While a third-party registry flags high holder correlation, the token exhibits no critical technical vulnerabilities or centralized control mechanisms.

> **Final Recommendation:** The token configuration is secure regarding on-chain authorities and liquidity. Holders should monitor the 'High holder correlation' flag noted by third-party registries to ensure that the concentration of tokens does not lead to excessive price volatility.

Verify the current supply and authority status using a block explorer to confirm that no changes have occurred since this audit. Users should perform their own due diligence regarding the project's off-chain governance and long-term utility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program, ensuring modern extension support. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are set to null. 7.2… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $151,001 in liquidity, with 100% of LP tokens burned, preventing rug-pull risks. 7.5 Governance is decentralized as no single entity holds minting power. 7.6… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL mint as the program is immutable. Metadata is locked, preventing unauthorized changes to the token's identity. No upgradeable extensions or proxy patterns… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — High Holder Correlation  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by related entities.

**Recommendation:** Monitor wallet activity for coordinated sell-offs and evaluate the distribution of tokens among top holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 3.2% of supply. Of that, 2.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.7% in wallets, 0.0% in other contracts. 2,984 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,984 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $151K (DexScreener, all pools). 24h trading volume $171K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $151K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ccR9NW...pump`](https://solscan.io/account/ccR9NWFARkTWPtSzVHZQuPpGtSjXq88wY3te25kpump) |
| **Network** | Solana |
| **Price** | $0.003297 |
| **24h Volume** | $170.9K |
| **Liquidity** | $151.2K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | 3.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13982 buys / 2486 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3dx9t2khgx3vykho58tcsd9sh4vvaayba59ildshnwrs)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/national-oil-dividend-fund-sol-cb00)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
