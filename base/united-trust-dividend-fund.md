---
token: United Trust Dividend Fund 🔥
ticker: UTDF
network: base
risk_score: 22
status: low
date: 2026-10-27
---

# United Trust Dividend Fund 🔥 (UTDF) — Smart Contract Security Analysis | Base

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-trust-dividend-fund-base)

---

## Audit Summary

The contract is a standard ERC-20 implementation utilizing OpenZeppelin libraries. It includes EIP-2612 permit functionality and standard metadata. No privileged roles or administrative functions were identified, ensuring a decentralized and immutable token structure.

> **Final Recommendation:** The contract is well-structured and adheres to established security standards. No further action is required for the current implementation.

Ensure that any future integrations or UI implementations correctly handle the EIP-2612 permit functionality to optimize user experience and gas efficiency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows industry-standard patterns for ERC-20 tokens, ensuring high compatibility with existing DeFi protocols. 7.1 Architecture is robust, utilizing modular OpenZeppelin components.… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance factors are not applicable as the contract lacks minting, burning, or administrative control mechanisms. The token supply is fixed upon deployment. 7.6 External… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not supported, as the contract is a standard implementation without proxy patterns. 7.8 Operations are straightforward, relying on standard ERC-20 interfaces. The lack of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xe627…8b13 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 34.7% of supply. What remains: 34.7% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 19.2%. 729 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

729 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $219K (DexScreener, all pools). 24h trading volume $2.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $219K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x201c...00b3`](https://basescan.org/address/0x201cea4860356bb8d65f8246f93c9b821fef00b3) |
| **Network** | Base |
| **Price** | $0.00000632 |
| **24h Volume** | $1.99M |
| **Liquidity** | $218.9K |
| **Volume / Liquidity** | 9.1× |
| **Token Age** | 10h |
| **Top-10 Holders** | 34.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2108 buys / 1581 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x7dc0434a9c4502ba0d8d349260e86b01e094c6f2d67ddc40db0ad008b982501b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-trust-dividend-fund-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
