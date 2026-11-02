---
token: Hims & Hers Health - Backpack Securities
ticker: HIMS
network: solana
risk_score: 78
status: high
date: 2026-11-02
---

# Hims & Hers Health - Backpack Securities (HIMS) — Smart Contract Security Analysis | Solana

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hims-hers-health-backpack-securities-sol)

---

## Audit Summary

The HIMS token exhibits critical centralization risks due to active mint, freeze, and permanent delegate authorities. Third-party registries have flagged the token as high-risk due to these control vectors and mutable metadata. All data sources were successfully retrieved.

> **Final Recommendation:** Investors should exercise extreme caution due to the presence of a permanent delegate and active freeze authority. Verify the current status of these authorities on-chain before interacting with the token.

Monitor the mint and freeze authority addresses for potential revocation. Avoid holding significant positions until the permanent delegate is removed or the token is transitioned to a decentralized governance model.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token utilizes the Token-2022 program. 7.1 Architecture is standard for SPL, but 7.3 Access Control is highly centralized. The mint authority (AQGfwos...) and freeze authority (2cVYpag...) remain… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic analysis shows top 10 holders control 33.38% of supply. 7.5 Governance is centralized under the authority holders. Liquidity is $179,009 with a 54-day pair age, indicating moderate… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are not applicable to SPL mints, but 7.8 Operations are affected by mutable metadata. Metadata can be changed at any time by the owner. The transfer hook is also marked as upgradable. |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 4 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is AQGfwosRHg8uZGf7cCPe1yax8fVoWKnW6r3odYVJuC31. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on developer history and authority control.

**Recommendation:** Do not interact with this token.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; change any holder's balance (seize or credit tokens); freeze or blacklist individual addresses; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

GoPlus balance_mutable is set to True, indicating an authority can adjust user balances.

**Recommendation:** Review the token program configuration to identify the specific authority responsible for balance adjustments.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 66.5% of supply. Of that, 33.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.4% in wallets, 21.9% in other contracts. 16,640 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Hims & Hers Health (Backpack Securities) (HIMS), rank #4105. 16,640 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $435K (DexScreener, all pools). 24h trading volume $1.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $4.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $435K of DEX liquidity across 29 pools. Launch: launched on pump.fun (PumpSwap), 54 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HiMSSz...7Lwx`](https://solscan.io/account/HiMSSzzwkZkrXJ4PGVJRdtfLaANeAztjjcgk5Dxe7Lwx) |
| **Network** | Solana |
| **Price** | $25.2300 |
| **24h Volume** | $781.7K |
| **Liquidity** | $176.7K |
| **Volume / Liquidity** | 4.4× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 66.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3814 buys / 3144 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7iqwwnjubstjmwxk9eyjvidlzjbn2kjryt5z9j8n8exq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hims-hers-health-backpack-securities-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
