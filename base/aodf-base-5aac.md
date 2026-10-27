---
token: AODF
ticker: AODF
network: base
risk_score: 57
status: medium
date: 2026-10-27
---

# AODF (AODF) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aodf-base-5aac)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting features. The protocol relies on a centralized owner to manage inflation, pool locking, and vesting releases. While the code follows standard OpenZeppelin patterns, the high level of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security and trust, consider transitioning ownership to a multi-signature wallet or a decentralized governance contract. This would mitigate the risks associated with a single point of failure regarding token minting and pool locking.

Additionally, implement a timelock mechanism for all sensitive administrative functions. This provides transparency to the community and allows users time to react to significant changes in token supply or transfer rules.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes robust, battle-tested OpenZeppelin libraries for ERC-20, voting, and ownership management. 7.1 Architecture and 7.2 Code Security are well-implemented, ensuring standard… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily reliant on the owner's discretion. The ability to mint tokens via updateMintRate and control liquidity via lockPool allows the owner to… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. This ensures immutability of the logic, which is a strength for security. The lack of upgradeability means the current administrative… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which can dilute the value of existing holdings.

**Recommendation:** Consider implementing a hard cap on the total supply or moving the minting authority to a decentralized governance contract with a timelock.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch via the lockPool and unlockPool functions. This allows the owner to effectively freeze or unfreeze transfers for the pool, potentially preventing users from moving or selling their tokens.

**Recommendation:** Remove the ability to arbitrarily lock transfers, or ensure that such functionality is governed by a transparent, community-voted process.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 17 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

17 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $692K (DexScreener, all pools). 24h trading volume $874K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $692K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7cdc...4f1d`](https://basescan.org/address/0x7cdcba1f30d17be9652487748aaf7b0d41ee4f1d) |
| **Network** | Base |
| **Price** | $6.2100 |
| **24h Volume** | $874.3K |
| **Liquidity** | $691.6K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 12h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1254 buys / 1236 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x2da0781b9427583ff505b51eeb5f6fba22c04b4c8ec8a4904d010c19def84889)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aodf-base-5aac)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
