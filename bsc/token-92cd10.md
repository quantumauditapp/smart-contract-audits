---
token: 孔子学院
ticker: 孔子学院
network: bsc
risk_score: 30
status: low
date: 2026-10-24
---

# 孔子学院 (孔子学院) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-92cd10-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with tax-enforced transfer logic. The contract ownership has been renounced on-chain, rendering all privileged administrative functions (startMigration, finalizeMigration) permanently dormant. The architecture is immutable and secure against unauthorized state changes.

> **Final Recommendation:** The contract is in a secure, immutable state due to the renunciation of ownership. No further action is required to secure the administrative functions as they are permanently disabled.

Users should be aware that the tax-enforced transfer logic is permanent and cannot be adjusted. Ensure that the current tax parameters align with long-term project requirements, as no future modifications are possible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 and EIP-712 functionality, ensuring robust compliance with token standards. 7.1 Architecture: The EIP-1167 clone pattern provides a… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: The token implements a tax-enforced mechanism that is locked into the contract state. 7.5 Governance: Governance is effectively non-existent due to the renounced ownership. 7.8… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades: The contract is a minimal clone, which is inherently immutable. There is no proxy upgrade mechanism present. The implementation address is fixed at deployment, ensuring long-term… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x2d6c…043c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.5% of supply. What remains: 11.3% in wallets, 45.2% in other contracts. 324 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

324 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $392K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 0.99% on sell. Market: $11K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd98f...7777`](https://bscscan.com/address/0xd98f1781cb8d19b6cabc5a3390ebfa99169d7777) |
| **Network** | BNB Chain |
| **Price** | $0.00001453 |
| **24h Volume** | $354.8K |
| **Liquidity** | $10.9K |
| **Volume / Liquidity** | 32.6× |
| **Token Age** | 13h |
| **Top-10 Holders** | 56.5% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 3237 buys / 3145 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xee7fe6e3046966861633e067c70f8cb34321dcdb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-92cd10-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
