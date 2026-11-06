---
token: ProShares UltraPro Short QQQ - Backpack Securities
ticker: SQQQ
network: solana
risk_score: 75
status: high
date: 2026-11-06
---

# ProShares UltraPro Short QQQ - Backpack Securities (SQQQ) — Smart Contract Security Analysis | Solana

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/proshares-ultrapro-short-qqq-backpack-securities-sol)

---

## Audit Summary

The token exhibits significant centralization risks due to active Mint, Freeze, and Permanent Delegate authorities. While liquidity is sufficient for current volume, the presence of a permanent delegate allows for unauthorized fund transfers, and the mint authority permits unlimited supply inflation. Third-party registry data confirms these high-risk configurations.

> **Final Recommendation:** Investors should exercise extreme caution due to the Permanent Delegate and Freeze Authority. Verify the identity of the authority holders before interacting with the token, as these keys have total control over user balances and transfer capabilities.

Monitor the mint address on-chain to check for future revocation of authorities. If the authorities are not renounced, the token should be treated as a custodial asset rather than a decentralized one.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token utilizes the Token-2022 program, incorporating advanced extensions. 7.1 Architecture relies on a centralized authority model. 7.2 Code Security is not applicable as this is a standard SPL… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic factors show a healthy $237,991 liquidity pool with a 42-day history. 7.5 Governance is centralized, with top 10 holders controlling 13.38% of the supply. The volume/liquidity ratio of… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are not applicable in the EVM sense, but 7.3 Access Control allows for metadata mutability. The token metadata can be changed by the owner at any time. No authority revocation has… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is EzHCq2gnCdFaeZcAf9ujd3a84ZzzmCRwGcUqLhFBKsUE. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


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

GoPlus balance_mutable is True, indicating a balance-mutating authority can adjust user balances.

**Recommendation:** Review the token program configuration to identify the scope of balance mutation.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Metadata is mutable, meaning the token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.7% of supply. Of that, 27.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.2% in wallets, 14.7% in other contracts. 9,625 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

9,625 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $323K (DexScreener, all pools). 24h trading volume $2.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $323K of DEX liquidity across 30 pools. Launch: 42 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`SQQQAa...WaGE`](https://solscan.io/account/SQQQAa3gUxgnqcEsdjPA4RQNQBgB97TnG2hJhk2WaGE) |
| **Network** | Solana |
| **Price** | $47.2300 |
| **24h Volume** | $1.20M |
| **Liquidity** | $231.3K |
| **Volume / Liquidity** | 5.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 48.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8561 buys / 8552 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7f5tkjyfn6tb1bdxlsnzjqeo5hthvrue4ilja82a1zxt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/proshares-ultrapro-short-qqq-backpack-securities-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
