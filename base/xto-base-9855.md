---
token: XTO
ticker: XTO
network: base
risk_score: 57
status: medium
date: 2026-10-24
---

# XTO (XTO) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-base-9855)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates, token vesting, and pool transfer restrictions. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security and decentralization, consider transitioning ownership to a multi-signature wallet or a decentralized governance contract (DAO). This would mitigate the risk of a single point of failure regarding minting and transfer control.

Additionally, implement a timelock for all privileged functions such as updateMintRate and lockPool. A delay period would provide the community with visibility and the ability to react to significant changes in token supply or transfer rules.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-tested OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard, audited… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance rely entirely on the owner's discretion. The owner can mint tokens up to a 2% annual cap and toggle transferability, which directly impacts 7.8 Operations. These… |
| **Upgrades** | 4/10 | Medium | The contract is not a proxy, meaning 7.7 Upgrades are not applicable. The logic is immutable, providing transparency to users regarding the current rules. Future changes would require a migration to… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply, which dilutes the value of existing holdings.

**Recommendation:** Implement a timelock on minting functions or transition to a decentralized governance model to ensure minting events are transparent and community-approved.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch using the lockPool and unlockPool functions. This allows the owner to arbitrarily halt or enable token transfers, effectively freezing user assets.

**Recommendation:** Remove the ability to pause transfers or restrict this functionality to a decentralized emergency pause mechanism that requires multi-party consensus.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 8,028 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

8,028 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $447K (DexScreener, all pools). 24h trading volume $984K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $447K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9d77...3988`](https://basescan.org/address/0x9d77087f3f51de3a14cf6d79e6613affe7343988) |
| **Network** | Base |
| **Price** | $0.9171 |
| **24h Volume** | $984.3K |
| **Liquidity** | $446.9K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 9h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1086 buys / 1054 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xd4351c4f34fce6ffe10fcc4f006704a1f5a78ff656ed08004752bf2631ce8bf0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-base-9855)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
