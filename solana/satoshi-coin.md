---
token: Satoshi Coin
ticker: SATOSHI
network: solana
risk_score: 24
status: low
date: 2026-11-03
---

# Satoshi Coin (SATOSHI) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/satoshi-coin-sol)

---

## Audit Summary

Satoshi Coin is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against supply dilution and account freezing. However, the token exhibits a high volume-to-liquidity ratio of 59.46, indicating potential wash trading. Holder concentration data was unavailable from the chain-native RPC.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which suggests that the reported trading volume may not reflect organic market demand. Monitor the token's liquidity depth before executing large trades to avoid significant slippage.

Verify that no new extensions have been added to the mint address via a block explorer. Since holder concentration data is unavailable, perform independent checks on the top token accounts if possible to assess the risk of whale-driven price volatility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust as… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $14,039 in liquidity, which is fully burned, preventing rug pulls via liquidity withdrawal. 7.5 Governance is decentralized due to the lack of mint authority. 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL mint. Metadata is immutable, and no authority exists to modify token parameters. The token state is fixed and cannot be altered by the… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume of $834,747 against $14,039 in liquidity results in a ratio of 59.46, which exceeds the 20x threshold for suspicious trading activity.

**Recommendation:** Account for potential price manipulation and high slippage when trading this asset.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $884K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (toshi); launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $20K of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Hu5Qdt...TYo5`](https://solscan.io/account/Hu5Qdto25NKcUepDxZYRjkJigU1UX4vGrxDeomt2TYo5) |
| **Network** | Solana |
| **Price** | $0.00005488 |
| **24h Volume** | $805.2K |
| **Liquidity** | $19.9K |
| **Volume / Liquidity** | 40.4× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11150 buys / 7460 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/32yheqpdeyqj18rr33zsrecbhi1fgbkc4du9wcquxdfr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/satoshi-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
