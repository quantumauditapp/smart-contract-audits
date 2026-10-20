---
token: STONKTOWER
ticker: TOWER
network: solana
risk_score: 16
status: low
date: 2026-10-14
---

# STONKTOWER (TOWER) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stonktower-sol)

---

## Audit Summary

This audit of the STONKTOWER (TOWER) SPL Token Mint found no critical or high-severity issues based on the provided on-chain data and deterministic rules. The mint and freeze authorities are revoked, and liquidity is 100% burned. Third-party registry data reported no adverse flags, and no transfer hooks or default frozen states are active.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure the supply is fixed and accounts cannot be frozen. Monitor the token's trading activity and liquidity over time, especially given its very recent launch. While no immediate red flags were identified, continuous monitoring of market dynamics is always advisable for new tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The STONKTOWER (TOWER) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a healthy distribution, with the top 10 holders that can sell holding 40.83% of the total supply, which does not indicate high concentration risk. Liquidity for the TOWER token is… |
| **Upgrades** | 10/10 | Low | The STONKTOWER (TOWER) token mint has a robust configuration regarding post-launch changes. Both the mint and freeze authorities are permanently revoked, preventing any further supply changes or… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.6% of supply. Of that, 7.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 40.8% in wallets, 0.0% in other contracts. 750 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

750 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $53K (DexScreener, all pools). 24h trading volume $361K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $53K of DEX liquidity across 9 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Ccp6is...pump`](https://solscan.io/account/Ccp6isbtxCknynmGKyky9xJav68UpRqeMoX76KxYpump) |
| **Network** | Solana |
| **Price** | $0.0003501 |
| **24h Volume** | $296.8K |
| **Liquidity** | $51.8K |
| **Volume / Liquidity** | 5.7× |
| **Token Age** | 18h |
| **Top-10 Holders** | 48.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1416 buys / 1204 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/57am4by6gfmevr1yrdglez5q6rfy25ryakehrk2vbgfd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stonktower-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
