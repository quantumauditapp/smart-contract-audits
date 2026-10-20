---
token: NeuralAI
ticker: NEURAL
network: solana
risk_score: 71
status: high
date: 2026-09-30
---

# NeuralAI (NEURAL) — Smart Contract Security Analysis | Solana

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/neuralai-sol)

---

## Audit Summary

The NeuralAI token mint has a critical vulnerability: the mint authority is still active, allowing the creation of unlimited new tokens. This poses a severe risk of supply dilution. Additionally, the token's metadata can be changed post-launch. Third-party registry data regarding pool liquidity locking was unavailable, preventing a full assessment of liquidity risk.

> **Final Recommendation:** Before any interaction, verify on-chain that the mint authority for the token has been permanently revoked to prevent future supply dilution. Monitor the token's metadata for any unexpected changes, as it can be modified by the controlling authority. If the mint authority is not revoked, consider the token highly risky due to the potential for infinite inflation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The NeuralAI token is an SPL token operating on the Solana blockchain, utilizing the `spl-token` program. A critical risk exists as the mint authority, held by… |
| **Governance / Economics** | 6/10 | Medium | Holder concentration is moderate, with the top 10 holders that can sell controlling 36.02% of the supply. The token has a healthy liquidity of $122,001 USD and a normal 24-hour volume to liquidity… |
| **Upgrades** | 5/10 | Medium | The mint authority is still active, posing a critical risk of supply manipulation. While the freeze authority has been revoked, which is a positive security measure, the token's metadata, including… |

## Security Findings

_🔴 1 Critical · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is EnHR9kZbKcFJ9xxWqc4pjZqFvwRHb3TNJtQCbtLvqxAH. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 40.1% of supply. Of that, 4.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 36.0% in wallets, 0.0% in other contracts. 1,255 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as NEURALAI (NEURAL), market cap $28M, rank #743. 1,255 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $120K (DexScreener, all pools). 24h trading volume $1.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $313K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $120K of DEX liquidity across 2 pools. Launch: 454 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BNC5eV...h2cZ`](https://solscan.io/account/BNC5eVJZixJFykygncDuUK5TpRBsWZuT6eSA99YNh2cZ) |
| **Network** | Solana |
| **Price** | $2.5200 |
| **24h Volume** | $309.6K |
| **Liquidity** | $116.6K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 40.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 660 buys / 760 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bnchsylfy3jelv2zyuf3hf6ncdxfcfle2knnvewzz9fl)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/neuralai-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
