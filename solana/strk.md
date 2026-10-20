---
token: STRK
ticker: STRK
network: solana
risk_score: 43
status: medium
date: 2026-10-09
---

# STRK (STRK) — Smart Contract Security Analysis | Solana

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/strk-sol)

---

## Audit Summary

The STRK token mint presents critical risks due to an unrevoked mint authority, allowing for unlimited token creation and potential dilution. A third-party risk registry also flags a large amount of unlocked liquidity, and the token's metadata is mutable. These factors indicate significant control retained by the issuer, posing risks to token holders. Third-party registry data was available and contributed to the assessment.

> **Final Recommendation:** Before any interaction, verify on-chain that the mint authority `FvULawNPGBbuwYus74ECaQoV1oH9Tk6XPN7VPN51NYds` has been permanently revoked to ensure the token supply is fixed. Monitor the liquidity provider wallets for any large withdrawals, as a significant portion of the pool's liquidity is reported as unlocked. Confirm the token's metadata (name, symbol, image) matches expectations, as it can be changed at any time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The STRK token is an SPL token operating on the `spl-token` program. A critical risk exists as the mint authority, `FvULawNPGBbuwYus74ECaQoV1oH9Tk6XPN7VPN51NYds`, is not revoked, enabling the… |
| **Governance / Economics** | 6/10 | Medium | The token exhibits a holder concentration where the top 10 holders that can sell account for 49.40% of the supply. Total DEX liquidity stands at $414,749, with a 24-hour volume of $2,614,239… |
| **Upgrades** | 5/10 | Medium | The mint authority remains active, allowing for potential future supply changes, which is a critical upgrade-like capability. While the freeze authority is revoked, the token's metadata is mutable… |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is FvULawNPGBbuwYus74ECaQoV1oH9Tk6XPN7VPN51NYds. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value. This fact is also flagged by a third-party risk registry.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry indicates a large amount of the pool's liquidity is unlocked. This means a significant portion can be withdrawn by whoever holds it, potentially impacting market stability.

**Recommendation:** Monitor the liquidity provider wallets for any large withdrawals.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`. This fact is also flagged by a third-party risk registry.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 82.6% of supply. Of that, 33.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 49.4% in wallets, 0.0% in other contracts. 571 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Starknet (STRK), market cap $489M, rank #118. 571 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $833K (DexScreener, all pools). 24h trading volume $329.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $5.0M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $4.41 on 2024-02-20; the price is now 98.5073% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $833K of DEX liquidity across 14 pools. Launch: 266 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HsRpHQ...SCoz`](https://solscan.io/account/HsRpHQn6VbyMs5b5j5SV6xQ2VvpvvCCzu19GjytVSCoz) |
| **Network** | Solana |
| **Price** | $0.07448 |
| **24h Volume** | $2.51M |
| **Liquidity** | $411.6K |
| **Volume / Liquidity** | 6.1× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 82.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4941 buys / 9014 sells |

## Security Flags (2/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/eq9tfrmhq2y7pu9cp1j8wfqmtqwxcm6kqg3e8xqhaxug)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/strk-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
