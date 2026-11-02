---
token: Genesis
ticker: GENESIS
network: bsc
risk_score: 38
status: medium
date: 2026-11-02
---

# Genesis (GENESIS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/genesis-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation of an ERC-20 token with custom tax and migration logic. The contract is immutable due to the clone pattern, preventing logic upgrades. The owner maintains significant control over the migration state, which dictates tax enforcement and anti-farmer mechanisms. No critical vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The protocol is structurally sound due to its immutable nature. We recommend that the owner address be transitioned to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with centralized control over migration and tax parameters.

Users should monitor the migration state transitions via events, as these changes directly impact the token's economic behavior. No further technical remediation is required at this time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes EIP-1167 minimal clones, ensuring the implementation remains fixed and immutable. 7.1 Architecture and 7.2 Code Security are robust, leveraging standard OpenZeppelin… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are centralized under the contract owner. The owner has the authority to trigger migration states, which directly influence tax enforcement and anti-farmer… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are not applicable as the contract is deployed as an EIP-1167 minimal clone. The implementation address is hardcoded into the clone's bytecode, making the logic immutable. This… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 53.6% of supply. What remains: 19.0% in wallets, 34.6% in other contracts. 157 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

157 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $76K (DexScreener, all pools).

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
| **Contract** | [`0xfbd2...7777`](https://bscscan.com/address/0xfbd273a07438b33d637e17aa8abf1d2290847777) |
| **Network** | BNB Chain |
| **Price** | $0.00002584 |
| **24h Volume** | $76.3K |
| **Liquidity** | $22.2K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 2h |
| **Top-10 Holders** | 53.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 764 buys / 525 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa64a783651c109c9f12e74e913fcf9dab63ad5ac)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/genesis-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
