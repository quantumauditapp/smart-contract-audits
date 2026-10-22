---
token: Jason Duval
ticker: JASON
network: solana
risk_score: 21
status: low
date: 2026-10-22
---

# Jason Duval (JASON) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jason-duval-sol-7264)

---

## Audit Summary

The Jason Duval (JASON) token is a Token-2022 asset with revoked mint and freeze authorities, which provides a baseline of security for supply and transferability. However, the token is flagged as high-risk by a third-party registry due to the creator's history of rug-pulling, and the liquidity pool's lock status is unknown. These factors, combined with a 3% transfer fee, necessitate extreme caution.

> **Final Recommendation:** Investors should treat this token as high-risk due to the third-party registry warnings regarding the creator's history. Before interacting, verify the liquidity pool's lock status on-chain to ensure the creator cannot withdraw the pool's assets.

Monitor the top holder wallets for any signs of coordinated selling, as the 16.45% concentration could impact market stability. Do not rely on the token's branding, as the third-party registry flag suggests a pattern of deceptive practices.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with 7.1 Architecture standards. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.2 Code Security is maintained via immutable… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows a 16.45% concentration among the top 10 sellable holders, which is relatively distributed. 7.6 External data indicates a $20,973 liquidity depth, though the lock status of… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not utilize proxy patterns. The token metadata and transfer fee configurations are immutable, preventing post-launch changes to branding or fee… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | 3.0% (immutable) |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 4 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on the developer's history of rugged tokens.

**Recommendation:** Do not interact with this token.


### `H-01` — High Transfer Fee  *(Severity: High · Status: Unresolved)*

Every transfer pays 3.00% to the fee authority. Trading is materially more expensive than the apparent price.

**Recommendation:** Account for the 300 bps fee in any swap calculation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.8% of supply. Of that, 80.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 16.5% in wallets, 0.0% in other contracts. 28 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

28 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $32K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 1 pools. Launch: 71 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`wKy6tE...hNbA`](https://solscan.io/account/wKy6tEDZj6jS1GUMmnSSTrR1bXJQa35s7VHcWHxhNbA) |
| **Network** | Solana |
| **Price** | $0.00004213 |
| **24h Volume** | $32.0K |
| **Liquidity** | $22.0K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 96.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 265 buys / 115 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/i6gkgadg8je9qxwriqjmieu1ctpyy7dyf2rztafkkjz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jason-duval-sol-7264)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
