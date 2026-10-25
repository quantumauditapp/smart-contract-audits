---
token: Soul Labs
ticker: SO
network: solana
risk_score: 25
status: low
date: 2026-10-25
---

# Soul Labs (SO) — Smart Contract Security Analysis | Solana

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-1566)

---

## Audit Summary

The Soul Labs token (SO) has successfully revoked both mint and freeze authorities, mitigating risks of supply inflation and account freezing. However, the token exhibits high-risk economic indicators, including a high volume-to-liquidity ratio suggestive of wash trading and 100% of pool liquidity remaining unlocked. Holder distribution data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the liquidity pool for sudden withdrawals before engaging in any transactions.

Verify the current liquidity status on-chain via block explorers to ensure the pool creator has not removed funds. Avoid high-frequency trading given the wash-trading signals present in the market data.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance risks are elevated due to liquidity management. 100% of pool liquidity is unlocked, allowing for potential removal by the creator. The volume/liquidity ratio of 193.56… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as SPL tokens do not use proxy patterns. Metadata is immutable, preventing branding changes. The token configuration is fixed and cannot be modified by any authority. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked; the remaining liquidity can be withdrawn by the pool creator.

**Recommendation:** The project should burn or time-lock the LP tokens to ensure long-term liquidity stability.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume is 193.56x the liquidity, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as the reported volume may not reflect genuine market interest or liquidity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $385K (DexScreener, all pools). 24h trading volume $56.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $385K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Hb5oWi...rcYM`](https://solscan.io/account/Hb5oWiwD18XHNTgPE59DMXf9BPEPkQABen91gGovrcYM) |
| **Network** | Solana |
| **Price** | $0.00001841 |
| **24h Volume** | $56.22M |
| **Liquidity** | $384.6K |
| **Volume / Liquidity** | 146.2× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 27515 buys / 24976 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6cxao7beatkzlbrfttv9rdw2rrtphtmumf7ogzsrxit2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-1566)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
