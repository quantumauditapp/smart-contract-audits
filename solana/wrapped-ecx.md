---
token: Wrapped ECX
ticker: WECX
network: solana
risk_score: 67
status: high
date: 2026-10-29
---

# Wrapped ECX (WECX) — Smart Contract Security Analysis | Solana

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-ecx-sol)

---

## Audit Summary

The token is managed via the standard SPL Token program. Key risks include an active mint authority allowing for supply inflation and a third-party registry flagging the token as a copycat with high holder concentration. Third-party risk registry data was successfully retrieved.

> **Final Recommendation:** Monitor the mint authority address for potential revocation to eliminate the risk of supply inflation. Verify the token's branding and metadata against official sources to ensure the 'copycat' flag does not indicate a fraudulent project.

Exercise caution regarding the high holder concentration. Before interacting with the token, confirm the liquidity locking status through a block explorer to ensure the pool creator cannot withdraw the majority of the liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token utilizes the standard SPL Token program (7.1 Architecture). The freeze authority is successfully revoked (7.3 Access Control), preventing account freezing. However, the mint authority… |
| **Governance / Economics** | 6/10 | Medium | The top 10 holders control 51.70% of the supply (7.4 Economic), indicating significant concentration. Liquidity is healthy at $821,200 with a stable volume/liquidity ratio of 0.43 (7.4 Economic). The… |
| **Upgrades** | 6/10 | Medium | The token metadata is mutable (7.7 Upgrades), allowing for potential changes to the token name or symbol. There are no upgradeable proxy patterns or complex logic modules (7.7 Upgrades). The mint… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 6Av9JtnZGADBATo3uyLVC12XojJYKJhZxv578cJR2sKT. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Holder Concentration > 50%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 51.70% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder wallet activity for large sell orders.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Low · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset (developer history, LP movements).

**Recommendation:** Do not interact with this token.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 88.4% of supply. Of that, 36.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 48.2% in wallets, 3.5% in other contracts. 902 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

902 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $841K (DexScreener, all pools). 24h trading volume $432K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $841K of DEX liquidity across 15 pools. Launch: 17 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 17 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 17 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6ombVv...YMVY`](https://solscan.io/account/6ombVv3YMs9qpx1QkycD9XW8HKSfv7vGrCFX3cxCYMVY) |
| **Network** | Solana |
| **Price** | $117.7300 |
| **24h Volume** | $348.8K |
| **Liquidity** | $820.1K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 17d |
| **Top-10 Holders** | 88.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2775 buys / 2438 sells |

## Security Flags (2/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/7t4xaj1eneupckhwqz6njp9zkvdnfpvf7nlbuavswm43)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-ecx-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
