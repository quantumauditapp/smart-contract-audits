---
token: AlloX
ticker: ALLOX
network: solana
risk_score: 28
status: low
date: 2026-10-24
---

# AlloX (ALLOX) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/allox-sol-baa0)

---

## Audit Summary

The AlloX token exhibits significant economic risks due to extreme wash-trading signals and a lack of locked liquidity. While the mint and freeze authorities are correctly revoked, the high volume-to-liquidity ratio and the inability to verify the security of the pool's liquidity present substantial concerns for potential investors. Third-party registry data indicates a large amount of unlocked liquidity.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the high probability of artificial trading volume. Monitor the liquidity pool for sudden withdrawals by anonymous entities.

Verify the current liquidity status via block explorers to ensure the pool has not been drained. Avoid large positions that cannot be supported by the current $272,289 liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program. 7.3 Access Control is robust as both the mint and freeze authorities are revoked. 7.1 Architecture follows standard SPL v3 specifications. 7.2 Code… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic indicators show extreme volatility potential with a volume/liquidity ratio of 193.93, suggesting significant wash trading. 7.6 External signals confirm that 100% of pool liquidity is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the mint is a standard SPL token. 7.8 Operations are stable; metadata is immutable and no extensions were found that allow for balance or fee modifications. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 193.93, which significantly exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading patterns for signs of manipulation and account for high slippage.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the entirety of the liquidity is potentially withdrawable by anonymous holders.

**Recommendation:** Treat the pool as removable until liquidity is formally locked or burned.


### `M-01` — Large Amount of LP Unlocked  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry flags the token for having a large amount of unlocked liquidity, increasing the risk of a liquidity rug pull.

**Recommendation:** Verify the liquidity provider's wallet activity and avoid tokens with high exposure to single-wallet liquidity withdrawals.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $338K (DexScreener, all pools). 24h trading volume $49.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $338K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BGpURk...Ku7P`](https://solscan.io/account/BGpURkQa9NeUp9uJPQnJgzdhmQtDkXesiFWWVDWcKu7P) |
| **Network** | Solana |
| **Price** | $0.00001678 |
| **24h Volume** | $49.44M |
| **Liquidity** | $338.4K |
| **Volume / Liquidity** | 146.1× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 24490 buys / 22182 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/a67d8qxm4frrjc4lcdoxnvebxjut4ywwcrvwbfsy6y7w)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/allox-sol-baa0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
