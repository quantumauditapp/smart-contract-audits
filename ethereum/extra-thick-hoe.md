---
token: Extra Thick Hoe
ticker: ETH
network: ethereum
risk_score: 23
status: low
date: 2026-10-25
---

# Extra Thick Hoe (ETH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/extra-thick-hoe-eth)

---

## Audit Summary

The ExtraThickHoe contract is a standard ERC-20 token implementation with administrative functions that have been permanently disabled via ownership renouncement. The contract logic is straightforward, though it contains a specific authorization pattern vulnerability regarding the use of tx.origin. As ownership is renounced, the privileged functions are effectively dormant and pose no further risk to the protocol.

> **Final Recommendation:** The protocol is currently in a safe, immutable state due to the renouncement of ownership. No further action is required for the current deployment as the administrative functions are permanently inaccessible.

For future deployments, avoid the use of tx.origin for authorization or logic checks, as it is susceptible to phishing attacks where a user is tricked into interacting with a malicious contract that then calls the target contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The codebase utilizes standard OpenZeppelin-style patterns for ERC-20 compliance, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control was previously managed via… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance controls are currently non-existent due to the renouncement of ownership. The token supply is fixed and no further minting or administrative adjustments can occur.… |
| **Upgrades** | 10/10 | Low | The contract is not upgradeable, satisfying 7.7 Upgrades requirements by being immutable. 7.8 Operations are restricted to standard token transfers. No proxy patterns are utilized, ensuring the logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CD-01` — Use of tx.origin for authorization  *(Severity: Medium · Status: Unresolved)*

The contract uses tx.origin to determine logic within the balanceOf function. This is dangerous because an intermediary contract can be used to trick the protocol into performing actions on behalf of the original sender, bypassing intended security checks.

**Recommendation:** Replace all instances of tx.origin with msg.sender to ensure that the immediate caller is the one being authenticated, which is the standard and secure practice in Solidity.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 52.4% of supply. Of that, 39.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.9% in wallets, 0.0% in other contracts. 206 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

206 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $46K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3e6d...0c07`](https://etherscan.io/address/0x3e6dd720f83aa5316b3c7a81a4112bd72cd20c07) |
| **Network** | Ethereum |
| **Price** | $0.00001318 |
| **24h Volume** | $46.4K |
| **Liquidity** | $11.1K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 11h |
| **Top-10 Holders** | 52.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 303 buys / 480 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x74affd45940abd873749e139cf2b3f0135d7ddcb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/extra-thick-hoe-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
