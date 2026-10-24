---
token: United Energy Reserve
ticker: UER
network: base
risk_score: 60
status: medium
date: 2026-10-24
---

# United Energy Reserve (UER) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-energy-reserve-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting capabilities. The architecture relies on a centralized owner to manage inflation, pool locking, and token metadata. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** It is recommended to transition ownership to a decentralized governance contract or a multi-signature wallet to mitigate the risks associated with a single point of failure. Implementing a timelock on sensitive functions like updateMintRate would provide community members with visibility and time to react to significant economic changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for core ERC-20 and governance functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the authority to mint tokens and halt transfers, which directly impacts the token's economic stability. While inflation… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. This ensures immutability of the logic, which is a positive security feature. No upgradeability risks are present. |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via updateMintRate and release functions. This allows the owner to increase the total supply at will, which can dilute the value of existing holdings.

**Recommendation:** Consider renouncing ownership or moving the minting authority to a decentralized governance mechanism with a mandatory timelock.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable transfers for specific pools. This gives the owner the power to freeze user assets or restrict liquidity at their discretion.

**Recommendation:** Remove the ability to arbitrarily lock transfers or implement a transparent, community-voted process for any such restrictions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.1% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,312 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,312 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $47K (DexScreener, all pools). 24h trading volume $87K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $47K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1de8...20bd`](https://basescan.org/address/0x1de8a433d418a27f3ecee1219a37d512a66520bd) |
| **Network** | Base |
| **Price** | $0.004591 |
| **24h Volume** | $86.8K |
| **Liquidity** | $46.8K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1413 buys / 1400 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x7b57430cbe767d47d1547d23dd2940b16ff5e8bced32f399c1b75efb3e2b5b6b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-energy-reserve-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
