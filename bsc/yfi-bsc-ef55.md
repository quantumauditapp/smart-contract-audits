---
token: YFI
ticker: YFI
network: bsc
risk_score: 43
status: medium
date: 2026-11-07
---

# YFI (YFI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yfi-bsc-ef55)

---

## Audit Summary

The FlapDirectTaxToken is a minimal clone implementation of an ERC-20 token with integrated tax and anti-sniper mechanisms. While the core token logic follows standard patterns, the contract includes centralized administrative controls over transfer fees and trading limits. The audit identified risks related to trapped ETH and the use of tx.origin for authorization, which could impact security under specific conditions.

> **Final Recommendation:** It is recommended to implement a withdrawal function to recover any ETH accidentally sent to the contract address. Additionally, refactor the tax logic to rely on msg.sender rather than tx.origin to prevent potential security bypasses via intermediate contract calls.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes EIP-1167 minimal clones to ensure immutable logic deployment. Code security is generally robust, adhering to standard ERC-20 interfaces and safe math practices via Solidity… |
| **Governance / Economics** | 7/10 | Low | Economic parameters, including tax rates and anti-sniper windows, are fully controlled by the contract owner. This centralized governance allows for rapid response to market conditions but poses a… |
| **Upgrades** | 8/10 | Low | The contract is deployed as an EIP-1167 minimal clone, which is inherently immutable. There is no upgrade path for the logic contract, ensuring that the rules defined at deployment remain consistent.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — ETH trapped in contract  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH but lacks a mechanism to withdraw it, meaning any ETH sent to the contract will be permanently locked.

**Recommendation:** Add a function restricted to the owner that allows for the withdrawal of accidentally sent ETH.


### `CD-02` — Use of tx.origin for authorization  *(Severity: Medium · Status: Unresolved)*

The _getTaxWithPoolState function uses tx.origin to determine tax rules, which is vulnerable to phishing attacks where a user is tricked into calling a malicious contract that then interacts with this token.

**Recommendation:** Replace tx.origin with msg.sender to ensure that the immediate caller is the one being evaluated for tax rules.


### `CP-07` — Owner can modify transfer fees  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to change the tax fees applied to token transfers via the finalizeMigration function, which could be used to unexpectedly increase costs for users.

**Recommendation:** Implement a timelock or a maximum fee cap to limit the owner's ability to change tax rates arbitrarily.


### `CP-08` — Owner can modify trading limits  *(Severity: Low · Status: Unresolved)*

The owner can adjust transfer or wallet limits through the finalizeMigration function, potentially restricting user access to their tokens.

**Recommendation:** Document these limits clearly in the project's public documentation and consider using a multi-sig wallet for the owner address.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 20.7% of supply. Of that, 8.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.8% in wallets, 2.4% in other contracts. 1,684 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,684 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $46K (DexScreener, all pools). 24h trading volume $271K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $46K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2766...7777`](https://bscscan.com/address/0x276681605b6a85894ef4d9a580050047e36a7777) |
| **Network** | BNB Chain |
| **Price** | $2,859.4000 |
| **24h Volume** | $271.4K |
| **Liquidity** | $45.6K |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 3h |
| **Top-10 Holders** | 20.7% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 2036 buys / 3601 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x4cfd8265853526e4fcb988b5a80d6d8ab962075c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yfi-bsc-ef55)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
