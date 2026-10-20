---
token: Octokn
ticker: OTK
network: solana
risk_score: 43
status: medium
date: 2026-10-10
---

# Octokn (OTK) — Smart Contract Security Analysis | Solana

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/octokn-sol)

---

## Audit Summary

The Octokn (OTK) SPL token mint has revoked its mint and freeze authorities, preventing further token creation or account freezing. However, a significant portion of the supply (63.27%) is concentrated among the top ten holders that can sell, posing a risk of price volatility from large sell-offs. Additionally, the token's metadata is mutable, allowing for changes to its name, symbol, or image post-launch. Information regarding the locking status of the pool's liquidity was unavailable.

> **Final Recommendation:** Holders should monitor the wallets of the top ten token holders for any significant movements that could indicate an impending sell-off, given the high concentration. Due to the mutable metadata, it is advisable to periodically verify the token's branding and details against official sources to ensure consistency. Before making significant investments, consider the implications of the concentrated supply and the unknown status of the pool's liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The SPL token mint operates on the spl-token program. Both the mint authority and freeze authority have been revoked, preventing further token issuance or freezing of holder accounts. The token has a… |
| **Governance / Economics** | 4/10 | Medium | The economic stability of the Octokn token is influenced by its holder distribution and liquidity. The top 10 holders that can sell control 63.27% of the total supply, indicating a significant… |
| **Upgrades** | 8/10 | Low | The token's core authorities, Mint Authority and Freeze Authority, have been revoked, meaning no further tokens can be minted and no accounts can be frozen. While the token does not employ Token-2022… |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 63.27% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the risk of significant price volatility due to potential large sell-offs from concentrated holders.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 63.3% of supply. What remains: 60.2% in wallets, 3.1% in other contracts. 12,484 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Octokn (OTK), market cap $2M, rank #2428. 12,484 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $756K (CoinGecko, all markets, daily snapshot). 24h trading volume $145K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.119 on 2024-03-20; the price is now 98.2115% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26K of DEX liquidity across 5 pools. Launch: 1186 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`octo82...PTqJ`](https://solscan.io/account/octo82drBEdm8CSDaEKBymVn86TBtgmPnDdmE64PTqJ) |
| **Network** | Solana |
| **Price** | $0.002325 |
| **24h Volume** | $131.5K |
| **Liquidity** | $16.8K |
| **Volume / Liquidity** | 7.8× |
| **Token Age** | 3y |
| **Top-10 Holders** | 63.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1204 buys / 770 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/df7vwhjqxnvtqacxidbfyba8ogaai7oqtgvsw7jyphhd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/octokn-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
