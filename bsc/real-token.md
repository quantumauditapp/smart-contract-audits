---
token: Real Token
ticker: RT
network: bsc
risk_score: 54
status: medium
date: 2026-11-01
---

# Real Token (RT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/real-token-bsc)

---

## Audit Summary

The RT contract is a standard ERC-20 token implementation utilizing OpenZeppelin libraries. It includes EIP-2612 permit functionality and burnable capabilities. No privileged roles or administrative backdoors were identified in the source code.

> **Final Recommendation:** The contract is secure and follows industry best practices for standard tokens. No further action is required for the current implementation.

Ensure that any future integrations or extensions maintain the current permissionless nature of the contract to avoid introducing centralized points of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard OpenZeppelin ERC-20 patterns (7.1 Architecture). Code security is robust due to the use of audited, battle-tested libraries (7.2 Code Security). Access control is… |
| **Governance / Economics** | 2/10 | High | There are no governance mechanisms or economic parameters defined within the contract (7.4 Economic, 7.5 Governance). The token supply is fixed upon deployment or managed via standard mint/burn… |
| **Upgrades** | 8/10 | Low | The contract is not upgradeable (7.7 Upgrades). It is a standard immutable deployment. No proxy patterns are utilized. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x6cee…9d29 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 99.9% in wallets, 0.0% in other contracts. 11,734 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as RealGo (RT). 11,734 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23K (DexScreener, all pools). 24h trading volume $3.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $127K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 1 pools. Launch: 10 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 10 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 10 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd24b...a562`](https://bscscan.com/address/0xd24b79c0844f53866c34275a83b2313a4a90a562) |
| **Network** | BNB Chain |
| **Price** | $0.004431 |
| **24h Volume** | $126.7K |
| **Liquidity** | $23.2K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 10d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 990 buys / 849 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x86563565637e34d6f2a3e82de86721edf1d60c10)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/real-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
