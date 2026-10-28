---
token: Dora Bulking
ticker: DORA
network: solana
risk_score: 29
status: low
date: 2026-10-28
---

# Dora Bulking (DORA) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dora-bulking-sol)

---

## Audit Summary

Dora Bulking (DORA) is a Token-2022 asset with fully revoked mint and freeze authorities, ensuring supply immutability and transfer safety. The primary risks identified are low liquidity and a high volume-to-liquidity ratio, which may indicate artificial trading activity. All third-party registry data was successfully retrieved.

> **Final Recommendation:** Investors should exercise caution regarding the low liquidity depth, which may result in significant slippage during large trades. Monitor the token's trading volume relative to liquidity to avoid interacting with potentially manipulated markets.

Verify the current liquidity status on-chain to ensure the burned status remains consistent with the provided data. No further administrative actions are required as the mint is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active transfer hooks or frozen account states. 7.1 Architecture is standard for SPL mints, and 7.3 Access Control is robust as both mint and… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show a concentration of 23.87% among the top 10 holders, which is within safe parameters. 7.6 External market data indicates $7,624 in liquidity, which is fully burned… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the token uses a standard SPL mint structure. Metadata is immutable, and no authority exists to modify token parameters. The configuration is locked permanently. |

## Security Findings

_🟠 2 High · ⚪ 6 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $7,624. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth before executing large market orders.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 47.18x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as high volume-to-liquidity ratios often indicate non-organic trading activity.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 45.9% of supply. Of that, 22.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.9% in wallets, 0.0% in other contracts. 502 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

502 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $450K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10K of DEX liquidity across 7 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DDgEb1...pump`](https://solscan.io/account/DDgEb1AyoqR81NNTJX44AgpfYkbnWAegf4BrxP1Bpump) |
| **Network** | Solana |
| **Price** | $0.00001908 |
| **24h Volume** | $347.2K |
| **Liquidity** | $10.2K |
| **Volume / Liquidity** | 34.2× |
| **Token Age** | 16h |
| **Top-10 Holders** | 45.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6170 buys / 4496 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5dpxjsnxo5rpiubns4pfkghkyfagarzxptvu9twhxcdv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dora-bulking-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
