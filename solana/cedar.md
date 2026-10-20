---
token: Cedar
ticker: CDR
network: solana
risk_score: 17
status: low
date: 2026-10-04
---

# Cedar (CDR) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cedar-sol)

---

## Audit Summary

This audit of the Cedar (CDR) SPL token mint identifies a medium risk due to the entire DEX liquidity pool being unlocked and held by a single program account, which could be withdrawn at any time. Additionally, the token's metadata is mutable, allowing for changes to its name, symbol, or image post-launch. Third-party registry data indicated single holder ownership and mutable metadata, while chain-native RPC data for holder distribution was unavailable.

> **Final Recommendation:** Holders should monitor the liquidity provider's wallet (2sV6GC…A2D8) for any movements of the 100.0% unlocked liquidity, as its withdrawal would severely impact market stability. Before relying on the token's branding, verify its metadata against official sources, as the `metadata_mutable` flag indicates it can be changed post-launch. Acknowledge that the top 10 holders control a notable portion of the supply, which could influence price volatility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Cedar (CDR) token is an SPL token operating under the `spl-token` program. Key authorities, including the Mint Authority and Freeze Authority, have been revoked, indicating a fixed supply and… |
| **Governance / Economics** | 2/10 | High | The economic profile shows a moderate holder concentration, with the top 10 holders that can sell accounting for 37.75% of the total supply. The token has a healthy liquidity of $439,675 USD, with a… |
| **Upgrades** | 8/10 | Low | The token's core authorities, Mint Authority and Freeze Authority, are revoked, preventing further minting or freezing of accounts. While the token does not use Token-2022 specific upgradeable… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

Only 0.0% of the pool's liquidity is burned or locked; 100.0% is held, unlocked, by a program account (2sV6GC…A2D8) which can remove that share at once. Who controls this program account is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Watch the program account (2sV6GC…A2D8) that holds the liquidity; treat the pool as removable until the liquidity is burned or locked.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the pool's creator. One of them — a program account, 2sV6GC…A2D8 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 45.0% of supply. Of that, 7.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.4% in wallets, 26.4% in other contracts. 5,605 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Cedar (CDR), market cap $3M, rank #2068. 5,605 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $440K (DexScreener, all pools). 24h trading volume $85K (CoinGecko, all markets, daily snapshot). 24h trading volume $79K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $440K of DEX liquidity across 1 pools. Launch: 420 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HZqjje...6o9C`](https://solscan.io/account/HZqjjeso24PDVdLsVJQyVb8kDnbo7HhXfY1Jane66o9C) |
| **Network** | Solana |
| **Price** | $0.00368 |
| **24h Volume** | $78.7K |
| **Liquidity** | $439.7K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 45.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 104 buys / 68 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/e36cuejlfpybptqixlam9avgejtqg4vs2aard41jxnld)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cedar-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
