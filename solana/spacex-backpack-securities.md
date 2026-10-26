---
token: SpaceX - Backpack Securities
ticker: SPCX
network: solana
risk_score: 81
status: high
date: 2026-09-20
---

# SpaceX - Backpack Securities (SPCX) — Smart Contract Security Analysis | Solana

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-backpack-securities-sol)

---

## Audit Summary

This SPL Token Mint exhibits critical security risks due to the presence of a mint authority, freeze authority, and a permanent delegate, allowing for arbitrary token minting, freezing of accounts, and transfer of user funds without consent. Additionally, a balance-mutating authority is active, and metadata can be changed. Third-party registry data was available and confirmed these authority flags. Holder distribution data was partially available, showing top 10 holders at 33.88%.

> **Final Recommendation:** Before interacting with this token, it is crucial to verify on-chain that the mint authority has been permanently revoked to ensure a fixed supply. Given the active freeze authority and permanent delegate, users should be aware of the custodial risks, as funds can be frozen or moved without consent. Monitor the token's metadata for any unannounced changes to branding.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | This token is implemented using the spl-token-2022 program, indicating support for advanced extensions (7.1 Architecture). As an SPL token mint, there is no on-chain source code for traditional code… |
| **Governance / Economics** | 3/10 | High | The token has a total DEX liquidity of $843,054, with a 24-hour volume of $316,899, resulting in a normal Volume/Liquidity Ratio of 0.38. The DEX pair has been active for 99 days, providing some… |
| **Upgrades** | 1/10 | High | The token mint's core authorities, including mint and freeze authorities, are not revoked, allowing for potential changes to the token supply and account states (7.7 Upgrades). A permanent delegate… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is HK6jF79duLLLfCMRQFBSgo6CgQ5mF4tFMFU7CmKcXctZ. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Treat this token as having a potential for balance manipulation.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.6% of supply. What remains: 36.6% in wallets, 0.0% in other contracts.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SpaceX (Backpack Securities) (SPCX), market cap $10M, rank #1191.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.9M (DexScreener, all pools). 24h trading volume $430K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.9M of DEX liquidity across 26 pools. Launch: 99 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`SPCXxc...imGb`](https://solscan.io/account/SPCXxcqXj6e5dJDVNovHN8744zkbhM2bYudU45BimGb) |
| **Network** | Solana |
| **Price** | $151.5800 |
| **24h Volume** | $430.0K |
| **Liquidity** | $913.5K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 36.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1701 buys / 1593 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7nvqtyqipn564e9obi6yzfgox4wl6cr4zslyyipqgtwu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-backpack-securities-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*
