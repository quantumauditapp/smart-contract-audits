---
token: GULD
ticker: GULD
network: base
risk_score: 60
status: medium
date: 2026-10-31
---

# GULD (GULD) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/guld-base)

---

## Audit Summary

The protocol implements a standard ERC-20 token with centralized minting capabilities. The architecture is straightforward and follows standard patterns for ownership and supply management. While the code is secure and well-structured, the centralized control over token issuance represents a significant economic risk to token holders.

> **Final Recommendation:** The protocol should consider implementing a multi-signature wallet for the owner and issuer roles to mitigate the risk of a single compromised key. Additionally, introducing a timelock for minting operations would provide transparency and protection for token holders against sudden supply inflation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-like patterns for ERC-20 compliance and ownership management. 7.1 Architecture is clean, and 7.2 Code Security is robust, utilizing Solidity 0.8.x to… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the centralized issuer role. The owner has the authority to mint new tokens, which directly impacts the total supply and token value. While this… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, ensuring that the current rules cannot be altered post-deployment. 7.8 Operations are limited to standard… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 47.3% |
| **Top-3 Unlocked** | ⚠️ 86.2% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'mint' function allows the designated issuer address to create new tokens at will. This increases the total supply and dilutes the value of existing holdings, posing a risk if the issuer's private key is compromised.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or implement a hard-coded supply cap with a timelock delay for any minting events.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 49% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 57.2% of supply. What remains: 45.8% in wallets, 11.4% in other contracts. 1,667 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GULD (GULD). 1,667 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $3.0M (DexScreener, all pools). 24h trading volume $11K (CoinGecko, all markets, daily snapshot). 24h trading volume $175K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $3.0M of DEX liquidity across 4 pools. Launch: 140 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x14d6...47a1`](https://basescan.org/address/0x14d6c649292c5c9790c5196d1a9ea039307947a1) |
| **Network** | Base |
| **Price** | $0.02102 |
| **24h Volume** | $85.6K |
| **Liquidity** | $1.47M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 57.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 65 buys / 189 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x95475b9b1492cf109969ff25c2862ef38d1a9998c6288f8b9b7d1c99c6443c2e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/guld-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
