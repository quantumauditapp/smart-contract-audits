---
token: Extended
ticker: XTEN
network: solana
risk_score: 28
status: low
date: 2026-11-02
---

# Extended (XTEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/extended-sol)

---

## Audit Summary

The token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits high risk due to extreme wash-trading signals and the fact that 100% of liquidity remains unlocked and potentially withdrawable. Holder concentration data is unavailable, limiting visibility into potential supply-side risks.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the high probability of artificial volume. Monitor the pool's liquidity levels closely for sudden withdrawals.

Verify the current liquidity provider's wallet activity on-chain. Avoid large positions until the liquidity is formally locked or burned, as the current state allows for immediate removal of the pool's backing assets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the standard SPL Token program (7.1 Architecture). Access control is secure as both mint and freeze authorities are revoked (7.3 Access Control). No advanced extensions like… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits a volume/liquidity ratio of 95.28, indicating significant wash-trading (7.4 Economic). Liquidity is entirely unlocked, posing a risk of sudden withdrawal (7.8 Operations). Holder… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There is no upgradeability mechanism for the token program logic itself, which is standard for SPL tokens. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked; the entirety of the liquidity is held by anonymous providers who can withdraw it at any time.

**Recommendation:** Lock or burn the liquidity tokens to ensure the pool remains functional for traders.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 95.28, which is significantly above the 20x threshold, indicating artificially inflated trade volume.

**Recommendation:** Perform due diligence on trading patterns before assuming market depth is organic.


### `M-01` — Large Amount of LP Unlocked  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry flags the token for having a large amount of unlocked liquidity, increasing the risk of a liquidity rug-pull.

**Recommendation:** Monitor the liquidity pool for significant outflows.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $190K (DexScreener, all pools). 24h trading volume $16.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $190K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9RppZf...DJwy`](https://solscan.io/account/9RppZfxRspVANnFCaAgXfhUNU9BobqHkdyPLZTgiDJwy) |
| **Network** | Solana |
| **Price** | $0.00000718 |
| **24h Volume** | $16.81M |
| **Liquidity** | $190.0K |
| **Volume / Liquidity** | 88.5× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 15208 buys / 13812 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ezdur7qvny2txh4uhvr6admctw4gb9s3xkca8dea8tsg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/extended-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
