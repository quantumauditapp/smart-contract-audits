---
token: 币安人生
ticker: 币安人生
network: bsc
risk_score: 46
status: medium
date: 2026-11-06
---

# 币安人生 (币安人生) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-33e4f6-bsc)

---

## Audit Summary

The FlapDirectTaxToken is a minimal clone (EIP-1167) implementing a tax-on-transfer token with migration-based state transitions. While the core ERC-20 logic is standard, the contract contains centralized control over tax and anti-sniper parameters. The protocol is not upgradeable, providing immutability for the logic, but it suffers from trapped ETH and reliance on tx.origin for authorization logic.

> **Final Recommendation:** Implement a withdrawal function to recover trapped ETH sent to the contract address. Replace the use of tx.origin with msg.sender to prevent potential security vulnerabilities associated with contract-based transaction chains.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes EIP-1167 minimal clones to ensure logic immutability, which is a strong security practice. 7.1 Architecture and 7.2 Code Security are generally sound, though 7.6 External… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance rely heavily on the owner's address. The owner has total control over tax rates and anti-sniper windows via finalizeMigration, which could be used to manipulate token… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is a minimal clone, ensuring the logic cannot be altered post-deployment. This provides high security against malicious logic updates. 7.8 Operations… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.2% (≈ permanent lock) |
| **LP Locked** | 99.2% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH but lacks any mechanism to withdraw it, meaning any funds sent to the contract are permanently locked.

**Recommendation:** Add an owner-restricted function to withdraw accidentally sent ETH from the contract balance.


### `CD-02` — Insecure Use of tx.origin  *(Severity: Medium · Status: Unresolved)*

The function _getTaxWithPoolState uses tx.origin for authorization, which is vulnerable to phishing attacks where a user is tricked into calling a malicious contract that then interacts with this token.

**Recommendation:** Refactor the code to use msg.sender instead of tx.origin for all authorization and rule-based logic.


### `CP-07` — Centralized Control Over Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The owner can modify the tax rates applied to token transfers using the finalizeMigration function, allowing for potential economic manipulation.

**Recommendation:** Introduce a timelock or a maximum cap on tax rates to limit the owner's ability to change fees arbitrarily.


### `CP-08` — Centralized Control Over Transfer Limits  *(Severity: Low · Status: Unresolved)*

The owner can adjust transaction and wallet limits via finalizeMigration, which directly impacts user liquidity and trading capabilities.

**Recommendation:** Document these limits clearly and consider making them immutable after a set period to increase trust.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.1% of supply. Of that, 21.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.6% in wallets, 5.0% in other contracts. 536 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

536 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.2% of the pool's LP is burned or time-locked. 99.2% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.8% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $169K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $20K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0aa4...7777`](https://bscscan.com/address/0x0aa4f116014fc09490fd4b5766f5c94c6c377777) |
| **Network** | BNB Chain |
| **Price** | $5.5300 |
| **24h Volume** | $169.3K |
| **Liquidity** | $19.7K |
| **Volume / Liquidity** | 8.6× |
| **Token Age** | 9h |
| **Top-10 Holders** | 33.1% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 4383 buys / 1262 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x6a6a781e01a4d76fc59efa08a377354066e9237f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-33e4f6-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
