---
token: United States Oil Exchange
ticker: USOE
network: solana
risk_score: 0
status: low
date: 2026-10-29
---

# United States Oil Exchange (USOE) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-oil-exchange-sol-6f68)

---

## Audit Summary

The USOE token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and metadata is immutable. A third-party registry flags high holder correlation, which warrants caution regarding potential coordinated market activity.

> **Final Recommendation:** Investors should monitor the high holder correlation flagged by third-party registries to ensure that market activity remains organic. No further technical action is required as the mint is fully renounced and liquidity is permanently locked.

Verify the current mint and freeze authority status on a block explorer to confirm they remain set to 'None'. Ensure that any future interactions with this token are performed through reputable DEX interfaces.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program, ensuring modern extension support. 7.1 Architecture and 7.2 Code Security are robust as both mint and freeze authorities are revoked. 7.3 Access… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $309,775 in liquidity, which is 100% burned and permanently locked. 7.5 Governance is decentralized due to the lack of mint authority. 7.6 External signals… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not utilize proxy patterns. Metadata is immutable, preventing unauthorized changes to the token identity. The configuration is static and cannot… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, which may indicate that a significant portion of the supply is controlled by a small group of related entities.

**Recommendation:** Monitor on-chain wallet movements for signs of coordinated sell-offs or wash trading.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 2.0% of supply. Of that, 1.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.8% in wallets, 0.0% in other contracts. 2,985 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,985 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $311K (DexScreener, all pools). 24h trading volume $175K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $311K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`T25YhK...pump`](https://solscan.io/account/T25YhKsRkTwdB2GeDHLXGfacnHcyW5r8rDV59jdpump) |
| **Network** | Solana |
| **Price** | $0.01414 |
| **24h Volume** | $174.5K |
| **Liquidity** | $310.9K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1d |
| **Top-10 Holders** | 2.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 22969 buys / 2540 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9ftmmxjx5vyvyvm51mm8zzndnsnat4yhbjlyu3wyz1u7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-oil-exchange-sol-6f68)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
