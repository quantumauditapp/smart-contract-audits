---
token: Actually Useless
ticker: AU
network: solana
risk_score: 16
status: low
date: 2026-10-22
---

# Actually Useless (AU) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/actually-useless-sol)

---

## Audit Summary

The token 'Actually Useless' (Au) utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the high volume-to-liquidity ratio suggests potential wash trading activity. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Monitor the token's trading volume on DEX platforms to determine if the high volume-to-liquidity ratio persists or stabilizes. Since liquidity is fully burned, the primary risk is market volatility rather than administrative rug-pulls.

Verify the token's current supply and holder distribution using a block explorer to ensure no single entity holds a majority stake, as this data was not available during this audit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust, as both… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic analysis shows $71,843 in liquidity, which is fully burned, preventing rug-pulls via liquidity withdrawal. 7.6 External market data indicates a volume/liquidity ratio of 21.11, exceeding… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL token mints in the EVM sense. Metadata is immutable, and there are no upgradable transfer hooks or fees. The token state is fixed and cannot be modified by any… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 21.11, which exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; monitor for organic trading activity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 56% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $126K (DexScreener, all pools). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $126K of DEX liquidity across 18 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6mYfg1...pump`](https://solscan.io/account/6mYfg1EmMVjbQv38QGY5XdRUQ4SyNpFauL1aiRiWpump) |
| **Network** | Solana |
| **Price** | $0.0005765 |
| **24h Volume** | $1.38M |
| **Liquidity** | $70.7K |
| **Volume / Liquidity** | 19.6× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13300 buys / 9675 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fnyuadkhuyanvbr25vxrht2s3n9s3tkcj3nbvy7sqjwj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/actually-useless-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
