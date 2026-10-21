---
token: Nookleus
ticker: NOOK
network: ethereum
risk_score: 69
status: high
date: 2026-10-21
---

# Nookleus (NOOK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nookleus-eth)

---

## Audit Summary

The Nook contract implements a custom token with integrated fee-sharing and distribution mechanisms. While the core ERC-20 transfer logic is functional, the protocol relies on centralized privileged roles (nucleus, sprout) to manage economic parameters. Coverage: 7.1 Architecture (Centralized), 7.2 Code Security (Standard), 7.3 Access Control (Privileged), 7.4 Economic (Fee-based), 7.5 Governance (None), 7.6 External (None), 7.7 Upgrades (None), 7.8 Operations (Manual).

> **Final Recommendation:** Implement a multi-signature wallet or a timelock controller for the nucleus and sprout roles to mitigate the risk of centralized control. Additionally, consider adding the missing totalSupply and allowance view functions to ensure full compatibility with standard decentralized finance interfaces.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard Solidity 0.8.x features to prevent overflow/underflow. The transfer logic correctly handles allowance updates and balance adjustments. However, the reliance on external… |
| **Governance / Economics** | 1/10 | High | Economic parameters are governed by the nucleus and sprout roles, which control fee distribution and initialization. This centralization allows for potential manipulation of user rewards if the… |
| **Upgrades** | 5/10 | Medium | The contract is not upgradeable and lacks proxy patterns. This ensures immutability of the current logic, preventing unauthorized code changes. Users can rely on the current logic remaining constant… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-07` — Centralized Control Over Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The privileged addresses 'nucleus' and 'sprout' have the authority to modify the fee structure and distribution logic via the start and feed functions. This allows these controllers to alter the economic outcome of token transfers at their discretion.

**Recommendation:** Restrict the ability to change fee parameters by implementing a governance-based voting mechanism or a timelock to provide transparency and prevent immediate, unilateral changes.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x852c…6c72 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 78% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 98.4% of supply. What remains: 2.0% in wallets, 96.4% in other contracts. 48 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

48 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23K (DexScreener, all pools). 24h trading volume $135K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 6 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8b04...f73d`](https://etherscan.io/address/0x8b046926a7f875309117f749411e83c7e37ff73d) |
| **Network** | Ethereum |
| **Price** | $0.00001801 |
| **24h Volume** | $134.3K |
| **Liquidity** | $18.0K |
| **Volume / Liquidity** | 7.5× |
| **Token Age** | 6h |
| **Top-10 Holders** | 98.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 310 buys / 254 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x39953660e1b8ffc629ea21afeb134eab9cae6bb8ce9ebecc725353addc3c9010)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nookleus-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
