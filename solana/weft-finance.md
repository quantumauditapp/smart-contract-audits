---
token: Weft Finance
ticker: WEFT
network: solana
risk_score: 16
status: low
date: 2026-10-19
---

# Weft Finance (WEFT) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/weft-finance-sol)

---

## Audit Summary

The Weft Finance (WEFT) SPL token mint has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. However, the token's metadata is mutable, allowing for post-launch changes to its name, symbol, or image. Third-party risk registry data was unavailable for this assessment, and the locking status of the liquidity pool could not be determined.

> **Final Recommendation:** Holders should monitor the token's metadata for any unexpected changes to its branding. While core authorities are revoked, the mutable metadata introduces a potential for brand misrepresentation. Verify the token's current name, symbol, and image against official sources before relying on its branding.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Weft Finance (WEFT) token operates under the standard `spl-token` program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no holder… |
| **Governance / Economics** | 7/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding 27.19% of the supply. The token has a liquidity of $162,126 USD, with a normal 24-hour volume to liquidity ratio of 3.06.… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, preventing further changes to supply or account freeze status. The token's metadata is mutable, meaning its name, symbol, or image can be… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 27.2% of supply. What remains: 23.5% in wallets, 3.7% in other contracts. 1,636 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,636 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $321K (DexScreener, all pools). 24h trading volume $2.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $321K of DEX liquidity across 10 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HqmFi8...6Ax8`](https://solscan.io/account/HqmFi85adLD8BQA7en1HfajdAfzVFps5REgQaYuw6Ax8) |
| **Network** | Solana |
| **Price** | $0.003081 |
| **24h Volume** | $480.9K |
| **Liquidity** | $153.8K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | 27.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2311 buys / 2858 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ajje4sn3r9htaxfkujdeyugyuv4shhat7utapd6k8oar)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/weft-finance-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
