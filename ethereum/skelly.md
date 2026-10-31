---
token: SKELLY
ticker: SKELLY
network: ethereum
risk_score: 34
status: low
date: 2026-10-31
---

# SKELLY (SKELLY) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 34/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/skelly-eth)

---

## Audit Summary

The SKELLY token is a standard ERC-20 implementation. The audit identified critical issues regarding return value consistency and insecure authorization patterns. While the core token logic follows standard patterns, the implementation of custom transfer rules and authorization logic introduces significant risks to token holders.

> **Final Recommendation:** The development team should immediately refactor the transfer functions to ensure consistent boolean return values to maintain compatibility with standard DeFi protocols. Furthermore, replace all instances of tx.origin with msg.sender to prevent potential authorization bypasses via malicious intermediary contracts.

Users should exercise caution when interacting with this token in complex smart contract environments until these issues are addressed. A formal verification of the transfer path is recommended after the suggested refactoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes standard OpenZeppelin-like ERC-20 structures for core functionality. Code quality is generally high, adhering to modern Solidity standards. However, the logic in the transfer… |
| **Governance / Economics** | 9/10 | Low | The token lacks centralized administrative controls, which limits 7.5 Governance risks. Economic parameters are static, reducing 7.4 Economic risk. However, the reliance on tx.origin for rules could… |
| **Upgrades** | 10/10 | Low | The contract is not upgradeable, eliminating 7.7 Upgrades risk. The architecture is immutable, ensuring that the current logic remains fixed for the lifetime of the contract. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `CD-01` — Inconsistent Return Values in Transfer Functions  *(Severity: High · Status: Unresolved)*

The _transfer, transfer, and transferFrom functions do not correctly handle return values, which can cause integrations with other DeFi protocols to fail or misinterpret the success of a transaction.

**Recommendation:** Ensure all transfer functions explicitly return a boolean value as required by the ERC-20 standard to maintain compatibility with external contracts.


### `CD-02` — Insecure Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The returnTx function uses tx.origin to determine authorization or rules. This is dangerous because a malicious contract can trick an authorized user into calling it, effectively bypassing intended security checks.

**Recommendation:** Replace tx.origin with msg.sender to ensure that only the immediate caller is authorized to perform sensitive actions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 21.8% of supply. What remains: 12.7% in wallets, 9.1% in other contracts. 371 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

371 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $51K (DexScreener, all pools). 24h trading volume $345K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $51K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfedc...905f`](https://etherscan.io/address/0xfedcb1513b389b1c4d243f85c56557e86de0905f) |
| **Network** | Ethereum |
| **Price** | $0.0003117 |
| **24h Volume** | $345.5K |
| **Liquidity** | $50.8K |
| **Volume / Liquidity** | 6.8× |
| **Token Age** | 7h |
| **Top-10 Holders** | 21.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 756 buys / 383 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x7e3c5a5a6a3bdd2a6ae66eef31e1ddd85ee4c30ff16c7b19f55ca76497ab1204)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/skelly-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
