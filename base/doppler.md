---
token: Doppler
ticker: XDP
network: base
risk_score: 46
status: medium
date: 2026-10-05
---

# Doppler (XDP) — Smart Contract Security Analysis | Base

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/doppler-base)

---

## Audit Summary

This audit covers a standard ERC-20 token contract. The contract implements basic token functionalities without any privileged roles or complex logic, resulting in a low overall risk profile. No specific vulnerabilities were identified during the analysis.

> **Final Recommendation:** Users should verify the contract address and ensure they are interacting with the intended token. Given the contract's immutable and standard ERC-20 nature, the primary security considerations shift to external factors such as front-end security and user wallet hygiene. Always exercise caution when approving token spending limits to third-party applications.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is a standard ERC-20 token, inheriting from `ERC20Burnable` and `ERC20`. It implements all core ERC-20 functions such as `transfer` and `balanceOf` (7.1 Architecture). Crucially, the… |
| **Governance / Economics** | 3/10 | High | The contract exhibits a highly decentralized governance and economic model due to the complete absence of privileged functions or owner roles (7.5 Governance). There are no mechanisms for an… |
| **Upgrades** | 8/10 | Low | The contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standalone implementation, which eliminates risks associated with proxy patterns such as storage collisions or improper… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.7% |
| **Top-3 Unlocked** | ⚠️ 96.5% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 98.4% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a wallet, 0x27a0…15f4 — holds 93.7% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 53% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.7% of supply. What remains: 57.2% in wallets, 38.5% in other contracts. 14,317 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Doppler Finance (XDP), market cap $21M, rank #891. 14,317 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $4.4M (DexScreener, all pools). 24h trading volume $219.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $262.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $4.4M of DEX liquidity across 30 pools. Launch: 6 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x07b3...91d0`](https://basescan.org/address/0x07b3d902783c3c12b077508c3b5c00113d1291d0) |
| **Network** | Base |
| **Price** | $0.02047 |
| **24h Volume** | $6.48M |
| **Liquidity** | $2.31M |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 6d |
| **Top-10 Holders** | 95.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7601 buys / 6885 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x1ef035205f94c7734827961c438474d089a334a0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/doppler-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
