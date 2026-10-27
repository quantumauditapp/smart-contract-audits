---
token: AOP
ticker: AOP
network: base
risk_score: 55
status: medium
date: 2026-10-27
---

# AOP (AOP) — Smart Contract Security Analysis | Base

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aop-base-090d)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage inflation, pool locking, and vesting releases. While the code follows standard OpenZeppelin patterns, the high level of administrative privilege introduces significant centralization risks for token holders.

> **Final Recommendation:** To improve security and trust, consider transitioning the owner role to a multi-signature wallet or a decentralized governance contract. This would mitigate the risk of a single point of failure and provide transparency for administrative actions like minting or pool locking.

Additionally, implement a timelock mechanism for all privileged functions. A delay between the announcement and execution of administrative changes would allow token holders to react to significant economic adjustments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages well-audited OpenZeppelin libraries for ERC-20, voting, and permit functionality (7.1 Architecture). Code security is high, utilizing modern Solidity 0.8.x features to prevent… |
| **Governance / Economics** | 3/10 | High | The protocol exhibits high centralization, as the owner holds absolute authority over token supply and transferability (7.3 Access Control). Economic parameters like mint rates are adjustable by the… |
| **Upgrades** | 4/10 | Medium | The contract is not a proxy and does not support upgrades (7.7 Upgrades). This ensures immutability of the current logic, preventing unauthorized logic changes. Future changes would require a full… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at will, which can dilute the value of existing holdings.

**Recommendation:** Transition the minting authority to a decentralized governance model or a time-locked multi-signature wallet to prevent unilateral supply increases.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch via the lockPool and unlockPool functions. This allows the owner to freeze or unfreeze token transfers, effectively controlling the liquidity of the token.

**Recommendation:** Remove the ability for the owner to arbitrarily pause transfers, or implement a transparent, community-governed process for managing pool locking.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 36 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

36 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $4.5M (DexScreener, all pools). 24h trading volume $4.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $4.5M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc133...6248`](https://basescan.org/address/0xc13318e0829f01533ac02b9a9eb309c2c00f6248) |
| **Network** | Base |
| **Price** | $0.9251 |
| **24h Volume** | $4.36M |
| **Liquidity** | $4.51M |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 12h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1246 buys / 1210 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x1a47a03fb040b7a74b0f92edad13e80f50c14d4129719cf9ce0a0946a97fa1f6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aop-base-090d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
