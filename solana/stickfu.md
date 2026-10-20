---
token: STICKFU
ticker: STICKFU
network: solana
risk_score: 21
status: low
date: 2026-10-20
---

# STICKFU (STICKFU) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stickfu-sol)

---

## Audit Summary

The STICKFU token is flagged as high-risk by an external registry due to creator history associated with rugged tokens. Trading is further impaired by extremely thin DEX liquidity of $2,683 and a 328.17 volume-to-liquidity ratio indicating potential wash trading, while chain-native holder distribution data remained unavailable. Although baseline mint parameters are structurally immutable, creator track record and market dynamics represent severe capital risks.

> **Final Recommendation:** Exercise extreme caution and avoid interacting with this token due to the deployer's established history of rugged projects and heavily distorted trading metrics. Market participants should monitor automated DEX pool events and verify whether on-chain transaction logs exhibit repetitive wash-trading loops before committing capital.

Should interaction occur, independently verify holder dispersion via an alternate RPC node once distribution data becomes available, set strict slippage bounds to counter the $2,683 liquidity pool, and maintain zero exposure beyond short-term speculative capacity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | Under 7.1 Architecture, the token relies entirely on the canonical Token-2022 program with standard 6 decimals and an initialized fixed supply. In terms of 7.2 Code Security and 7.3 Access Control… |
| **Governance / Economics** | 7/10 | Low | Examining 7.4 Economic conditions, 100.0% of pool liquidity is permanently burned, preventing direct liquidity extraction by the creator. However, available DEX depth is exceptionally fragile at… |
| **Upgrades** | 10/10 | Low | Addressing 7.7 Upgrades, the mint structure is entirely non-upgradeable with balance mutability, transfer fee adjustments, and hook upgrades marked false. Regarding 7.8 Operations, metadata… |

## Security Findings

_🔴 1 Critical · 🟠 2 High · ⚪ 5 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset (developer history, LP movements).

**Recommendation:** Do not interact with this token.


### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,683. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Ensure liquidity depth deepens substantially before executing trades, or restrict trade sizes to negligible amounts.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 328.17x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Inspect trading logs for circular bot activity and do not rely on reported volume as an indicator of genuine market interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $887K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`D3tSj2...pump`](https://solscan.io/account/D3tSj2izyLwXMr1svmwmtg6sLr4RubYVJfvmCKJUpump) |
| **Network** | Solana |
| **Price** | $0.00005001 |
| **24h Volume** | $856.4K |
| **Liquidity** | $18.6K |
| **Volume / Liquidity** | 45.9× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12451 buys / 11667 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6eegazeqemsu89w49jskm8fhwbaqhihxfavuut9usspu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stickfu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
