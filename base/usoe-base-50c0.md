---
token: USOE
ticker: USOE
network: base
risk_score: 58
status: medium
date: 2026-10-21
---

# USOE (USOE) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usoe-base-50c0)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage minting rates and pool transfer restrictions. While the code follows established OpenZeppelin standards, the high level of administrative control over supply and transferability introduces significant centralization risks.

> **Final Recommendation:** To improve security, consider transitioning ownership to a multi-signature wallet or a decentralized governance contract (DAO) to prevent single-point-of-failure risks. Implementing a timelock on privileged functions like updateMintRate would provide transparency and allow the community to react to significant economic changes.

Ensure that all administrative actions are documented and communicated to token holders. Regularly audit the vesting schedules and minting logic to ensure they remain aligned with the protocol's stated economic objectives.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture leverages standard OpenZeppelin libraries for ERC-20, Votes, and EIP-712, ensuring robust base functionality. 7.1 Architecture and 7.2 Code Security are well-implemented, utilizing… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are dominated by the owner's ability to adjust inflation rates and lock pools. While 7.6 External dependencies are minimal, the economic model is subject to… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, which mitigates 7.7 Upgrades risks. 7.8 Operations are straightforward, though the reliance on the owner for critical updates remains a point of failure. No proxy… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to mint new tokens, which increases the total supply and dilutes existing holders. This power is unrestricted by any community vote or timelock.

**Recommendation:** Implement a timelock for all supply-altering functions and consider moving ownership to a DAO or multi-sig to ensure community oversight.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to toggle the ability for users to transfer tokens. This allows the owner to effectively freeze assets or restrict liquidity at will.

**Recommendation:** Remove the ability to arbitrarily lock transfers or restrict this functionality to specific, time-bound scenarios with clear, public criteria.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 24,006 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

24,006 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $4.5M (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

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
| **Contract** | [`0x5bf9...be07`](https://basescan.org/address/0x5bf91d9f4d97bc09cd4af31292395a58d8b6be07) |
| **Network** | Base |
| **Price** | $0.9417 |
| **24h Volume** | $1.46M |
| **Liquidity** | $4.48M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 6h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2196 buys / 1805 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x4f758d27b606419ebc09de87d87071250bf407e15968ac53d1089346ca6d9abd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usoe-base-50c0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
