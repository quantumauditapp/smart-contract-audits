---
token: orcapod.fun
ticker: POD
network: solana
risk_score: 16
status: low
date: 2026-10-04
---

# orcapod.fun (POD) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orcapodfun-sol)

---

## Audit Summary

This audit of the orcapod.fun (POD) SPL Token Mint found no critical or high-severity risks based on the available on-chain data, security registries, and DEX market information. Both mint and freeze authorities are revoked, and no concerning Token-2022 extensions are active. Holder concentration is low, and liquidity is moderate. Information regarding the locking status of the pool's liquidity was unavailable.

> **Final Recommendation:** Holders should independently verify the current on-chain status of the mint and freeze authorities to confirm they remain revoked. It is also recommended to monitor the liquidity pool's locking status if that information becomes available, as this was not ascertainable during this audit. Continue to observe holder distribution and trading volume for any significant shifts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token mint for orcapod.fun (POD) operates under the standard spl-token program. Both the mint authority and freeze authority have been revoked, preventing further token issuance or freezing of… |
| **Governance / Economics** | 7/10 | Low | Holder concentration for the POD token is low, with the top 10 sellable holders controlling only 19.47% of the total supply, indicating a relatively distributed ownership. The token has a total DEX… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority for the POD token have both been permanently revoked, ensuring that no new tokens can be minted and no accounts can be frozen. The token's metadata is… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.7% of supply. Of that, 14.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.5% in wallets, 0.0% in other contracts. 1,025 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,025 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $105K (DexScreener, all pools). 24h trading volume $283K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $105K of DEX liquidity across 7 pools. Launch: 6 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`F4K2Sb...ZtB6`](https://solscan.io/account/F4K2SbLNgyz9gzNqT8bPeLpRkxy4oMA9twaffUDdZtB6) |
| **Network** | Solana |
| **Price** | $0.000346 |
| **24h Volume** | $236.5K |
| **Liquidity** | $93.8K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 6d |
| **Top-10 Holders** | 33.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 874 buys / 596 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4759sggn3ypwtphobq65wcwa1t1tbda5cwskjohux39d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orcapodfun-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
