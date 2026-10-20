---
token: Cao Zhen
ticker: CZ
network: bsc
risk_score: 21
status: low
date: 2026-10-08
---

# Cao Zhen (CZ) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cao-zhen-bsc)

---

## Audit Summary

The audit of the BrewDividendToken contract found it to be a standard ERC-20 implementation with no privileged functions or complex logic. No critical or high-severity vulnerabilities were identified, indicating a robust and secure design for its intended purpose.

> **Final Recommendation:** Given the contract's simplicity as a standard ERC-20 token with no identified vulnerabilities, the primary recommendation is to ensure thorough testing of all standard ERC-20 functionalities. Implement robust monitoring for contract interactions and token transfers to detect any unusual activity. Adhere to best practices for key management and operational security (7.8 Operations).

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The BrewDividendToken contract is a straightforward ERC-20 implementation (7.1 Architecture). It includes all standard ERC-20 functions like `transfer` and `balanceOf`. The static analysis indicates… |
| **Governance / Economics** | 2/10 | High | The contract does not incorporate any complex economic models, staking mechanisms, or governance features (7.4 Economic, 7.5 Governance). Its simplicity as a standard token reduces the surface area… |
| **Upgrades** | 8/10 | Low | The BrewDividendToken is not implemented as a proxy contract (7.7 Upgrades), meaning it is not upgradeable. This eliminates risks associated with upgradeability patterns, such as proxy initialization… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 87.2% |
| **Top-3 Unlocked** | ⚠️ 95.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.3% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0x3b66…2d8a — holds 87.2% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 27.0% of supply. Of that, 4.9% burned, 7.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.0% in wallets, 8.5% in other contracts. 2,014 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,014 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $200K (DexScreener, all pools). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $200K of DEX liquidity across 1 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb1b7...6666`](https://bscscan.com/address/0xb1b798c76a9f7bc6f5002dd72c23cf0d64b76666) |
| **Network** | BNB Chain |
| **Price** | $0.001337 |
| **24h Volume** | $1.44M |
| **Liquidity** | $200.1K |
| **Volume / Liquidity** | 7.2× |
| **Token Age** | 2d |
| **Top-10 Holders** | 27.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3770 buys / 2982 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6f0aa2c067ce5f6e5253d7f6487548fa01601b3b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cao-zhen-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
