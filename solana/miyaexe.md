---
token: MIYA.EXE
ticker: MIYA
network: solana
risk_score: 22
status: low
date: 2026-10-27
---

# MIYA.EXE (MIYA) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/miyaexe-sol)

---

## Audit Summary

MIYA.EXE is a Token-2022 asset with fully revoked mint and freeze authorities, indicating a decentralized ownership model. However, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading activity. Holder concentration data is unavailable, and third-party registry data shows no adverse flags.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high ratio is driven by organic interest or automated wash trading. Given the lack of holder concentration data, users should exercise caution regarding potential whale activity.

Verify the current supply and authority status directly on a Solana block explorer to confirm the revocation status remains unchanged. Before executing large trades, assess the impact of the current liquidity depth on slippage.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or default frozen states… |
| **Governance / Economics** | 7/10 | Low | Liquidity is $35,653 and is fully burned, preventing rug pulls via liquidity withdrawal (7.4 Economic). The volume/liquidity ratio of 24.72 indicates significant trading activity relative to pool… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, and no upgradeable extensions are configured (7.7 Upgrades). Authority revocation is permanent, ensuring the contract state cannot be altered (7.3 Access Control). No… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 24.72, exceeding the threshold of 20. This pattern is strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading patterns for organic activity before committing capital.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 87% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $874K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $41K of DEX liquidity across 15 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`91RBVu...pump`](https://solscan.io/account/91RBVuoCLvikHs4qeUGczABotGLd1Tjo84DMfpFUpump) |
| **Network** | Solana |
| **Price** | $0.0001793 |
| **24h Volume** | $805.4K |
| **Liquidity** | $35.5K |
| **Volume / Liquidity** | 22.7× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8225 buys / 6868 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4dgujyxecnq7zsqrnu14fwxmdijrwmmw7wigl7vrhfsw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/miyaexe-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
