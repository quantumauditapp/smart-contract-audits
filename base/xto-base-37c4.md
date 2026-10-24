---
token: XTO
ticker: XTO
network: base
risk_score: 55
status: medium
date: 2026-10-24
---

# XTO (XTO) — Smart Contract Security Analysis | Base

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-base-37c4)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting features. The architecture relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high level of administrative control over token supply and transferability presents a significant centralization risk to token holders.

> **Final Recommendation:** To improve security and trust, consider transitioning the ownership of the contract to a multi-signature wallet or a decentralized governance contract. This would mitigate the risk of a single compromised key performing unauthorized minting or locking user transfers.

Additionally, implement a timelock mechanism for all privileged functions such as updateMintRate and lockPool. A delay of 24-48 hours would provide the community with sufficient notice and the ability to react to significant changes in the token's economic parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-tested OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard, audited… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the contract owner. The owner has the ability to mint new tokens up to a 2% annual cap and toggle transferability via the pool… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, which provides security against malicious logic updates but prevents fixing bugs without a migration. The… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of tokens. This allows the owner to dilute the holdings of all existing token holders at their discretion, up to a defined annual limit.

**Recommendation:** Implement a timelock for minting operations or transition ownership to a DAO to ensure that supply changes are transparent and community-approved.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable the ability for tokens to be transferred. This gives the owner the power to effectively freeze user assets or halt trading at any time.

**Recommendation:** Remove the ability for the owner to arbitrarily lock transfers, or restrict this functionality to a decentralized governance process to prevent abuse.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,514 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,514 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $447K (DexScreener, all pools). 24h trading volume $629K (DexScreener, all pools).

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
| **Contract** | [`0x6282...7a5d`](https://basescan.org/address/0x6282b476ca574ef8f24de1223d5b08cd91167a5d) |
| **Network** | Base |
| **Price** | $0.9166 |
| **24h Volume** | $628.9K |
| **Liquidity** | $446.5K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 16h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1741 buys / 1555 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x8c31170be4d2b8c14a81305021694119eb6ae3221721e3ee0ce9aed73227a303)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-base-37c4)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
