---
token: MAMESUKE
ticker: MAMESUKE
network: ethereum
risk_score: 56
status: medium
date: 2026-11-03
---

# MAMESUKE (MAMESUKE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mamesuke-eth-8eca)

---

## Audit Summary

The MAMESUKE token is a standard ERC-20 implementation with additional custom logic. The audit identified critical flaws in the return value handling of transfer functions and insecure usage of tx.origin for authorization logic. While the contract follows standard ERC-20 patterns, these specific implementation choices introduce significant risks to integration with external protocols and potential security bypasses.

> **Final Recommendation:** The contract must be updated to ensure that transfer and transferFrom functions strictly adhere to the ERC-20 standard by returning a boolean value that accurately reflects the success of the operation. Additionally, all instances of tx.origin must be replaced with msg.sender to prevent unauthorized access and potential manipulation by malicious intermediary contracts.

Developers should perform a thorough refactor of the transfer path to ensure compatibility with DeFi protocols that rely on standard ERC-20 return values. Post-fix, a comprehensive suite of unit tests should be implemented to verify standard compliance and access control integrity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract architecture relies on standard OpenZeppelin-like ERC-20 patterns for core functionality. 7.1 Architecture is straightforward, but 7.2 Code Security is compromised by non-standard return… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance aspects are minimal as the contract lacks administrative functions or complex economic parameters. There are no minting or burning mechanisms that could impact token… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is not a proxy and lacks upgradeability patterns. The code is immutable. 7.8 Operations are limited to standard token transfers. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `CD-01` — Non-Compliant Transfer Return Values  *(Severity: High · Status: Unresolved)*

The transfer and transferFrom functions do not correctly handle return values, which can cause external protocols (like DEXs or lending platforms) to fail or misinterpret the success of a transaction.

**Recommendation:** Ensure that all transfer functions explicitly return a boolean 'true' upon successful execution and revert on failure, adhering strictly to the ERC-20 specification.


### `CD-02` — Insecure Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The use of tx.origin in the returnTx function allows an attacker to trick a user into interacting with a malicious contract, which can then perform actions on behalf of the user by bypassing standard msg.sender checks.

**Recommendation:** Replace all occurrences of tx.origin with msg.sender to ensure that authorization is tied to the immediate caller, preventing unauthorized contract-based interactions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.2% of supply. What remains: 26.6% in wallets, 9.6% in other contracts. 164 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

164 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $43K (DexScreener, all pools). 24h trading volume $260K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $43K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x158c...c45f`](https://etherscan.io/address/0x158c9abd9d104c60cabf9870fbe92f3b30a0c45f) |
| **Network** | Ethereum |
| **Price** | $0.0002259 |
| **24h Volume** | $259.7K |
| **Liquidity** | $43.0K |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 3h |
| **Top-10 Holders** | 36.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 510 buys / 234 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xd7c2edea3634525d009d3dac752d71a894de1eb7de76ffcb9912322bc6c07c4d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mamesuke-eth-8eca)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
