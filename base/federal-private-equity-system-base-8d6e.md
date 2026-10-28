---
token: Federal Private Equity System
ticker: FPES
network: base
risk_score: 57
status: medium
date: 2026-10-28
---

# Federal Private Equity System (FPES) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/federal-private-equity-system-base-8d6e)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with integrated governance and vesting capabilities. The protocol relies heavily on a centralized owner account to manage token supply inflation and transfer restrictions. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents a significant centralization risk for token holders.

> **Final Recommendation:** To mitigate centralization risks, consider transitioning ownership to a decentralized governance model, such as a multi-signature wallet or a DAO contract. This would require community consensus for sensitive actions like minting or locking pools, rather than relying on a single owner address.

Additionally, implement timelocks for all privileged functions. A delay between the announcement and execution of administrative actions would provide transparency and allow token holders to react to significant changes in tokenomics or transfer rules.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the contract owner. The owner has the authority to mint tokens and toggle transfer restrictions, which directly impacts token… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as this is an immutable contract. The logic is fixed upon deployment, which eliminates risks associated with proxy-based upgrade vulnerabilities. No further upgrade… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which can lead to the dilution of existing token holders' value.

**Recommendation:** Implement a hard-coded minting schedule or move the minting authority to a decentralized governance contract that requires a community vote for any supply increases.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers. This grants the owner the power to freeze user assets or restrict liquidity at any time.

**Recommendation:** Remove the ability for the owner to arbitrarily lock transfers, or implement a transparent, time-bound mechanism that prevents the owner from locking assets indefinitely without community oversight.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 1,506 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,506 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $72K (DexScreener, all pools). 24h trading volume $35K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $72K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2549...9004`](https://basescan.org/address/0x2549039017dc0820af7e8faeb352d8e8b7b89004) |
| **Network** | Base |
| **Price** | $0.03408 |
| **24h Volume** | $34.9K |
| **Liquidity** | $72.1K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 5h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1749 buys / 175 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xba01554adb7536d936ae7a72855de99d8ecb1b7578b4889631a8fd6e1e55a8b1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/federal-private-equity-system-base-8d6e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
