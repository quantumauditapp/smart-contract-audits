---
token: Neuralink PreStocks
ticker: NEURALINK
network: solana
risk_score: 84
status: high
date: 2026-10-21
---

# Neuralink PreStocks (NEURALINK) — Smart Contract Security Analysis | Solana

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/neuralink-prestocks-sol)

---

## Audit Summary

The token is highly centralized, with the mint, freeze, and permanent delegate authorities held by a single address. This configuration allows the authority to mint unlimited supply, freeze user accounts, and transfer any holder's tokens without consent. Third-party risk registry data confirms these high-risk flags.

> **Final Recommendation:** Do not hold this token due to the presence of a permanent delegate and active freeze authority. These features allow the controller to seize funds or restrict access at will.

Verify the current authority status on-chain using a block explorer. If the mint, freeze, and permanent delegate authorities are not set to null, the token remains fully custodial and subject to the controller's actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token utilizes the Token-2022 program, which supports advanced extensions. 7.1 Architecture is defined by the SPL-2022 standard. 7.3 Access Control is severely compromised as the mint, freeze… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic coverage shows a 1% transfer fee (100 bps) applied to all transactions. 7.5 Governance is non-existent, with 50.23% of supply held by the top 10 holders. 7.6 External data indicates… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are not applicable in the EVM sense, but 7.8 Operations are impacted by mutable metadata. The token allows for future changes to the transfer fee and transfer hook configurations, which… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🔴 3 Critical · 🟠 2 High · 🟡 2 Medium · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `H-01` — Holder Concentration > 50%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 50.23% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder wallet activity for large sell orders.


### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; change any holder's balance (seize or credit tokens); freeze or blacklist individual addresses; change the buy/sell tax; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

GoPlus balance_mutable == True indicates a balance-mutating authority can adjust user balances.

**Recommendation:** Exercise extreme caution as user balances are not immutable.


### `M-02` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

GoPlus metadata_mutable == True. Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.6% of supply. Of that, 23.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 40.3% in wallets, 7.1% in other contracts. 7,471 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

7,471 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $547K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $547K of DEX liquidity across 30 pools. Launch: 187 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`PrekqL...bw9S`](https://solscan.io/account/PrekqLJvJ3qVdXmBGDiexvwUTF4rLFDa6HWS4HJbw9S) |
| **Network** | Solana |
| **Price** | $418.7800 |
| **24h Volume** | $1.36M |
| **Liquidity** | $409.6K |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 70.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14560 buys / 13874 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/frxxhbgidg2v4bvzqtxggiijmg1bquw4cvxplsxn58wf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/neuralink-prestocks-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
