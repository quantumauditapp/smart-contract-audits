---
token: Binance AI
ticker: BIBI
network: bsc
risk_score: 15
status: low
date: 2026-10-16
---

# Binance AI (BIBI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-ai-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an EIP-1167 minimal clone, functioning as an ERC-20 token. Ownership has been renounced, making all owner-restricted functions, including those that modify transfer parameters like `poolState`, permanently inactive. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** Users should be aware that the FlapTaxTokenV3 contract is immutable, with its core parameters, including any transfer taxes or anti-farmer mechanisms, permanently fixed due to renounced ownership. This design choice provides a high degree of stability and predictability, as no administrative entity can alter the token's behavior. It is recommended to verify the renounced ownership status on-chain to confirm the immutability of the contract's operational logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FlapTaxTokenV3 contract is a well-implemented ERC-20 token deployed as an EIP-1167 minimal clone (7.1 Architecture). Its core ERC-20 functionalities are standard and robust (7.2 Code Security). A… |
| **Governance / Economics** | 7/10 | Low | The economic model of the FlapTaxTokenV3 is highly stable due to the renounced ownership (7.4 Economic). The `poolState` variable, which influences transfer taxes and anti-farmer mechanisms, cannot… |
| **Upgrades** | 8/10 | Low | The FlapTaxTokenV3 is deployed as an EIP-1167 minimal clone, which means its implementation is fixed and cannot be upgraded or changed (7.7 Upgrades). This design choice inherently eliminates all… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 24.0% of supply. What remains: 3.5% in wallets, 20.4% in other contracts. 1,598 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,598 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $159K (DexScreener, all pools). 24h trading volume $785K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 0.99% on sell. Market: $159K of DEX liquidity across 4 pools. Launch: 4 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x409f...7777`](https://bscscan.com/address/0x409f0bcdc9a70565a71af56cb50b2a6688cb7777) |
| **Network** | BNB Chain |
| **Price** | $0.001867 |
| **24h Volume** | $780.5K |
| **Liquidity** | $133.8K |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 4d |
| **Top-10 Holders** | 24.0% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 2090 buys / 1936 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xed76af88fd8c74bd287468348600c9643efb7dcf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-ai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
