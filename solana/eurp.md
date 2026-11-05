---
token: EURØP
ticker: EUROP
network: solana
risk_score: 81
status: high
date: 2026-11-05
---

# EURØP (EUROP) — Smart Contract Security Analysis | Solana

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/eurp-sol)

---

## Audit Summary

The EURØP token utilizes the Token-2022 program with significant centralized control mechanisms enabled. The presence of an active mint authority, freeze authority, and a permanent delegate creates critical risks for token holders. Third-party risk registry data confirms these findings, flagging the token as high-risk due to developer-controlled authorities.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of authority revocation. Verify on-chain that the mint and freeze authorities are set to null before considering the token supply fixed or the accounts secure.

Monitor the addresses 3t3X4xqXbRDksat5cPjfHoWftvTwpHEj9c7tWMVvNPAh and 28o3KhjN6kd1YHN8LXiZ8i9d2dcCjbwna2rGZz3pGcKW for any activity. Avoid holding significant positions until the permanent delegate is removed and administrative authorities are renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is deployed using the Token-2022 program. 7.1 Architecture and 7.3 Access Control are compromised by the retention of mint and freeze authorities (3t3X...NPAh and 28o3...GcKW). 7.2 Code… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic analysis shows high holder concentration, with the top 10 holders controlling 86.14% of the supply. 7.5 Governance is non-existent, as control is held by specific addresses rather than a… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are not applicable in the traditional sense, but the token metadata is mutable, allowing for potential branding changes. The transfer fee configuration is also marked as upgradable.… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 3t3X4xqXbRDksat5cPjfHoWftvTwpHEj9c7tWMVvNPAh. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 28o3KhjN6kd1YHN8LXiZ8i9d2dcCjbwna2rGZz3pGcKW. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

28o3KhjN6kd1YHN8LXiZ8i9d2dcCjbwna2rGZz3pGcKW has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 86.14% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder wallet activity for potential liquidation events.


### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; change any holder's balance (seize or credit tokens); freeze or blacklist individual addresses; change the buy/sell tax; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

The GoPlus registry indicates balance_mutable is True, allowing an authority to adjust user balances.

**Recommendation:** Review the token program configuration to identify the specific authority capable of balance modification.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 13.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.4% in wallets, 85.7% in other contracts. 60 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as EURØP (EUROP), market cap $15M, rank #988. 60 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (DexScreener, all pools). 24h trading volume $2.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $3.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — backing unverified  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Its identity is not independently verified, so it gets none of the allowances an established stablecoin gets: every power its owner holds over supply and transfers is scored in full, because a peg is only as good as whoever can mint. Basis: CoinGecko category: EUR Stablecoin. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.2M of DEX liquidity across 2 pools. Launch: 66 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`euro5s...MftA`](https://solscan.io/account/euro5sNHrZC2wu2RoLvy6xxoVMc3Qnd1vjxoWf4MftA) |
| **Network** | Solana |
| **Price** | $1.1100 |
| **24h Volume** | $3.36M |
| **Liquidity** | $1.16M |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4196 buys / 4105 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fzg7qarl4xnu7s55jk7j3xjwp6ndcmttneq62h4nymld)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/eurp-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
