---
token: 币安BNCB股票
ticker: 币安BNCB股票
network: bsc
risk_score: 42
status: medium
date: 2026-10-25
---

# 币安BNCB股票 (币安BNCB股票) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bncb-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token deployed on BSC. The contract ownership has been renounced, effectively disabling all privileged administrative functions. The codebase follows standard ERC-20 patterns with additional tax-enforcement logic. No critical or high-severity vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The protocol is currently in a secure, immutable state due to the renunciation of ownership. No further action is required for the smart contract logic itself. Users should remain aware that the tax-enforcement logic is permanently active as defined by the contract's state machine.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a robust EIP-1167 minimal clone architecture, ensuring immutability of the logic. Code security is maintained through standard OpenZeppelin library usage for ERC-20 and permit… |
| **Governance / Economics** | 4/10 | Medium | Economic parameters are fixed due to the renounced ownership, preventing arbitrary changes to tax logic. 7.4 Economic: Tax enforcement is hardcoded into the state machine. 7.5 Governance: No active… |
| **Upgrades** | 8/10 | Low | The contract is an EIP-1167 minimal clone, which is inherently immutable and cannot be upgraded. 7.7 Upgrades: No upgrade path exists for the implementation contract. The logic is fixed at… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xddac…308c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $148K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 38.9% of supply. What remains: 9.1% in wallets, 29.8% in other contracts. 2,038 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,038 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 0.99% on sell. Market: $10K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfa6a...7777`](https://bscscan.com/address/0xfa6ad3d1a9d954aa0c729d1f55f0234b259d7777) |
| **Network** | BNB Chain |
| **Price** | $0.0000102 |
| **24h Volume** | $108.3K |
| **Liquidity** | $9.6K |
| **Volume / Liquidity** | 11.2× |
| **Token Age** | 15h |
| **Top-10 Holders** | 38.9% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 7895 buys / 1200 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9e4852b63586573c7d0686085c98b93968558552)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bncb-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
