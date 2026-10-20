---
token: FLYING TESLA DOGESTER
ticker: DOGESTER
network: solana
risk_score: 14
status: low
date: 2026-10-19
---

# FLYING TESLA DOGESTER (DOGESTER) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flying-tesla-dogester-sol)

---

## Audit Summary

The FLYING TESLA DOGESTER (DOGESTER) SPL Token Mint exhibits a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, and all pool liquidity is permanently burned. Third-party risk registry data was unavailable for this assessment.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of the token. Monitor the token's liquidity and trading volume for any significant changes, although current liquidity is locked. No further specific actions are required based on the current on-chain configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be created and no accounts can be frozen. No… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding only 19.94% of the supply. The token has a liquidity of $36,765 USD, which is above the very low liquidity threshold. All… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, preventing any future changes to token supply or account freezing capabilities. No Token-2022 extensions like transfer hooks or default frozen… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 28.2% of supply. Of that, 8.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.9% in wallets, 0.0% in other contracts. 1,390 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,390 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $37K (DexScreener, all pools). 24h trading volume $339K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (doge); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $37K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8Rpybi...pump`](https://solscan.io/account/8RpybikpGLbKsYJ4FXz12ExDz89R7VXAUZ3JXNcKpump) |
| **Network** | Solana |
| **Price** | $0.0002 |
| **24h Volume** | $330.6K |
| **Liquidity** | $37.3K |
| **Volume / Liquidity** | 8.9× |
| **Token Age** | 16h |
| **Top-10 Holders** | 28.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4694 buys / 1910 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/c1gr6idrfxx3neg8qckak452qtnbiu4orzm13nrzt4i8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flying-tesla-dogester-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
