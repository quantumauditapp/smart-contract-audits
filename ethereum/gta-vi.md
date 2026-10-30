---
token: GTA VI
ticker: GTA6
network: ethereum
risk_score: 46
status: medium
date: 2026-10-30
---

# GTA VI (GTA6) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gta-vi-eth)

---

## Audit Summary

The GTA token is a standard ERC-20 implementation. The architecture is straightforward, utilizing OpenZeppelin's standard library for core token functionality. A critical logic flaw exists in the transfer mechanism that may cause integration issues with external protocols, though the contract lacks centralized privileged controls.

> **Final Recommendation:** The project should address the return value discrepancy in the transfer functions to ensure full compatibility with the ERC-20 standard. This will prevent potential failures when the token is used within automated smart contract vaults or decentralized exchanges.

Given the lack of administrative controls, the token is immutable and transparent. Users should verify the contract address against official sources before interacting, as no further updates or emergency pauses are possible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract follows standard ERC-20 patterns with 7.1 Architecture and 7.2 Code Security adhering to established OpenZeppelin practices. 7.3 Access Control is absent, meaning no privileged roles… |
| **Governance / Economics** | 8/10 | Low | The token lacks 7.5 Governance mechanisms, operating as a permissionless asset. 7.4 Economic parameters are fixed by the initial supply and standard ERC-20 logic. There are no inflationary or… |
| **Upgrades** | 8/10 | Low | The contract is not upgradeable, satisfying 7.7 Upgrades requirements by being immutable. 7.8 Operations are limited to standard token transfers. No proxy patterns are utilized, eliminating risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `CD-01` — Incorrect Return Value in Transfer Functions  *(Severity: High · Status: Unresolved)*

The transfer and transferFrom functions contain logic inconsistencies regarding the return values defined in the MAxTradingIdentifierLimits and _transfer internal calls. This deviation from the ERC-20 standard can cause external smart contracts that rely on the boolean return value to revert or fail unexpectedly.

**Recommendation:** Ensure that the transfer and transferFrom functions strictly follow the ERC-20 specification by returning a boolean 'true' upon successful execution and reverting on failure, without relying on non-standard internal return paths.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 35.9% of supply. What remains: 12.8% in wallets, 23.1% in other contracts. 201 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

201 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $78K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x19d5...3150`](https://etherscan.io/address/0x19d5a29c82afab60fe6047b8437c1858789b3150) |
| **Network** | Ethereum |
| **Price** | $0.00004274 |
| **24h Volume** | $78.3K |
| **Liquidity** | $17.3K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 13h |
| **Top-10 Holders** | 35.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 323 buys / 236 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc4fc30660423bd04ae1038c2910437d4c2e337498f19cea23df90f4c3e5cf88f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gta-vi-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
