---
token: Niannian_GiggleAcademy
ticker: 年年
network: bsc
risk_score: 10
status: low
date: 2026-10-21
---

# Niannian_GiggleAcademy (年年) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nianniangiggleacademy-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with tax-enforced transfer logic. The contract ownership has been renounced on-chain, effectively locking the privileged migration functions and ensuring the current state is immutable. The architecture is standard for minimal clones, and the code security is robust due to the lack of active administrative control.

> **Final Recommendation:** The protocol is currently in a secure, immutable state due to the renunciation of ownership. No further action is required regarding the contract logic or access control. Users should continue to monitor the token's market behavior as the tax and anti-farmer mechanisms are now permanently active.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture is sound, utilizing standard OpenZeppelin upgradeable base contracts for… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance risks are minimal because the contract is immutable. Since ownership is renounced, no entity can manipulate the tax logic or migration states. The economic parameters… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not possible for this contract. As an EIP-1167 minimal clone, the implementation address is hardcoded into the bytecode. This design choice eliminates the risk of malicious logic… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 13.7% of supply. Of that, 3.5% burned — not holders that can sell, so excluded from the concentration score. What remains: 4.3% in wallets, 5.9% in other contracts. 7,254 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

7,254 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $163K (DexScreener, all pools). 24h trading volume $611K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $163K of DEX liquidity across 5 pools. Launch: 6 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf4d5...7777`](https://bscscan.com/address/0xf4d5765e448774ed9482870420da7c3c4c787777) |
| **Network** | BNB Chain |
| **Price** | $0.002487 |
| **24h Volume** | $611.2K |
| **Liquidity** | $162.6K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 6d |
| **Top-10 Holders** | 13.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3605 buys / 1931 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x3568b85ca64dce06dc08d1d65042aa737276eb41)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nianniangiggleacademy-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
