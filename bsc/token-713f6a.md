---
token: 翱翔天际的巨鸟
ticker: 长鹏
network: bsc
risk_score: 25
status: low
date: 2026-10-20
---

# 翱翔天际的巨鸟 (长鹏) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-713f6a-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation. The contract ownership has been renounced, effectively disabling all privileged administrative functions. The protocol operates as a static token with no further upgradeability or administrative control possible.

> **Final Recommendation:** As the contract ownership is renounced and the implementation is an immutable minimal clone, no further administrative actions are possible. Users should rely on the current on-chain state as the final and permanent configuration of the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent logic across deployments. Code security is robust, adhering to standard ERC-20 and EIP-712 specifications.… |
| **Governance / Economics** | 4/10 | Medium | Governance is non-existent due to the renouncement of ownership. Economic parameters are fixed and immutable, preventing any future manipulation of tax or migration states. The protocol relies on its… |
| **Upgrades** | 9/10 | Low | The contract is an immutable minimal clone, meaning the implementation logic cannot be altered. There are no proxy upgrade mechanisms present. The system is permanently locked in its current state. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 71.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xe5fb…d872 — holds 71.4% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.0% of supply. What remains: 11.0% in wallets, 21.0% in other contracts. 776 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

776 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $797K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0484...7777`](https://bscscan.com/address/0x0484372612d7a6c23959bc9492b03e047b537777) |
| **Network** | BNB Chain |
| **Price** | $0.00007826 |
| **24h Volume** | $759.1K |
| **Liquidity** | $26.0K |
| **Volume / Liquidity** | 29.2× |
| **Token Age** | 5h |
| **Top-10 Holders** | 32.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5639 buys / 5451 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd27d4f5995516035463c0315a6cae01d5b28f383)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-713f6a-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
