---
token: BURN
ticker: BURN
network: bsc
risk_score: 48
status: medium
date: 2026-11-05
---

# BURN (BURN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/burn-bsc-5a8a)

---

## Audit Summary

The FlapDirectTaxToken is an EIP-1167 minimal clone implementing standard ERC-20 functionality with custom tax and anti-sniper mechanisms. The contract is not upgradeable, providing immutability for the logic, but the owner retains significant control over economic parameters via migration functions. Key risks include the inability to recover trapped ETH and the use of tx.origin for authorization, which may introduce security vulnerabilities in specific interaction patterns.

> **Final Recommendation:** It is recommended to implement an emergency withdrawal function to recover any ETH accidentally sent to the contract. Additionally, refactor the authorization logic to use msg.sender instead of tx.origin to prevent potential cross-contract manipulation vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes EIP-1167 clones for gas-efficient deployment, ensuring the logic remains immutable post-deployment. 7.1 Architecture and 7.2 Code Security are generally sound, though the… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance aspects are centralized under the contract owner. The owner has the authority to finalize migration, which triggers tax enforcement and anti-sniper windows. While this… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is an EIP-1167 minimal clone, meaning the implementation logic is fixed at deployment. 7.8 Operations are stable, but the lack of an emergency… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — ETH trapped in contract  *(Severity: Medium · Status: Unresolved)*

The contract can receive ETH but lacks any function to withdraw or transfer it, meaning any funds sent to the contract address will be permanently locked.

**Recommendation:** Add a restricted function to allow the owner to withdraw accidentally sent ETH.


### `CD-02` — Use of tx.origin for authorization  *(Severity: Medium · Status: Unresolved)*

The _getTaxWithPoolState function uses tx.origin to determine tax rules, which is vulnerable to phishing attacks where a user is tricked into interacting with a malicious contract that then calls the token contract.

**Recommendation:** Replace tx.origin with msg.sender to ensure that the immediate caller is the one being authorized.


### `CP-07` — Owner can modify transfer fees  *(Severity: Medium · Status: Unresolved)*

The finalizeMigration function allows the owner to set and modify the tax rates applied to token transfers, directly impacting the economic cost for users.

**Recommendation:** Implement a timelock or a maximum fee cap to prevent sudden, unexpected changes to the tax structure.


### `CP-08` — Owner can modify transfer and wallet limits  *(Severity: Low · Status: Unresolved)*

The finalizeMigration function allows the owner to adjust numeric limits such as anti-sniper windows and launch parameters, which dictate how users can interact with the token.

**Recommendation:** Document these parameters clearly in the UI and consider making them immutable after the launch phase.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 71.6% of supply. Of that, 19.1% burned, 33.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.7% in wallets, 4.1% in other contracts. 161 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

161 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $244K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $12K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x39ac...7777`](https://bscscan.com/address/0x39ac588c1b099d810dcabcd1857faec0202c7777) |
| **Network** | BNB Chain |
| **Price** | $0.01748 |
| **24h Volume** | $243.8K |
| **Liquidity** | $11.5K |
| **Volume / Liquidity** | 21.1× |
| **Token Age** | 8h |
| **Top-10 Holders** | 71.6% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 2699 buys / 2469 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9f8461512a8545cdf39a44240790733ab9f81bdd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/burn-bsc-5a8a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
