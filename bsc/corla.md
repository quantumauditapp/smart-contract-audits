---
token: CORLA
ticker: CORLA
network: bsc
risk_score: 45
status: medium
date: 2026-11-05
---

# CORLA (CORLA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/corla-bsc)

---

## Audit Summary

The FlapDirectTaxToken is an EIP-1167 minimal clone implementing a tax-on-transfer mechanism with migration states. The contract is immutable post-deployment, meaning logic cannot be upgraded. While the core ERC-20 functionality is standard, the contract contains centralized control over tax and anti-sniper parameters, and lacks a mechanism to recover accidentally sent ETH.

> **Final Recommendation:** Implement a recovery function restricted to the owner to withdraw accidentally sent ETH from the contract balance. Additionally, consider introducing a timelock for the finalizeMigration function to provide transparency and protection to token holders regarding changes to tax and anti-sniper parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a standard EIP-1167 clone pattern, ensuring consistent logic across instances. 7.1 Architecture is sound for a fixed-logic token, and 7.2 Code Security follows modern Solidity… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are heavily centralized under the owner address. The owner can modify tax rates and anti-sniper windows via finalizeMigration, which directly impacts token holder… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is an EIP-1167 minimal clone. The logic is fixed at deployment, eliminating risks associated with malicious implementation updates. 7.8 Operations are… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — ETH sent to contract is permanently locked  *(Severity: Medium · Status: Unresolved)*

The contract can receive ETH but lacks any function to withdraw or transfer it out, meaning any ETH sent to the contract address is permanently inaccessible.

**Recommendation:** Add a function to allow the owner to withdraw ETH accidentally sent to the contract.


### `CD-02` — Use of tx.origin for authorization  *(Severity: Medium · Status: Unresolved)*

The _getTaxWithPoolState function relies on tx.origin for logic, which is vulnerable to phishing attacks where a user is tricked into calling a malicious contract that then interacts with this token.

**Recommendation:** Replace tx.origin with msg.sender to ensure the direct caller is the one being authorized.


### `CP-07` — Owner can modify transfer fees  *(Severity: Medium · Status: Unresolved)*

The finalizeMigration function allows the contract owner to change the tax rates applied to token transfers, directly impacting the amount received by users.

**Recommendation:** Document the tax logic clearly for users and consider implementing a maximum tax cap to prevent excessive fees.


### `CP-08` — Owner can modify transfer and wallet limits  *(Severity: Low · Status: Unresolved)*

The finalizeMigration function allows the owner to update anti-sniper windows and launch parameters, which control transaction limits and wallet restrictions.

**Recommendation:** Ensure these parameters are set to reasonable defaults and provide public notice before any significant changes.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 27.9% of supply. Of that, 18.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.2% in wallets, 3.7% in other contracts. 6,388 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,388 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 83% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $247K (DexScreener, all pools). 24h trading volume $4.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: 0% on buy, 1% on sell. Market: $247K of DEX liquidity across 7 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xba30...7777`](https://bscscan.com/address/0xba300df4c929eb137e266d17d1fe6db058837777) |
| **Network** | BNB Chain |
| **Price** | $0.5601 |
| **24h Volume** | $4.63M |
| **Liquidity** | $205.1K |
| **Volume / Liquidity** | 22.6× |
| **Token Age** | 9h |
| **Top-10 Holders** | 27.9% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 24321 buys / 19300 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe015a78814ebadeb0f202446e64b970642f9b965)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/corla-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
