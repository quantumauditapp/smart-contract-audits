---
token: UAV
ticker: UAV
network: solana
risk_score: 22
status: low
date: 2026-11-04
---

# UAV (UAV) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uav-sol)

---

## Audit Summary

The UAV token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. The liquidity pool is fully burned, preventing rug-pulls via liquidity withdrawal. However, the high volume-to-liquidity ratio suggests potential wash trading, and holder concentration data is currently unavailable.

> **Final Recommendation:** Investors should monitor the token's trading activity, as the high volume-to-liquidity ratio may indicate artificial market manipulation. Since holder concentration data is unavailable, users should exercise caution regarding potential price volatility caused by large, undisclosed wallets.

Verify the current supply and authority status directly on a block explorer to confirm that the mint and freeze authorities remain null. Do not rely on third-party volume metrics as a sole indicator of organic demand.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL mints, with no… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $39,507 in liquidity, which is fully burned, ensuring 7.5 Governance and 7.8 Operations safety regarding pool access. 7.6 External market data indicates a volume/liquidity… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL token mints. Metadata is immutable, and no transfer fee or hook upgrade paths exist. The token state is fixed and cannot be altered by the original deployer. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 34.97, which exceeds the 20x threshold, indicating potential wash trading or artificially inflated volume.

**Recommendation:** Exercise caution when interpreting volume metrics; perform independent analysis of trade frequency and order book depth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 86% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $48K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $48K of DEX liquidity across 20 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`95kvFs...pump`](https://solscan.io/account/95kvFsVDJ5Lr4GH9Uau4dUgstft6gwnVagpKwYt2pump) |
| **Network** | Solana |
| **Price** | $0.0002552 |
| **24h Volume** | $1.37M |
| **Liquidity** | $41.2K |
| **Volume / Liquidity** | 33.3× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8795 buys / 6328 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fwaqynqgehz58rwkyrr6bcp4c4runhpcq8dxytfrzvcr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/uav-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
