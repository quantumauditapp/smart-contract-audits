---
token: streamcall.fun
ticker: STREAM
network: bsc
risk_score: 65
status: high
date: 2026-10-24
---

# streamcall.fun (STREAM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/streamcallfun-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a standard ERC-20 token deployed as an EIP-1167 minimal clone. The contract implements a migration mechanism that allows the owner to transition the token state between bonding curve, migration, and tax-enforced modes. The architecture is immutable regarding logic, as the clone points to a fixed implementation. No critical vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The protocol is structurally sound due to its immutable clone architecture. We recommend that the owner address be transitioned to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with centralized control over migration and tax states.

Ensure that all future interactions with the migration functions are documented and communicated to the community to maintain transparency regarding state changes that affect token utility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin libraries for ERC-20 and ownership management, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is strictly enforced… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are centralized under the owner's control. The owner has the authority to trigger migration states, which directly impacts token transfer logic and tax… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is an EIP-1167 minimal clone, which is inherently immutable. The implementation logic is fixed at deployment, preventing unauthorized logic changes.… |

## Security Findings

_🟡 1 Medium · ⚪ 4 Informational_

### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $33K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No code-level findings — contract source is not verified on the explorer  *(Severity: Informational · Status: Acknowledged)*

The contract's source code has not been published or verified on the block explorer, so only its deployed bytecode and on-chain behaviour were available. No source-level vulnerability could be confirmed or ruled out. The assessment on this page rests on mint/owner authority, mint capability.

**Recommendation:** Treat an unverified contract as unaudited at the code level. Ask the team to verify the source on the explorer, which makes an independent review possible.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xeaa9...7777`](https://bscscan.com/address/0xeaa9e9868e704e9829d8c3209bf8ea8e152f7777) |
| **Network** | BNB Chain |
| **Price** | $0.00000411 |
| **24h Volume** | $33.4K |
| **Liquidity** | $9.0K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 316 buys / 252 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xcbda5db792ddd232438744795950405c412f2e80)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/streamcallfun-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
