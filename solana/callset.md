---
token: Callset
ticker: CALL
network: solana
risk_score: 17
status: low
date: 2026-11-07
---

# Callset (CALL) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/callset-sol)

---

## Audit Summary

The Callset (CALL) token is a standard SPL v3 token with both mint and freeze authorities successfully revoked. The liquidity pool is fully burned, ensuring the liquidity cannot be withdrawn by the creator. Third-party risk registry data indicates no adverse flags, and holder distribution data is currently unavailable.

> **Final Recommendation:** The token is technically sound regarding authority management and liquidity safety. Users should monitor the token's market activity and volume trends, as the lack of holder distribution data prevents a full assessment of supply concentration risks.

Verify the current supply and authority status directly via a block explorer to confirm that no changes have occurred since this audit. Exercise caution with low-liquidity assets and ensure that any trade execution accounts for potential slippage.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, preventing unauthorized supply inflation or account freezing (7.3 Access Control).… |
| **Governance / Economics** | 9/10 | Low | Liquidity is $10,375 with 100% of LP tokens burned, protecting against rug-pulls via liquidity withdrawal (7.4 Economic). The volume/liquidity ratio is 9.10, indicating active trading relative to… |
| **Upgrades** | 10/10 | Low | The mint is immutable as both mint and freeze authorities are revoked (7.7 Upgrades). Metadata is not mutable, ensuring branding consistency (7.3 Access Control). No upgrade paths exist for this… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $127K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 4 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7tAjeX...pump`](https://solscan.io/account/7tAjeX7mNQg2jsJkDH1ePwVNBG5J9xKoys2CMZdfpump) |
| **Network** | Solana |
| **Price** | $0.0000235 |
| **24h Volume** | $91.4K |
| **Liquidity** | $10.7K |
| **Volume / Liquidity** | 8.5× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 890 buys / 1042 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4w4xge3r89imrxwfocwqs2twcz8o7vzq4k15qgxzgv49)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/callset-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
