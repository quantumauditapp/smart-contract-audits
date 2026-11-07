---
token: BTC
ticker: 比特币
network: bsc
risk_score: 48
status: medium
date: 2026-11-07
---

# BTC (比特币) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/btc-bsc)

---

## Audit Summary

The FlapDirectTaxToken is a tax-enabled ERC-20 token deployed as an EIP-1167 minimal clone. The contract implements custom migration logic that allows the owner to enforce tax and anti-sniper rules. While the core ERC-20 functionality is standard, the contract contains centralized control over economic parameters and lacks a mechanism to recover accidentally sent ETH.

> **Final Recommendation:** The protocol should implement a function to allow the owner or a designated address to withdraw accidentally sent ETH to prevent permanent loss of funds. Additionally, the reliance on tx.origin for tax calculations should be refactored to use msg.sender to align with standard security practices and prevent potential manipulation by intermediary contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a standard EIP-1167 proxy pattern, ensuring the implementation logic remains immutable post-deployment. 7.1 Architecture is sound for a token, and 7.2 Code Security is generally… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance are heavily centralized under the contract owner. The owner has the authority to trigger migration phases that fundamentally alter the token's tax and anti-sniper… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is an EIP-1167 minimal clone. The implementation logic is fixed at the time of deployment, preventing any future logic changes. This provides high… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — ETH cannot be withdrawn  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH but lacks any function to withdraw or transfer it out, meaning any ETH sent to the contract is permanently locked.

**Recommendation:** Add an owner-restricted function to withdraw ETH from the contract balance.


### `CD-02` — Insecure use of tx.origin  *(Severity: Medium · Status: Unresolved)*

The _getTaxWithPoolState function uses tx.origin to determine authorization or rules, which is vulnerable to phishing attacks via malicious smart contracts.

**Recommendation:** Replace tx.origin with msg.sender to ensure that the immediate caller is the one being validated.


### `CP-07` — Owner can modify transfer fees  *(Severity: Medium · Status: Unresolved)*

The finalizeMigration function allows the contract owner to enforce and change tax rates applied to token transfers, directly impacting user balances.

**Recommendation:** Implement a timelock or a multi-signature requirement for changes to economic parameters to increase transparency and trust.


### `CP-08` — Owner can modify transfer and wallet limits  *(Severity: Low · Status: Unresolved)*

The finalizeMigration function allows the owner to set numeric limits on transactions and wallet holdings, which can restrict user activity.

**Recommendation:** Document these limits clearly in the project's whitepaper or documentation to ensure users are aware of potential restrictions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.9% of supply. Of that, 2.3% burned, 13.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.1% in wallets, 2.9% in other contracts. 634 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

634 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 79% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $27K (DexScreener, all pools). 24h trading volume $487K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $27K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6f6e...7777`](https://bscscan.com/address/0x6f6e44925c17e7290c2032fd2d0731ac861e7777) |
| **Network** | BNB Chain |
| **Price** | $281.1100 |
| **24h Volume** | $478.4K |
| **Liquidity** | $21.4K |
| **Volume / Liquidity** | 22.3× |
| **Token Age** | 2h |
| **Top-10 Holders** | 29.9% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 4195 buys / 4357 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x3f95dfce2d6bd72fba4433a50b54ac7bbcc64e02)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/btc-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
