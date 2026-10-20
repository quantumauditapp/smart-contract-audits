---
token: xingxing
ticker: XINGXING
network: solana
risk_score: 20
status: low
date: 2026-10-20
---

# xingxing (XINGXING) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xingxing-sol)

---

## Audit Summary

The xingxing token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the token's trading volume relative to its liquidity to avoid slippage caused by artificial market activity. Since holder concentration data is unavailable, users should exercise caution regarding potential whale activity that may not be visible in current market metrics.

Verify the current supply and authority status using a block explorer to confirm that the mint and freeze authorities remain null. No further administrative actions are possible for this contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program, ensuring standard compliance. 7.1 Architecture and 7.2 Code Security are governed by the native Solana program logic. 7.3 Access Control is… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic stability is supported by 100% of pool liquidity being burned, preventing rug pulls via withdrawal. However, 7.5 Governance and 7.6 External market signals indicate a high… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are restricted by the revocation of all administrative authorities. Metadata is immutable, and no upgradeable extensions are present. The token state is fixed and… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 33.52, which exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when trading; high volume relative to liquidity often masks low organic demand.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $568K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 8 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Bivugv...pump`](https://solscan.io/account/Bivugv4GNFUiqUabDhvFcepDskTcgPk7EtExV4mvpump) |
| **Network** | Solana |
| **Price** | $0.00003696 |
| **24h Volume** | $517.5K |
| **Liquidity** | $15.4K |
| **Volume / Liquidity** | 33.6× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5955 buys / 4447 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dqjymzeab41ffvy9pr6symzwuvabk1wxe7tkwzhnuxxr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xingxing-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
