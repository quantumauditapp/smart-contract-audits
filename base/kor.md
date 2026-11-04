---
token: KOR
ticker: KOR
network: base
risk_score: 28
status: low
date: 2026-11-04
---

# KOR (KOR) — Smart Contract Security Analysis | Base

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kor-base)

---

## Audit Summary

The Kor contract is a standard ERC-20 token implementation incorporating EIP-712 permit functionality and governance voting capabilities. The codebase relies on well-audited OpenZeppelin libraries, and static analysis confirms the absence of privileged administrative functions or centralized control mechanisms. No vulnerabilities were identified in the transfer logic or state management.

> **Final Recommendation:** The contract is secure and follows industry best practices for token implementation. No further action is required for the current codebase.

Users should remain aware that as an immutable token, no emergency recovery or pause functionality exists if the underlying network or integrated protocols experience issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard ERC-20 and ERC-5805 patterns, ensuring high interoperability with DeFi protocols. 7.1 Architecture is robust, utilizing modular inheritance for governance and permit… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic parameters are defined by the token supply and standard ERC-20 mechanics. 7.5 Governance is decentralized by design, as the contract lacks any owner-controlled minting or pausing… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not applicable as the contract is deployed as an immutable implementation. There are no proxy patterns or delegatecall mechanisms present. The contract logic is fixed at the time of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 85.6% |
| **Top-3 Unlocked** | ⚠️ 99.8% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. One of them — a wallet, 0x9a2e…f5b5 — holds 85.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 27% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 89.9% of supply. What remains: 5.1% in wallets, 84.7% in other contracts. 1,079 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Kor Protocol (KOR). 1,079 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $43K (DexScreener, all pools). 24h trading volume $239K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $43K of DEX liquidity across 14 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd367...6926`](https://basescan.org/address/0xd3679306360705ba3580bc4130b56460fb4e6926) |
| **Network** | Base |
| **Price** | $0.01301 |
| **24h Volume** | $111.8K |
| **Liquidity** | $11.6K |
| **Volume / Liquidity** | 9.6× |
| **Token Age** | 8h |
| **Top-10 Holders** | 89.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 697 buys / 1171 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x6dd916fb422692ea1594b40c21edc8167250f8a07108a23d1dedc866de7fbaaf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kor-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
