---
token: American Overwatch Protocol
ticker: AOP
network: base
risk_score: 59
status: medium
date: 2026-11-02
---

# American Overwatch Protocol (AOP) — Smart Contract Security Analysis | Base

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-base-1151)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage inflation, token vesting releases, and transfer restrictions. While the code follows standard OpenZeppelin patterns, the high level of administrative control over supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security, transition the ownership of the contract to a multi-signature wallet or a decentralized governance DAO. Implementing a timelock on privileged functions like updateMintRate and lockPool would provide transparency and allow the community to react to administrative changes before they take effect.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes robust, battle-tested OpenZeppelin libraries for ERC-20 and governance functionality (7.1 Architecture). Code security is high, with clear separation of concerns and… |
| **Governance / Economics** | 3/10 | High | Economic parameters are heavily centralized under the owner role (7.4 Economic). The owner has the authority to mint tokens and modify transfer rules, which directly impacts token holder value (7.5… |
| **Upgrades** | 4/10 | Medium | The contract is not currently using a proxy pattern (7.7 Upgrades). Logic is immutable once deployed, which eliminates risks associated with malicious implementation updates. Future changes would… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of tokens. This allows the administrator to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Consider implementing a hard-coded inflation schedule or moving the minting authority to a decentralized governance contract with a mandatory timelock.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable token transfers. This gives the administrator the power to freeze user assets or prevent trading activity entirely.

**Recommendation:** Remove the ability to pause transfers or restrict this functionality to a decentralized emergency pause mechanism that requires community consensus.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.5% of supply. What remains: 0.5% in wallets, 95.0% in other contracts. 159 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

159 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $30.0M (DexScreener, all pools). 24h trading volume $502K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30.0M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1b9c...e47e`](https://basescan.org/address/0x1b9c921fb0bf1bbea5a3d4d16cce5a16fd57e47e) |
| **Network** | Base |
| **Price** | $0.02 |
| **24h Volume** | $501.8K |
| **Liquidity** | $30.01M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 6h |
| **Top-10 Holders** | 95.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 723 buys / 472 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xb0dac864f6c77dc7e504f2856ce696d6f1f9a4d3e55fb39ce8e222de6ca78f47)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-base-1151)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
