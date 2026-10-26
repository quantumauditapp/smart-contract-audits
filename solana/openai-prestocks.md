---
token: OpenAI PreStocks
ticker: OPENAI
network: solana
risk_score: 84
status: high
date: 2026-09-12
---

# OpenAI PreStocks (OPENAI) — Smart Contract Security Analysis | Solana

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/openai-prestocks-sol)

---

## Audit Summary

This SPL Token Mint exhibits critical centralization risks due to active Mint, Freeze, and Permanent Delegate authorities, all held by WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc. These authorities allow for arbitrary supply changes, asset freezing, and direct fund transfers. Additionally, holder concentration is very high, with the top 10 accounts holding 88.72% of the supply. Third-party risk registry data was available, but detailed holder distribution from chain-native RPC was not.

> **Final Recommendation:** Prospective holders should verify on-chain that the Mint Authority, Freeze Authority, and Permanent Delegate have been revoked to ensure the supply is fixed and funds cannot be frozen or moved without consent. Given the high holder concentration, monitor on-chain movements of large holders for potential sell-offs. Be aware that the token's metadata and transfer fee settings can be changed, and an authority can adjust balances, requiring continuous vigilance regarding the token's configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is an SPL Token-2022 mint with a total supply of 1,902,072,264.97 tokens (9 decimals). Critical authorities are active: the Mint Authority, Freeze Authority, and Permanent Delegate are all… |
| **Governance / Economics** | 1/10 | High | Holder concentration is extremely high, with the top 10 token accounts holding 88.72% of the total supply, indicating significant centralization risk. The token has a liquidity of $237,126 USD, with… |
| **Upgrades** | 1/10 | High | The token's metadata, including name, symbol, or image, is mutable, allowing for post-launch changes. The transfer fee and transfer hook configurations are also upgradable. The balance_mutable flag… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🔴 3 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

Top 10 token accounts hold 88.72% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the risk of large-holder sell-offs when considering this token.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Be aware that an authority exists that can modify user balances, which could lead to unexpected changes in holdings.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 87.9% of supply. What remains: 87.9% in wallets, 0.0% in other contracts.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as OpenAI PreStocks (OPENAI), market cap $4M, rank #1846.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $229K (DexScreener, all pools). 24h trading volume $439K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Pre-IPO Stocks. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $229K of DEX liquidity across 11 pools. Launch: 196 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`PreweJ...rpgF`](https://solscan.io/account/PreweJYECqtQwBtpxHL171nL2K6umo692gTm7Q3rpgF) |
| **Network** | Solana |
| **Price** | $1,700.7100 |
| **24h Volume** | $438.8K |
| **Liquidity** | $157.7K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 87.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3737 buys / 14115 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4hty7atjpm5ptsews2ywrdpx6gjwm6sc2dv5mv9u8jsh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/openai-prestocks-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
