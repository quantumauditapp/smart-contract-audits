---
token: Trump Media & Technology Group Corp. Common Stock - Backpack Securities
ticker: DJT
network: solana
risk_score: 84
status: high
date: 2026-09-15
---

# Trump Media & Technology Group Corp. Common Stock - Backpack Securities (DJT) — Smart Contract Security Analysis | Solana

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trump-media-technology-group-corp-common-stock-backpack-securities-sol)

---

## Audit Summary

This SPL Token Mint exhibits critical security risks due to multiple unrevoked authorities, including mint, freeze, and a permanent delegate, which allow for arbitrary control over token supply and user funds. High holder concentration and a very new DEX pair also indicate significant market volatility and immaturity. Holder distribution data from chain-native RPC was unavailable for a complete assessment.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the mint authority, freeze authority, and permanent delegate have all been revoked. The presence of these unrevoked authorities means the token issuer retains full control over the token supply and user funds. Monitor holder distribution closely for any changes that could further concentrate supply. Given the newness of the DEX pair, observe trading patterns and liquidity over a longer period to establish a more reliable market assessment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is an SPL Token-2022 mint, indicating modern Solana token standards. However, the mint authority (3zbLadZi7cn7A6SavYkKah2QzUQEGNDtwmf5o17Rx17G) remains active, allowing for unlimited new… |
| **Governance / Economics** | 2/10 | High | The token exhibits high holder concentration, with the top 10 accounts holding 70.55% of the total supply, posing a significant risk of price manipulation or sudden sell-offs. The DEX pair is very… |
| **Upgrades** | 1/10 | High | The token's metadata is mutable, meaning the token name, symbol, or image can be changed post-launch. The token program is `spl-token-2022`, which supports various extensions, but no transfer hook is… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 1 High · 🟡 3 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 3zbLadZi7cn7A6SavYkKah2QzUQEGNDtwmf5o17Rx17G. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

Top 10 token accounts hold 70.55% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the fee in any swap calculation.


### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 5 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Account for the fee in any swap calculation.


### `M-02` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Account for the fee in any swap calculation.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 54.0% of supply. What remains: 54.0% in wallets, 0.0% in other contracts.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Trump Media & Technology Group Corp. Common Stock (Backpack Securities) (DJT), market cap $1M, rank #2792.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $421K (DexScreener, all pools). 24h trading volume $3.0M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $421K of DEX liquidity across 9 pools. Launch: 5 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DJTu7v...xvoF`](https://solscan.io/account/DJTu7vi8norVzdVAffgvb39VP7wjKeTsgaMBJrzfxvoF) |
| **Network** | Solana |
| **Price** | $9.0760 |
| **24h Volume** | $3.02M |
| **Liquidity** | $250.8K |
| **Volume / Liquidity** | 12.0× |
| **Token Age** | 5d |
| **Top-10 Holders** | 54.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12560 buys / 11237 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7gkb2d1sqhuygkrspdu5cma4tk9efijhouyituabdjcg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trump-media-technology-group-corp-common-stock-backpack-securities-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
