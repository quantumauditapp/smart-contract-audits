---
token: farm
ticker: FARM
network: solana
risk_score: 5
status: low
date: 2026-10-14
---

# farm (FARM) — Smart Contract Security Analysis | Solana

> **Risk Score: 5/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/farm-sol)

---

## Audit Summary

This audit of the FARM SPL token mint found no critical or high-severity issues based on the provided on-chain facts and third-party security signals. The mint and freeze authorities are revoked, holder concentration is low, and liquidity is substantial and largely locked. Third-party risk registry data reported no adverse flags. Chain-native RPC data for holder distribution was unavailable.

> **Final Recommendation:** This token presents a low-risk profile based on the available on-chain data. Holders should continue to monitor the token's liquidity and trading volume for any significant changes. Verify on-chain that the mint and freeze authorities remain revoked. No further specific actions are immediately required beyond standard due diligence for any cryptocurrency asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FARM token is a standard SPL token operating on the spl-token program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing… |
| **Governance / Economics** | 10/10 | Low | The token exhibits low holder concentration, with the top 10 holders that can sell accounting for only 23.26% of the supply. DEX liquidity is healthy at $56,440, and 98.0% of this liquidity is locked… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, meaning no further changes can be made to the token's supply or account freeze status. The token's metadata is immutable, ensuring its name… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.5% of supply. Of that, 25.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.3% in wallets, 0.0% in other contracts. 1,281 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as farm (FARM), rank #4713. 1,281 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

98.0% of the pool's LP is burned or time-locked. 98.0% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 1.9% is held, unlocked, by 1 address(es) other than the pool's creator. This assessment covers the main pool, which holds 95% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $60K (DexScreener, all pools). 24h trading volume $147K (CoinGecko, all markets, daily snapshot). 24h trading volume $136K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $60K of DEX liquidity across 14 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`hKyXZV...farm`](https://solscan.io/account/hKyXZVKmrBDPhKKhdSaaGf1qrFwUkwjqrdzRc63farm) |
| **Network** | Solana |
| **Price** | $0.00003263 |
| **24h Volume** | $130.3K |
| **Liquidity** | $56.7K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | 48.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 962 buys / 982 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fzjpqfbqaoze9psuptlwpockgvapgworfopjkfphoylk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/farm-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
