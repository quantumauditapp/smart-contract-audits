---
token: SIGH
ticker: SIGH
network: bsc
risk_score: 35
status: medium
date: 2026-10-20
---

# SIGH (SIGH) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sigh-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom tax and migration logic. The contract ownership has been renounced on-chain, effectively disabling all administrative functions, including migration state transitions. The code follows standard OpenZeppelin patterns for token functionality and initialization. No vulnerabilities were identified in the current state.

> **Final Recommendation:** The contract is in a secure, immutable state due to the renounced ownership. No further action is required for the current deployment. Users should verify the contract address against official documentation to ensure they are interacting with the intended clone.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a gas-efficient EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture and 7.2 Code Security are robust, leveraging standard OpenZeppelin… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance parameters are effectively locked due to the renounced ownership. The token logic relies on a fixed state machine that cannot be altered by any external actor. This… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are impossible for this contract as it is a minimal clone with a fixed implementation address. The use of Initializable ensures that the contract state is set correctly upon deployment.… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.5% of supply. What remains: 11.1% in wallets, 31.4% in other contracts. 519 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

519 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $61K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 1.98% on sell. Market: $18K of DEX liquidity across 3 pools. Launch: 17 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 17 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 17 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6b5b...7777`](https://bscscan.com/address/0x6b5b4cc9f07d10cc48e75d234cfe04a0931b7777) |
| **Network** | BNB Chain |
| **Price** | $0.00003832 |
| **24h Volume** | $61.4K |
| **Liquidity** | $18.1K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 17d |
| **Top-10 Holders** | 42.5% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 528 buys / 405 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8dadf48991fd39efa507a5ea52757bd27ee265ae)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sigh-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
