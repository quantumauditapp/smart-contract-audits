---
token: Anthropic PreStocks
ticker: ANTHROPIC
network: solana
risk_score: 81
status: high
date: 2026-09-18
---

# Anthropic PreStocks (ANTHROPIC) — Smart Contract Security Analysis | Solana

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-prestocks-sol)

---

## Audit Summary

The BUTTHOLE SPL Token Mint exhibits critical centralization risks. The same address, WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc, retains mint, freeze, and permanent delegate authorities, allowing for unlimited token creation, account freezing, and direct fund transfers from user accounts. Additionally, the token features mutable balances and metadata. While holder distribution data was unavailable from one source, top 10 holder percentage was available from another.

> **Final Recommendation:** Before any interaction, verify on-chain that the mint authority has been revoked to prevent arbitrary supply inflation. Confirm the freeze authority is nullified to ensure funds cannot be frozen or confiscated. Given the permanent delegate authority, treat this token as fully custodial, as funds can be moved without user consent. Monitor for any changes to the mutable metadata, transfer fee, or balance mutability settings, as these can alter token behavior and value proposition.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The BUTTHOLE token is an SPL Token-2022 mint with a total supply of 7,381,916,322.152 tokens and 9 decimals. It utilizes the spl-token-2022 program, which supports advanced features. However, the… |
| **Governance / Economics** | 3/10 | High | The token has a healthy liquidity of $313,994 USD and a 24-hour trading volume of $55,457 USD, with a normal Volume/Liquidity Ratio of 0.18 (7.4 Economic). The DEX pair has been active for 43 days… |
| **Upgrades** | 1/10 | High | The token's mint authority, freeze authority, and permanent delegate are all active, indicating significant centralized control (7.7 Upgrades). The Token-2022 extensions include a transfer fee of… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🔴 3 Critical · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of a balance-mutating authority and its potential impact on token holdings.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.6% of supply. What remains: 48.6% in wallets, 0.0% in other contracts.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Anthropic PreStocks (ANTHROPIC), market cap $8M, rank #1360.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $344K (DexScreener, all pools). 24h trading volume $203K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Pre-IPO Stocks. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $344K of DEX liquidity across 14 pools. Launch: 154 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Pren1F...Lkhw`](https://solscan.io/account/Pren1FvFX6J3E4kXhJuCiAD5aDmGEb7qJRncwA8Lkhw) |
| **Network** | Solana |
| **Price** | $1,020.1800 |
| **24h Volume** | $203.2K |
| **Liquidity** | $195.2K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 48.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1138 buys / 7835 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ezyszdex1lzdt7tssfv8xdpi49sdkc3mdfv2mvmeqltu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-prestocks-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-18*
