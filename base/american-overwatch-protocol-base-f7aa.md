---
token: American Overwatch Protocol
ticker: AOP
network: base
risk_score: 58
status: medium
date: 2026-10-23
---

# American Overwatch Protocol (AOP) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-base-f7aa)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol utilizes a centralized ownership model where the owner holds significant power over token supply and transferability. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents a centralization risk to token holders.

> **Final Recommendation:** To mitigate centralization risks, it is recommended to transition administrative functions to a multi-signature wallet or a decentralized governance contract. Implementing a timelock on sensitive functions like updateMintRate and lockPool would provide users with advance notice of changes and prevent instantaneous, potentially harmful, administrative actions.

Ensure that the owner's private keys are managed with high-security standards, such as hardware security modules or institutional-grade custody solutions. Regularly monitor the contract's state to ensure that minting and pool locking activities remain within the expected parameters defined by the project's whitepaper.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture leverages well-tested OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the owner. The owner can influence token supply through minting functions and control liquidity access via pool locking… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, providing certainty to users regarding the contract's behavior. No upgradeability patterns are implemented… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call updateMintRate and release, which can increase the total supply of the token. This allows the owner to dilute existing token holders at their discretion.

**Recommendation:** Consider implementing a hard cap on the total supply or moving the minting authority to a decentralized governance mechanism or a timelocked contract.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable transfers for specific pools. This grants the owner the power to freeze user assets or restrict liquidity at will.

**Recommendation:** Restrict the ability to lock/unlock pools to a decentralized voting process or remove the functionality entirely if it is not strictly required for the protocol's operation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 5,100 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,100 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $106K (DexScreener, all pools). 24h trading volume $410K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $106K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1087...346e`](https://basescan.org/address/0x1087d8ce68d36b056157311b82c9273d1083346e) |
| **Network** | Base |
| **Price** | $0.2455 |
| **24h Volume** | $409.7K |
| **Liquidity** | $106.3K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 10h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1325 buys / 1281 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x6075254f764730168f67b590cbf0e5d4a74cbde54425f6b009b3b160956017bb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-base-f7aa)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
