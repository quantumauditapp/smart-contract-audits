---
token: Baola
ticker: 豹拉
network: bsc
risk_score: 41
status: medium
date: 2026-11-02
---

# Baola (豹拉) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/baola-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token. The ownership of the contract has been renounced on-chain, effectively disabling all privileged administrative functions. The contract logic is immutable, and the token operates as a standard ERC-20 with additional tax and migration state logic. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** The protocol is currently in a secure, immutable state due to the renounced ownership. No further action is required for the smart contract code itself. Users should continue to monitor the token's market activity and liquidity pools, as the contract logic is now fixed and cannot be altered by any party.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent logic deployment. Code security is robust, adhering to modern Solidity standards and utilizing OpenZeppelin's… |
| **Governance / Economics** | 1/10 | High | Economic parameters are fixed due to the renounced ownership, preventing any further manipulation of tax or migration states. 7.4 Economic and 7.5 Governance items are effectively locked, providing… |
| **Upgrades** | 8/10 | Low | The contract is an immutable EIP-1167 clone, meaning 7.7 Upgrades are not applicable as the logic cannot be changed. 7.8 Operations are stable and predictable. The lack of upgradeability is a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x5722…6512 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 52.9% of supply. Of that, 2.6% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.8% in wallets, 33.5% in other contracts. 5,561 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,561 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $307K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 0% on sell. Market: $13K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfffb...7777`](https://bscscan.com/address/0xfffbd7e5f455eda48ac4e80156354b39fb697777) |
| **Network** | BNB Chain |
| **Price** | $0.00001959 |
| **24h Volume** | $260.9K |
| **Liquidity** | $13.1K |
| **Volume / Liquidity** | 19.9× |
| **Token Age** | 7h |
| **Top-10 Holders** | 52.9% of supply |
| **Buy / Sell Tax** | 1.0% / 0.0% |
| **24h Transactions** | 3855 buys / 2590 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xc5c7884947d813d9598ec229d7b9292c36a8442c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/baola-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
