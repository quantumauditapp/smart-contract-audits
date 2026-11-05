---
token: 蝴蝶金库
ticker: 蝴蝶金库
network: bsc
risk_score: 27
status: low
date: 2026-11-05
---

# 蝴蝶金库 (蝴蝶金库) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-85060d-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token. Ownership has been renounced on-chain, rendering all privileged administrative functions permanently dormant. The contract logic is immutable, and the token functions as a standard ERC-20 with additional tax-enforcement states. No vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renouncement of ownership and the use of the EIP-1167 clone pattern. No further action is required for the current implementation. Users should monitor the token for standard market risks associated with tax-enforced tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a standard EIP-1167 minimal clone pattern, ensuring gas-efficient deployment. Code security is robust, adhering to modern Solidity 0.8.x standards with built-in overflow… |
| **Governance / Economics** | 6/10 | Medium | Governance is effectively decentralized as ownership is renounced, preventing any further changes to tokenomics or migration states. 7.4 Economic: Fixed state transitions. 7.5 Governance: None… |
| **Upgrades** | 9/10 | Low | The contract is an EIP-1167 minimal clone, which is inherently immutable and cannot be upgraded. 7.7 Upgrades: None. 7.8 Operations: Stable. There is no risk of malicious logic injection via proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xddac…308c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 53.3% of supply. Of that, 2.0% burned — not holders that can sell, so excluded from the concentration score. What remains: 3.2% in wallets, 48.1% in other contracts. 13,201 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

13,201 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $46K (DexScreener, all pools). 24h trading volume $222K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 2.97% on sell. Market: $46K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0795...7777`](https://bscscan.com/address/0x079594ae3f559d5d19b9ab32851aa4c8212d7777) |
| **Network** | BNB Chain |
| **Price** | $0.0002416 |
| **24h Volume** | $221.8K |
| **Liquidity** | $45.8K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 3h |
| **Top-10 Holders** | 53.3% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 3943 buys / 1252 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0707c5ce9f285b39b03a866b81439ce07e7926cb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-85060d-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
