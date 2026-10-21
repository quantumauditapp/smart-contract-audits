---
token: AlloX
ticker: ALLOX
network: solana
risk_score: 25
status: low
date: 2026-10-21
---

# AlloX (ALLOX) — Smart Contract Security Analysis | Solana

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/allox-sol-e9ab)

---

## Audit Summary

The AlloX token mint has successfully revoked both mint and freeze authorities, providing a secure foundation for supply and transfer integrity. However, the protocol exhibits high-risk economic indicators, specifically a volume-to-liquidity ratio exceeding 128 and 100% of liquidity remaining unlocked. Third-party registry data indicates a high concentration of unlocked LP tokens.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the liquidity pool for sudden withdrawals, as the current lack of locks allows for potential removal of all backing assets.

Verify the current liquidity status via block explorers before executing trades. Avoid large market orders to mitigate the impact of high slippage and potential volatility associated with the reported wash-trading patterns.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.6 External factors present significant risks. The volume/liquidity ratio of 128.29 suggests potential wash trading. 7.5 Governance is impacted by the fact that 100% of liquidity is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token mint. Metadata is immutable, and no upgradeable extensions are present. The token state is fixed and cannot be modified by any… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 128.29, which significantly exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading activity for consistent, non-organic patterns.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

100% of the pool's liquidity is unlocked and potentially withdrawable by anonymous holders, posing a risk of sudden liquidity removal.

**Recommendation:** Require liquidity locking or burning to ensure long-term pool stability.


### `M-01` — High-Risk Registry Flag  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry identifies a large amount of unlocked LP tokens and a low number of liquidity providers.

**Recommendation:** Exercise caution; verify the source of liquidity and the distribution of LP tokens.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $293K (DexScreener, all pools). 24h trading volume $35.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $293K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AVTTVL...FX1U`](https://solscan.io/account/AVTTVLHVtDdHbGcZ9ki6LRBLjGJQEqHH6eq1CRCkFX1U) |
| **Network** | Solana |
| **Price** | $0.00001531 |
| **24h Volume** | $35.44M |
| **Liquidity** | $293.2K |
| **Volume / Liquidity** | 120.9× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 17250 buys / 15556 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/svmvpwvgeo1ht33wpxpvdbussmsyssja8s9qycgwmta)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/allox-sol-e9ab)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
