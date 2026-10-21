---
token: Energy Coin
ticker: ENERGY
network: solana
risk_score: 23
status: low
date: 2026-10-21
---

# Energy Coin (ENERGY) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/energy-coin-sol)

---

## Audit Summary

Energy Coin is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong baseline security for token supply and transferability. However, the token exhibits a high volume-to-liquidity ratio indicative of wash trading and is flagged as a copycat token by third-party registries. Holder concentration data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise caution due to the 'copycat' registry flag and the high volume-to-liquidity ratio, which often precedes high volatility or liquidity exhaustion. Verify the token mint address against official project channels to ensure you are interacting with the intended asset.

Monitor the token's trading activity on-chain to confirm that volume is organic rather than automated. Given the lack of holder concentration data, avoid large market orders that could be impacted by low liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture is standard for SPL mints, with 7.3 Access Control confirmed by the revocation of both mint… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis reveals a high volume-to-liquidity ratio of 161.30, suggesting artificial trading activity. 7.5 Governance is decentralized as the mint authority is null. 7.6 External signals… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL token mints in the EVM sense; however, metadata and transfer fees are immutable. 7.8 Operations are stable as the token program configuration is locked. No… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 161.30, significantly exceeding the 20x threshold, which is a strong indicator of wash trading.

**Recommendation:** Monitor trading patterns for artificial volume and exercise caution regarding price discovery.


### `M-01` — Flagged as Copycat Token  *(Severity: Medium · Status: Unresolved)*

Third-party risk registries have flagged this token as a copycat, suggesting it may be impersonating a more established project.

**Recommendation:** Verify the project's legitimacy and official contract address through verified social channels.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 87% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $24K (DexScreener, all pools). 24h trading volume $2.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $24K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CicoFL...pump`](https://solscan.io/account/CicoFLHq5c3n6w61e68WfnooFWUzTLisp3a2HdiWpump) |
| **Network** | Solana |
| **Price** | $0.00005585 |
| **24h Volume** | $2.32M |
| **Liquidity** | $21.1K |
| **Volume / Liquidity** | 110.2× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20978 buys / 17486 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/evdxxqa1tpuannw2emmhsj36g9qumjhhcl8nui9sadxp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/energy-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
