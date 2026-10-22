---
token: EggEmpire
ticker: EMP
network: solana
risk_score: 26
status: low
date: 2026-10-22
---

# EggEmpire (EMP) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/eggempire-sol)

---

## Audit Summary

EggEmpire (EMP) is a Token-2022 asset with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits high holder concentration, with the top 10 holders controlling 99.86% of the supply. All requested data sources were successfully retrieved.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for potential sell-side pressure, given the high concentration of supply. As the mint and freeze authorities are revoked, the token's supply and transferability are fixed, reducing administrative risk.

Verify the current holder distribution via a block explorer to assess if the top 10 wallets represent exchange hot wallets or individual entities before committing capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture is standard for SPL mints, with no active transfer hooks or frozen account states. 7.2 Code… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic factors show high concentration, as the top 10 holders control 99.86% of the supply. 7.6 External signals are positive, with 100% of liquidity burned, preventing withdrawal risks.… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints, but metadata mutability is disabled, ensuring branding consistency. The token configuration is immutable regarding its core authorities and extension… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 99.86% of the supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor the top 10 wallets for movement and assess if these represent centralized exchanges or concentrated private holdings.


### `M-01` — High Holder Concentration  *(Severity: Medium · Status: Unresolved)*

The top 10 holders control nearly the entire circulating supply, creating significant market impact risk for retail participants.

**Recommendation:** Exercise caution when entering large positions to avoid slippage caused by low liquidity depth relative to the concentrated supply.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.9% of supply. What remains: 8.9% in wallets, 91.0% in other contracts. 35 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

35 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $28K (DexScreener, all pools). 24h trading volume $33K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $28K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7JJvLX...pump`](https://solscan.io/account/7JJvLXiP5kiVsBsoGRJeqAhLEmHycA4hmC3oa5Fbpump) |
| **Network** | Solana |
| **Price** | $0.0001166 |
| **24h Volume** | $32.5K |
| **Liquidity** | $27.5K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 2d |
| **Top-10 Holders** | 99.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 128 buys / 121 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/aj5erpjzlvbl2fgsg85vxtjmmjocffs8wxbvahk6acss)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/eggempire-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
