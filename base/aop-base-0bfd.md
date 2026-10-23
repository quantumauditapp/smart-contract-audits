---
token: AOP
ticker: AOP
network: base
risk_score: 58
status: medium
date: 2026-10-23
---

# AOP (AOP) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aop-base-0bfd)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting features. The protocol relies on a centralized owner to manage token inflation and pool access. While the code follows standard OpenZeppelin patterns, the high level of administrative control over supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** The protocol should consider transitioning the owner role to a decentralized DAO or a time-locked contract to mitigate the risks associated with centralized control. Implementing a timelock on sensitive functions like updateMintRate would provide transparency and allow the community to react to administrative changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes standard OpenZeppelin libraries for ERC-20, Votes, and Permit functionality, ensuring robust base security. 7.1 Architecture and 7.2 Code Security are well-implemented… |
| **Governance / Economics** | 3/10 | High | The economic model is governed by the owner, who controls inflation via updateMintRate and vesting releases. 7.4 Economic and 7.5 Governance items are heavily reliant on the owner's address, which is… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, which eliminates 7.7 Upgrades risks related to proxy logic. 7.8 Operations are straightforward, with no complex migration paths required. The immutability of the… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to mint new tokens, which increases the total supply and dilutes the value of existing holdings.

**Recommendation:** Implement a timelock on minting functions or transition ownership to a decentralized governance contract.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to toggle a switch that determines whether transfers are permitted, effectively freezing or unfreezing token movement at will.

**Recommendation:** Remove the ability to arbitrarily pause transfers or restrict this functionality to emergency-only scenarios managed by a decentralized multisig.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 6,011 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,011 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $74K (DexScreener, all pools). 24h trading volume $96K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $74K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbde0...9d78`](https://basescan.org/address/0xbde00f63e46130dd32f918a70ad63fde0a1b9d78) |
| **Network** | Base |
| **Price** | $0.3939 |
| **24h Volume** | $95.6K |
| **Liquidity** | $74.1K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 4h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2301 buys / 2017 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x8cc63240ceb21013cedc5c775bb53f222513531d918b55dc79b27113cc0b599f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aop-base-0bfd)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
