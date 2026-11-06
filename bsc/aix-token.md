---
token: AIX Token
ticker: AIX
network: bsc
risk_score: 66
status: high
date: 2026-11-06
---

# AIX Token (AIX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aix-token-bsc)

---

## Audit Summary

The AIXTokenV8 contract is a highly centralized ERC-20 token with extensive administrative controls over transfer logic, fees, and supply. The contract implements a 'decay' mechanism that allows for token minting and supply manipulation. While the code follows standard ERC-20 patterns, the degree of owner control presents significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the owner possesses total control over the token's utility and economic parameters. We recommend transitioning to a multi-signature wallet or a decentralized governance contract to manage these privileged functions, reducing the risk associated with a single point of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture relies on a centralized owner model where 7.1 Architecture and 7.2 Code Security are heavily dependent on the integrity of the owner's EOA. 7.3 Access Control is strictly enforced… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance are entirely centralized under the owner's control. The owner can arbitrarily modify tax rates, blacklist users, and trigger supply inflation via the decay mechanism.… |
| **Upgrades** | 3/10 | High | The contract is not a proxy and does not support 7.7 Upgrades. 7.8 Operations are limited to the functions provided in the current bytecode. Once deployed, the logic remains fixed, though the state… |

## Security Findings

_🟡 4 Medium · ⚪ 5 Informational_

### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The triggerDecay function allows a designated decay keeper to mint new tokens, which increases the total supply and dilutes the value of existing holdings.

**Recommendation:** Implement a hard cap on the total supply or require a time-locked governance vote before any supply expansion occurs.


### `CP-05` — Transfer Restriction Switches  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the canBuy and canSell switches, effectively halting all trading activity for the token at their discretion.

**Recommendation:** Remove the ability to pause trading or implement a decentralized circuit breaker that requires community approval.


### `CP-06` — Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The owner can add any address to a blacklist, preventing those holders from transferring or selling their tokens.

**Recommendation:** Limit the blacklist functionality to only address malicious actors identified through a transparent, community-voted process.


### `CP-07` — Arbitrary Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to change buy and sell tax rates, which directly impacts the amount of tokens received by users during transactions.

**Recommendation:** Set a maximum tax threshold in the contract code that the owner cannot exceed, providing predictability for users.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 0.9% burned — not holders that can sell, so excluded from the concentration score. What remains: 2.4% in wallets, 96.7% in other contracts. 70,008 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

70,008 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11.1M (DexScreener, all pools). 24h trading volume $269K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11.1M of DEX liquidity across 1 pools. Launch: 6 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0747...d69a`](https://bscscan.com/address/0x0747d3d37ab929e795a09aeff5939d9e5647d69a) |
| **Network** | BNB Chain |
| **Price** | $0.6317 |
| **24h Volume** | $268.9K |
| **Liquidity** | $11.14M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 6d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1758 buys / 3909 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x860b958b9119a8979f08c99fa65619d014721101)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aix-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
