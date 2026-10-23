---
token: Anduril PreStocks
ticker: ANDURIL
network: solana
risk_score: 84
status: high
date: 2026-10-23
---

# Anduril PreStocks (ANDURIL) — Smart Contract Security Analysis | Solana

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anduril-prestocks-sol)

---

## Audit Summary

The token is governed by a single authority (WV9PJN7XTmTLVwbutCLFxp8TyePee6Xq5mRq6Fti5Wc) that retains mint, freeze, and permanent delegate capabilities, presenting a critical centralization risk. While liquidity is sufficient at $510,456, the lack of information regarding liquidity locking and the presence of high-privilege administrative controls necessitate extreme caution. All third-party registry data was successfully retrieved.

> **Final Recommendation:** Potential holders should monitor the mint authority address for any signs of renouncement. Given the presence of a permanent delegate and freeze authority, users should treat this token as a fully custodial asset. 

Verify the current status of the mint and freeze authorities on-chain before committing capital. Avoid holding large positions until the liquidity status is confirmed as locked or burned, as the current lack of transparency regarding liquidity withdrawal poses a significant risk to exit liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token utilizes the Token-2022 program, which enables advanced extensions. 7.1 Architecture is defined by the SPL-2022 standard. 7.2 Code Security is not applicable as this is a mint configuration… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic factors show a 1% transfer fee and $510,456 in liquidity. 7.5 Governance is non-existent, as all power resides with the mint authority. 7.6 External data indicates a 24h volume of… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are not applicable to SPL mints, but 7.8 Operations are affected by mutable metadata and upgradable fee/hook configurations. The metadata can be altered by the authority at any time.… |

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


### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; change any holder's balance (seize or credit tokens); freeze or blacklist individual addresses; change the buy/sell tax; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

GoPlus balance_mutable is set to True, meaning an authority can adjust user balances.

**Recommendation:** Monitor the token program configuration for changes to balance-related extensions.


### `M-02` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

The fact block does not confirm that the pool's liquidity is locked or burned, implying it may be withdrawable by the creator.

**Recommendation:** Verify the liquidity provider's lock status on-chain.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch as metadata_mutable is True.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 54.3% of supply. Of that, 10.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 37.3% in wallets, 6.4% in other contracts. 11,125 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Anduril PreStocks (ANDURIL), market cap $2M, rank #2353. 11,125 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $633K (DexScreener, all pools). 24h trading volume $4.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $3.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Pre-IPO Stocks. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $633K of DEX liquidity across 30 pools. Launch: 238 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`PresTj...BoQB`](https://solscan.io/account/PresTj4Yc2bAR197Er7wz4UUKSfqt6FryBEdAriBoQB) |
| **Network** | Solana |
| **Price** | $162.2100 |
| **24h Volume** | $3.54M |
| **Liquidity** | $509.7K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 54.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 33813 buys / 30006 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/aab2xatnjvdspbmfya82tvwlrjrjbmdgqnjymbpouu78)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anduril-prestocks-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
