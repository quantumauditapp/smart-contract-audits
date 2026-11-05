---
token: 雪球
ticker: 雪球
network: bsc
risk_score: 51
status: medium
date: 2026-11-05
---

# 雪球 (雪球) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-0bbc4c-bsc)

---

## Audit Summary

The FlapDirectTaxToken is an EIP-1167 minimal clone implementing a tax-on-transfer mechanism with migration states. The architecture is immutable, as the implementation address is fixed via the clone pattern. While the core ERC-20 functionality is standard, the contract contains centralized control over tax and anti-sniper parameters, and exhibits minor design flaws regarding ETH handling and authorization patterns.

> **Final Recommendation:** We recommend replacing the use of tx.origin with msg.sender to prevent potential cross-contract manipulation. Additionally, implement a rescue function restricted to the owner to allow for the withdrawal of accidentally sent ETH or other tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a standard EIP-1167 clone pattern, ensuring consistent logic across deployments. Code security is generally high with standard ERC-20 implementations. However, the use of… |
| **Governance / Economics** | 5/10 | Medium | The protocol relies on a single owner to manage migration states and tax enforcement. The owner has the power to finalize migration, which triggers anti-sniper windows and tax expiration times. This… |
| **Upgrades** | 8/10 | Low | The contract is an EIP-1167 minimal clone, which is inherently immutable. There is no upgrade mechanism present, meaning the logic cannot be altered after deployment. This eliminates risks associated… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Inaccessible ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract can receive ETH but lacks any function to withdraw or transfer it, resulting in any ETH sent to the contract being permanently locked.

**Recommendation:** Add an owner-restricted function to withdraw ETH from the contract balance.


### `CD-02` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The _getTaxWithPoolState function uses tx.origin to determine tax rules, which is vulnerable to phishing attacks where a user is tricked into interacting with a malicious contract.

**Recommendation:** Replace tx.origin with msg.sender to ensure that the immediate caller is the one being authorized.


### `CP-07` — Centralized Control Over Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The owner can modify the tax rates and transfer fees via the finalizeMigration function, which directly impacts the economic behavior of the token.

**Recommendation:** Implement a timelock or a multi-signature wallet for the owner address to increase transparency and security for fee adjustments.


### `CP-08` — Centralized Control Over Transfer Limits  *(Severity: Low · Status: Unresolved)*

The owner has the authority to change wallet limits and transaction thresholds through the finalizeMigration function, potentially restricting user activity.

**Recommendation:** Document these parameters clearly in the project's public documentation and consider moving to a decentralized governance model for parameter changes.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.3% of supply. Of that, 24.8% burned, 12.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.8% in wallets, 1.0% in other contracts. 1,235 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,235 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $29K (DexScreener, all pools). 24h trading volume $743K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $29K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x181e...7777`](https://bscscan.com/address/0x181e5757d2a2f0eabd189fdc6446f9e2cf527777) |
| **Network** | BNB Chain |
| **Price** | $0.1076 |
| **24h Volume** | $743.0K |
| **Liquidity** | $28.8K |
| **Volume / Liquidity** | 25.8× |
| **Token Age** | 9h |
| **Top-10 Holders** | 48.3% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 6770 buys / 5725 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x36a69bd7a3277d50de1e4532aa069501f371b2b8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-0bbc4c-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
