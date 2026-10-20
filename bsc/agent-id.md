---
token: Agent ID
ticker: .AI
network: bsc
risk_score: 30
status: low
date: 2026-10-20
---

# Agent ID (.AI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agent-id-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom tax and migration logic. The contract ownership has been renounced, effectively locking the privileged migration functions and preventing further administrative changes to the token's economic parameters. The architecture is standard for immutable clones, and no critical vulnerabilities were identified in the current state.

> **Final Recommendation:** The contract is in a secure, immutable state due to the renunciation of ownership. No further action is required for the current deployment. Users should be aware that the tax and migration logic is permanently fixed and cannot be adjusted by any entity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture: Immutable clone pattern prevents logic tampering. 7.2 Code Security: Standard… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: The token features a tax-enforced mechanism that is now permanently fixed due to the renounced ownership. 7.5 Governance: Governance is effectively non-existent as the owner role is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The contract is deployed as an EIP-1167 minimal clone, which is inherently immutable and cannot be upgraded. 7.8 Operations: Operational risk is minimal as the contract logic is fixed… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.8% of supply. What remains: 10.8% in wallets, 22.1% in other contracts. 674 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

674 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $43K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $43K of DEX liquidity across 9 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5943...7777`](https://bscscan.com/address/0x5943d989cd95388b4dfaa9a61fd66843e6e57777) |
| **Network** | BNB Chain |
| **Price** | $0.0002013 |
| **24h Volume** | $947.8K |
| **Liquidity** | $43.4K |
| **Volume / Liquidity** | 21.8× |
| **Token Age** | 5h |
| **Top-10 Holders** | 32.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6380 buys / 5581 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x574d77ff94a6cf559eaa5d0f42f8f1ba02db50ca)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agent-id-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
