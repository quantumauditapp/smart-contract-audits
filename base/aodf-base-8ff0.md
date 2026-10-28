---
token: AODF
ticker: AODF
network: base
risk_score: 56
status: medium
date: 2026-10-28
---

# AODF (AODF) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aodf-base-8ff0)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting features. The protocol relies on a centralized owner to manage inflation rates and liquidity pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents a significant centralization risk to token holders.

> **Final Recommendation:** To improve security and decentralization, consider transitioning ownership to a multi-signature wallet or a decentralized governance contract (DAO). This would mitigate the risk of a single point of failure and provide transparency for administrative actions like minting or pool locking.

Additionally, implement a timelock mechanism for all sensitive administrative functions. This would provide the community with a window to react to significant changes in token supply or transfer rules, enhancing trust in the protocol's economic stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes standard OpenZeppelin libraries for ERC-20, Votes, and Permit functionality, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are elevated due to the owner's ability to mint tokens and toggle transfer restrictions. While inflation is capped at 2% per year, the owner retains unilateral… |
| **Upgrades** | 4/10 | Medium | The contract is not a proxy, meaning 7.7 Upgrades are not applicable. Logic is immutable upon deployment. Any changes to protocol behavior must be handled through the existing owner-restricted… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which directly dilutes the value of existing holdings.

**Recommendation:** Transition ownership to a decentralized governance model or implement a strict, immutable minting schedule that does not require manual owner intervention.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers. This gives the owner the power to effectively freeze user assets or halt trading activity at any time.

**Recommendation:** Remove the ability for the owner to pause or restrict transfers, or move this functionality to a community-governed emergency pause mechanism with a timelock.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 1,515 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,515 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.9M (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.9M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb442...c075`](https://basescan.org/address/0xb442849dc43edce4981652995ae5cf015b30c075) |
| **Network** | Base |
| **Price** | $0.3395 |
| **24h Volume** | $1.06M |
| **Liquidity** | $1.93M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 4h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1730 buys / 154 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xdb753cd4311c9790c0458eac8112ca3cc0093dd4d63c4715a5db70d17ad4dc7f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aodf-base-8ff0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
