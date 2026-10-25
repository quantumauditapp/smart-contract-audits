---
token: Orderly Network
ticker: ORDER
network: solana
risk_score: 76
status: high
date: 2026-10-25
---

# Orderly Network (ORDER) — Smart Contract Security Analysis | Solana

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orderly-network-sol)

---

## Audit Summary

The Orderly Network (ORDER) token mint retains active Mint and Freeze authorities, posing significant centralization risks. Third-party registries have flagged the token for metadata and symbol mismatches, and metadata remains mutable. Holder concentration and liquidity data were analyzed, though specific lock status for pool liquidity was unavailable.

> **Final Recommendation:** Holders should monitor the Mint and Freeze authority addresses for potential revocation transactions. Given the mutable metadata, verify the token's identity against official project channels before performing any transactions.

Users should exercise caution regarding the active Freeze authority, which allows the controller to restrict token transfers. Verify the current liquidity lock status through block explorers to ensure the pool creator cannot withdraw the underlying assets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token utilizes the standard spl-token program (7.1 Architecture). Access control is centralized, with both Mint and Freeze authorities held by the same address (7.3 Access Control). The mint is… |
| **Governance / Economics** | 2/10 | High | The top 10 holders that can sell control 24.08% of the supply (7.5 Governance). Liquidity is $201,155 with a 24h volume of $1,839,454, resulting in a volume/liquidity ratio of 9.14 (7.4 Economic).… |
| **Upgrades** | 3/10 | High | Metadata is mutable, allowing for potential changes to the token's branding (7.7 Upgrades). The mint and freeze authorities are not revoked, allowing for potential supply expansion or account… |

## Security Findings

_🔴 2 Critical · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is Efvf2QfcPAJc8XCd1MV1MN1JLNDZRKj2ZbJ3xg6pAf7. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is Efvf2QfcPAJc8XCd1MV1MN1JLNDZRKj2ZbJ3xg6pAf7. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch as metadata_mutable is True.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; freeze or blacklist individual addresses; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Third-Party Registry Flag  *(Severity: Low · Status: Unresolved)*

Third-party risk registry signals indicate Symbol Mismatch and Name Mismatch.

**Recommendation:** Cross-reference the token identity with official project documentation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.6% of supply. Of that, 67.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.0% in wallets, 1.1% in other contracts. 691 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Orderly (ORDER), market cap $24M, rank #756. 691 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $212K (DexScreener, all pools). 24h trading volume $314.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $212K of DEX liquidity across 4 pools. Launch: 691 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ABt79M...iQ6E`](https://solscan.io/account/ABt79MkRXUsoHuV2CVQT32YMXQhTparKFjmidQxgiQ6E) |
| **Network** | Solana |
| **Price** | $0.0572 |
| **24h Volume** | $1.79M |
| **Liquidity** | $198.5K |
| **Volume / Liquidity** | 9.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 91.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14502 buys / 16255 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bxuigngqxhu8wapwvck5cavcbbfge47etnwlexncvwz4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orderly-network-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
