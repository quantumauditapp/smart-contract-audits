---
token: BTC18
ticker: BTC18
network: bsc
risk_score: 33
status: low
date: 2026-11-04
---

# BTC18 (BTC18) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/btc18-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation. The contract utilizes standard OpenZeppelin upgradeable libraries for initialization but functions as an immutable clone post-deployment. The protocol features a migration mechanism controlled by the owner that transitions the token state between bonding curve, migration, and tax-enforced modes. No critical vulnerabilities were identified in the provided source analysis.

> **Final Recommendation:** The protocol is secure in its current implementation. It is recommended that the owner address be transitioned to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with centralized control over migration and tax parameters. Ensure that all future state transitions are documented and communicated to the community prior to execution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard EIP-1167 patterns, ensuring code consistency across clones. 7.1 Architecture and 7.2 Code Security are robust, utilizing well-audited OpenZeppelin libraries. 7.3… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance risks are centralized under the owner's control. The owner has the authority to trigger migration states, which directly impacts token tax logic and anti-farmer… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are effectively disabled due to the EIP-1167 minimal clone pattern, which points to a fixed implementation address. This provides high security against malicious logic updates. 7.8… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 43.0% of supply. What remains: 2.5% in wallets, 40.5% in other contracts. The deployer/owner wallet itself holds 34.2%. A holder that also controls the contract can sell into its own liquidity. 468 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

468 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $47K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8ce6...7777`](https://bscscan.com/address/0x8ce6f0fd88088f872944668ecbcdff6ed4537777) |
| **Network** | BNB Chain |
| **Price** | $0.00002661 |
| **24h Volume** | $46.7K |
| **Liquidity** | $22.3K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 3h |
| **Top-10 Holders** | 43.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 946 buys / 300 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x23369767b378be1565809cd5d75cd14151f37f59)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/btc18-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
