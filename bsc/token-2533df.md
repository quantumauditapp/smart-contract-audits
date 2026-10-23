---
token: 三星堆:未来往事
ticker: 三星堆
network: bsc
risk_score: 28
status: low
date: 2026-10-23
---

# 三星堆:未来往事 (三星堆) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-2533df-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a standard ERC-20 token deployed as an EIP-1167 minimal clone. The contract ownership has been formally renounced, rendering all privileged administrative functions permanently inaccessible. The codebase is clean and utilizes standard OpenZeppelin libraries for core functionality. No vulnerabilities were identified in the provided source code.

> **Final Recommendation:** The contract is in a secure, immutable state. No further action is required as the administrative functions are permanently disabled and the logic is fixed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the EIP-1167 minimal clone pattern, which is gas-efficient and immutable by design. 7.1 Architecture: The logic is fixed and cannot be altered post-deployment. 7.2 Code… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: The tokenomics are fixed and immutable. 7.5 Governance: Governance is non-existent as ownership is renounced. 7.6 External: The contract does not rely on external oracles or complex… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades: The contract is an immutable minimal clone and cannot be upgraded. 7.8 Operations: Operational risks are minimal as the contract state is locked. No upgrade paths exist for the logic or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x6ff3…b322 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.4% of supply. What remains: 5.9% in wallets, 42.6% in other contracts. 564 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

564 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $14K (DexScreener, all pools). 24h trading volume $914K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $14K of DEX liquidity across 4 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x637a...7777`](https://bscscan.com/address/0x637a7dcb36ec545e751e4c332efa64614a9d7777) |
| **Network** | BNB Chain |
| **Price** | $0.00002169 |
| **24h Volume** | $882.1K |
| **Liquidity** | $13.7K |
| **Volume / Liquidity** | 64.3× |
| **Token Age** | 4h |
| **Top-10 Holders** | 48.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6818 buys / 6133 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x3b104c6adf53dc10d6c169da681962fa25681097)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-2533df-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
