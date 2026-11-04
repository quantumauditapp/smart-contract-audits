---
token: Slingtoshi Nakamoto
ticker: SLINGTOSHI
network: solana
risk_score: 1
status: low
date: 2026-11-04
---

# Slingtoshi Nakamoto (SLINGTOSHI) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/slingtoshi-nakamoto-sol)

---

## Audit Summary

The Slingtoshi Nakamoto token is a Token-2022 asset with both mint and freeze authorities successfully revoked. Liquidity is fully burned, ensuring the pool cannot be withdrawn by the creator. While third-party registries flag potential concentration and liquidity risks, the core on-chain configuration is secure.

> **Final Recommendation:** Investors should monitor on-chain holder distribution once data becomes available to assess concentration risks. Given the lack of visibility into top holders, maintain a position size appropriate for a high-concentration asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control (7.3) is robust as both mint and freeze authorities are revoked. No transfer hooks or balance-mutating extensions are… |
| **Governance / Economics** | 10/10 | Low | Economic (7.4) stability is supported by 100% burned liquidity, preventing rug-pulls via pool withdrawal. Governance (7.5) and holder distribution data are currently unavailable, limiting visibility… |
| **Upgrades** | 10/10 | Low | Upgrades (7.7) are not applicable as the mint is immutable. Metadata is immutable, preventing branding changes post-launch. The token configuration is finalized and cannot be altered by any authority. |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Third-Party Registry Risk Flag  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry flags the token for potential high holder concentration and liquidity concerns.

**Recommendation:** Perform manual analysis of the top 10 token accounts on a block explorer to verify current distribution.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $70K (DexScreener, all pools). 24h trading volume $304K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (toshi); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $70K of DEX liquidity across 19 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`F1LQvm...pump`](https://solscan.io/account/F1LQvm5biTdEXPrHokxhkR7sDwQcBnA8VTEmD5Gdpump) |
| **Network** | Solana |
| **Price** | $0.0004855 |
| **24h Volume** | $297.5K |
| **Liquidity** | $68.4K |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2268 buys / 1827 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8pgez9dvefxyz2ogisx588y4kgxk7yufydgan7wiwhah)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/slingtoshi-nakamoto-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
