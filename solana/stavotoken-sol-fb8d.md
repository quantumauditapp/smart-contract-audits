---
token: stavotoken
ticker: STAVO
network: solana
risk_score: 28
status: low
date: 2026-11-01
---

# stavotoken (STAVO) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stavotoken-sol-fb8d)

---

## Audit Summary

The STAVO token mint has successfully revoked both mint and freeze authorities, preventing supply inflation and account freezing. However, the token exhibits high-risk economic indicators, including extreme wash-trading signals and a lack of locked liquidity. Third-party registry data indicates a history of malicious developer activity, and holder distribution data is currently unavailable.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the third-party risk registry warnings regarding developer history. Monitor the liquidity pool for sudden withdrawals, as the creator retains the ability to remove all funds.

Verify the current liquidity status on-chain before any trade. Given the high volume/liquidity ratio, do not rely on DEX-reported volume as an indicator of genuine market interest or exit liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic indicators are concerning, with a volume/liquidity ratio of 208.47, suggesting significant wash trading. 7.5 Governance and liquidity management are weak, as 100% of pool liquidity is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token mint. Metadata is immutable, and no transfer hooks or other mutable extensions are configured. The token state is fixed. |

## Security Findings

_🔴 1 Critical · 🟠 2 High · ⚪ 5 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry has flagged this token due to developer history of rugged tokens and large amounts of unlocked LP.

**Recommendation:** Do not interact with this token.


### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the pool creator can withdraw all liquidity at any time.

**Recommendation:** Ensure liquidity is locked via a reputable time-lock program.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 208.47, which is significantly above the 20x threshold, indicating artificial trade volume.

**Recommendation:** Perform independent volume analysis before executing large trades.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $70K (DexScreener, all pools). 24h trading volume $14.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $70K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5ZWTin...ApTo`](https://solscan.io/account/5ZWTin4FBPJ2G572jCWCi59o4SdPsGSinENMcmKYApTo) |
| **Network** | Solana |
| **Price** | $0.0001106 |
| **24h Volume** | $14.76M |
| **Liquidity** | $70.0K |
| **Volume / Liquidity** | 210.9× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14931 buys / 10303 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/defvsd5ucnjy4nwacj5fj1avpphebejtdrcz4jg6qims)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stavotoken-sol-fb8d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
