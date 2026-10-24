---
token: United States Oil Exchange 🔥
ticker: USOE
network: base
risk_score: 74
status: high
date: 2026-10-24
---

# United States Oil Exchange 🔥 (USOE) — Smart Contract Security Analysis | Base

> **Risk Score: 74/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-oil-exchange-base)

---

## Audit Summary

The audit evaluated the DERC20 token contract deployed on Base. The codebase implements a standard OpenZeppelin-derived ERC-20 structure with voting extensions (ERC20Votes), linear vesting logic, and an inflation mechanism capped at 2% annually. However, centralization vectors exist around transfer gating and mint rate manipulation controlled by a privileged owner address.

> **Final Recommendation:** Implement a formal timelock and decentralized governance module to intermediate all administrative calls currently restricted to `onlyOwner`, particularly `lockPool`, `unlockPool`, and `updateMintRate`. Additionally, adopt a two-step ownership transfer pattern (such as OpenZeppelin's `Ownable2Step`) to prevent accidental transfer of administrative privileges.

Consider bounding pool locking mechanics so that user funds cannot be permanently restricted in secondary liquidity pools, and ensure transparent emission schedules are published on-chain to provide predictable supply dynamics for token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | Under 7.1 Architecture and 7.2 Code Security, the contract relies heavily on robust OpenZeppelin primitives, including ERC20Votes, ERC20Permit, and standard Math libraries. Standard safe math… |
| **Governance / Economics** | 3/10 | High | In terms of 7.4 Economic considerations, the token enforces a hardcoded upper limit on yearly inflation at 2% (`MAX_YEARLY_MINT_RATE_WAD`), preventing hyperinflationary abuse. Additionally, 7.5… |
| **Upgrades** | 4/10 | Medium | Regarding 7.7 Upgrades, the deployed DERC20 contract is non-upgradeable and deployed without proxy indirection, preventing unauthorized implementation swaps. The contract relies on static storage… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Privileged Supply Minting and Inflation Control  *(Severity: Medium · Status: Unresolved)*

The contract allows the privileged owner to mint new tokens and adjust the annual inflation rate by calling the `updateMintRate(uint256)` function. When invoked, it executes `mintInflation()`, creating new tokens that dilute existing holders up to the hardcoded maximum rate of 2% annually. Additionally, the `release()` function transfers vested tokens from contract custody to recipients based on vesting schedules.

**Recommendation:** Subject the `updateMintRate` function to a transparent timelock contract or direct decentralized DAO governance voting, and consider enforcing strict time-delayed caps before inflation adjustments take effect.


### `CP-05` — Privileged Pool Transfer Switch Control  *(Severity: Medium · Status: Unresolved)*

The contract contains an administrative transfer-gating mechanism where the owner can call `lockPool(address)` and `unlockPool()` to toggle the `isPoolUnlocked` boolean switch and assign the target `pool` address. When locked, token transfers or interactions routed through the specified liquidity pool can be restricted or refused, placing secondary market trading under centralized control.

**Recommendation:** Remove the ability to arbitrarily lock liquidity pools once trading has commenced, or strictly enforce automated time-based unlocks and multisig/timelock safeguards to avoid centralized trade restrictions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 10,027 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

10,027 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $130K (DexScreener, all pools). 24h trading volume $426K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $130K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc660...260f`](https://basescan.org/address/0xc66037403f99ce93ebff19ed8b8a36bb48ef260f) |
| **Network** | Base |
| **Price** | $0.9218 |
| **24h Volume** | $426.1K |
| **Liquidity** | $129.9K |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 7h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4314 buys / 3820 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x3d55323f2137e35e91282dae35ae6bf9ee3cf94e0a3b6c1b58d15b53edba1c37)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-oil-exchange-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
