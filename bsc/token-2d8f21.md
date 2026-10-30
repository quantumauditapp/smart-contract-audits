---
token: 币安加油
ticker: 币安加油
network: bsc
risk_score: 34
status: low
date: 2026-10-30
---

# 币安加油 (币安加油) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 34/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-2d8f21-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with migration-based state transitions. Ownership has been formally renounced on-chain, rendering all privileged administrative functions (startMigration, finalizeMigration) permanently dormant. The architecture is immutable, and the code follows standard OpenZeppelin patterns for upgradeable contracts, though the clone pattern ensures no future logic changes are possible.

> **Final Recommendation:** The contract is secure due to the renunciation of ownership and the immutable nature of the EIP-1167 clone pattern. No further action is required as the administrative functions are permanently disabled.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone architecture, ensuring bytecode immutability. 7.1 Architecture: The design is modular and follows standard ERC-20 patterns. 7.2 Code Security… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: The tokenomics are fixed by the immutable state machine. 7.5 Governance: Governance is effectively non-existent as ownership is renounced. 7.6 External: The contract does not rely on… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The contract is a minimal clone, which is inherently immutable and cannot be upgraded. 7.8 Operations: Operational risks are minimized by the lack of administrative control. No upgrade… |

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

The ten largest holders own 54.2% of supply. Of that, 1.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 9.0% in wallets, 43.4% in other contracts. 17,579 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

17,579 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $205K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 0% on sell. Market: $10K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2648...7777`](https://bscscan.com/address/0x264844a1afa0512323c5575bf6701ce51f3a7777) |
| **Network** | BNB Chain |
| **Price** | $0.00001194 |
| **24h Volume** | $158.2K |
| **Liquidity** | $10.1K |
| **Volume / Liquidity** | 15.7× |
| **Token Age** | 9h |
| **Top-10 Holders** | 54.2% of supply |
| **Buy / Sell Tax** | 1.0% / 0.0% |
| **24h Transactions** | 5766 buys / 1729 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x91777072e6aa8aab4ea0cccd2cab5661202f3395)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-2d8f21-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
