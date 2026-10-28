---
token: Robotaxi Coin
ticker: ROBOTAXI
network: solana
risk_score: 29
status: low
date: 2026-10-28
---

# Robotaxi Coin (ROBOTAXI) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/robotaxi-coin-sol-12b9)

---

## Audit Summary

The Robotaxi Coin (JEFb35...) exhibits high centralization risk due to extreme holder concentration, with the top 10 holders controlling 93.98% of the supply. While mint and freeze authorities are correctly revoked and liquidity is fully burned, the token's economic structure remains highly susceptible to manipulation by a small number of entities. Third-party registry data confirms high ownership risks.

> **Final Recommendation:** Investors should exercise extreme caution due to the high concentration of supply among a small number of holders. Monitor the top 10 wallet addresses for significant sell-side activity that could impact market stability.

Verify the current holder distribution via block explorers to ensure no single entity is accumulating a majority of the circulating supply. Do not rely on the token's liquidity lock alone to mitigate the risk of a coordinated sell-off by major holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance metrics indicate extreme concentration, with 93.98% of supply held by the top 10 wallets. 7.6 External signals confirm high ownership risk. Liquidity is fully secured… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token mint. Metadata is immutable, and there are no upgradeable components or proxies. The token state is fixed and cannot be modified by the… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 93.98% of the total supply. Coordinated sell-off by these entities would crash the price, and single-whale dumps are highly likely given this distribution.

**Recommendation:** Monitor the top 10 holders for movement and diversify holdings to avoid exposure to concentrated sell-side pressure.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $200K (DexScreener, all pools). 24h trading volume $7.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $200K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`JEFb35...nb6K`](https://solscan.io/account/JEFb35pKTaJirpdQYLtVTkSGAQACvMLaJQ2cAV3Fnb6K) |
| **Network** | Solana |
| **Price** | $0.000144 |
| **24h Volume** | $7.54M |
| **Liquidity** | $199.7K |
| **Volume / Liquidity** | 37.8× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12345 buys / 7335 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/utquymwhbqjreoapaygekz7wghy7xaoqxrewxnadl8f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/robotaxi-coin-sol-12b9)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
