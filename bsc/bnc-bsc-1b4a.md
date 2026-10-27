---
token: bnc的新名字
ticker: BNB STANDARD
network: bsc
risk_score: 21
status: low
date: 2026-10-27
---

# bnc的新名字 (BNB STANDARD) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnc-bsc-1b4a)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with migration-based tax logic. The contract ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The architecture is immutable, and the token logic is fixed, providing high confidence in the current state of the contract.

> **Final Recommendation:** No security issues were identified. Since ownership has been renounced, the contract is immutable and no further administrative actions can be taken. Users should note that the current tax and migration state is permanent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture is robust due to the immutable nature of the clone. 7.2 Code Security is high… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic parameters are fixed due to the renounced ownership. 7.5 Governance is non-existent as the contract is fully decentralized and immutable. The economic model relies on the pre-set… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are impossible for this contract. As an EIP-1167 clone, the implementation address is hardcoded into the bytecode. This eliminates risks associated with malicious proxy upgrades or… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 22.1% of supply. What remains: 4.1% in wallets, 18.0% in other contracts. 8,407 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

8,407 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $44K (DexScreener, all pools). 24h trading volume $502K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 0.99% on sell. Market: $44K of DEX liquidity across 2 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7f5e...7777`](https://bscscan.com/address/0x7f5ec95dcce46c1b12300bce604454de58f87777) |
| **Network** | BNB Chain |
| **Price** | $0.0002071 |
| **24h Volume** | $468.4K |
| **Liquidity** | $43.6K |
| **Volume / Liquidity** | 10.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | 22.1% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 5585 buys / 2735 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x6badb317a1b52fa7c89bfb40b96938bd0c152ead)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnc-bsc-1b4a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
