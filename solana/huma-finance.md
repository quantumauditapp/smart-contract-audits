---
token: Huma Finance
ticker: HUMA
network: solana
risk_score: 40
status: medium
date: 2026-10-27
---

# Huma Finance (HUMA) — Smart Contract Security Analysis | Solana

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/huma-finance-sol)

---

## Audit Summary

The Huma Finance token mint has successfully revoked both mint and freeze authorities, ensuring supply stability and preventing account freezing. However, the protocol faces significant economic risks due to 99.8% of liquidity being held in an unlocked wallet by the pool creator and high holder concentration. Third-party registry data indicates concerns regarding metadata mutability and ownership distribution.

> **Final Recommendation:** Investors should monitor the pool creator's wallet (6vPq6V…wV8k) for any movement of the 99.8% unlocked liquidity. We recommend that the project team move this liquidity to a time-locked contract or burn the LP tokens to mitigate the risk of a sudden liquidity withdrawal.

Additionally, holders should be aware that the metadata is mutable. Verify the token's identity and branding through official channels before interacting with the asset, as the name or symbol could be altered by the current owner.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is inherent to the… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are elevated due to high holder concentration, with the top 10 holders controlling 76.48% of the supply. 7.6 External liquidity data shows $653,779 in TVL, but… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to the SPL mint logic itself, but 7.8 Operations are impacted by mutable metadata. The token metadata can be modified by the current owner, which may affect branding… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 3 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Pool Creator Can Withdraw Liquidity  *(Severity: High · Status: Unresolved)*

99.8% of the pool's liquidity is held, unlocked, by the wallet that created the pool (6vPq6V…wV8k). It can remove that liquidity at any moment and leave holders unable to sell.

**Recommendation:** Watch that wallet's liquidity position; treat the pool as removable until the liquidity is burned or locked.


### `H-02` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 76.48% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder wallet activity for potential large-scale sell pressure.


### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.8% is held, unlocked, by the wallet that created this pool (6vPq6V…wV8k) — it can pull that liquidity at any moment. This is the rug-pull path. This assessment covers the main pool, which holds 72% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 76.5% of supply. What remains: 4.7% in wallets, 71.8% in other contracts. 21,780 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Huma Finance (HUMA), market cap $36M, rank #563. 21,780 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $911K (DexScreener, all pools). 24h trading volume $71.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $498K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $911K of DEX liquidity across 13 pools. Launch: 519 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HUMA18...wvGw`](https://solscan.io/account/HUMA1821qVDKta3u2ovmfDQeW2fSQouSKE8fkF44wvGw) |
| **Network** | Solana |
| **Price** | $0.02619 |
| **24h Volume** | $334.3K |
| **Liquidity** | $659.0K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 76.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2249 buys / 1377 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3fx6tczy9t11i6frvr3dwjy3h7wi9yaso8os8utqshdx)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/huma-finance-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
