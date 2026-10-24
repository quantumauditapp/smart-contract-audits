---
token: 信念
ticker: CONVICTION
network: bsc
risk_score: 29
status: low
date: 2026-10-24
---

# 信念 (CONVICTION) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/conviction-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with tax-enforced transfer logic. The contract ownership has been renounced on-chain, rendering all privileged administrative functions (startMigration, finalizeMigration) permanently inaccessible. The code follows standard OpenZeppelin patterns for token functionality and initialization.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renouncement of ownership. No further administrative actions are possible, which eliminates the risk of rug-pulls or unauthorized parameter changes via the migration functions. Users should verify the current state of the poolState to understand the active tax enforcement parameters, as these are now permanent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a robust EIP-1167 minimal clone pattern, ensuring immutable logic deployment. 7.1 Architecture: Standardized clone pattern. 7.2 Code Security: Implementation uses secure… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: The token utilizes a tax-enforced mechanism that is now immutable due to ownership renouncement. 7.5 Governance: No active governance exists as the owner role is nullified. 7.8… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades: The contract is a minimal clone, meaning the implementation logic is fixed and cannot be upgraded. The use of Initializable base contracts is strictly for the deployment phase and does… |

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

The ten largest holders own 52.6% of supply. Of that, 2.4% burned — not holders that can sell, so excluded from the concentration score. What remains: 4.1% in wallets, 46.1% in other contracts. 867 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

867 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $314K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 2.97% on sell. Market: $13K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9ac2...7777`](https://bscscan.com/address/0x9ac2821707aa22be4984bfaf76bbcdf317dd7777) |
| **Network** | BNB Chain |
| **Price** | $0.00001731 |
| **24h Volume** | $286.6K |
| **Liquidity** | $12.5K |
| **Volume / Liquidity** | 22.9× |
| **Token Age** | 23h |
| **Top-10 Holders** | 52.6% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 3762 buys / 2103 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb8af7b6bea65cc89e525b5a2254355695c6790b0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/conviction-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
