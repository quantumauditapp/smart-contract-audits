---
token: RISE Token
ticker: RISE
network: polygon
risk_score: 84
status: high
date: 2026-10-20
---

# RISE Token (RISE) — Smart Contract Security Analysis | Polygon

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rise-token-poly)

---

## Audit Summary

The RISEToken contract implements a highly centralized architecture where the owner or privileged system addresses maintain extensive control over token balances, transfer logic, and liquidity management. While the code is functional and follows standard ERC-20 patterns, the presence of administrative functions that can move user funds or redirect core protocol logic introduces significant trust requirements and potential for abuse. Users should be aware that the protocol's behavior is subject to change by the contract owner.

> **Final Recommendation:** It is strongly recommended to implement a multi-signature wallet or a decentralized governance mechanism to control privileged functions, reducing the risk of single-point-of-failure attacks. Furthermore, the contract should be updated to include proper return value checks for all ERC-20 transfers and to remove functions that allow direct manipulation of user balances.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract architecture relies on heavy centralization, with multiple administrative functions capable of modifying internal state and external dependencies. 7.1 Architecture is modular but tightly… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are entirely controlled by the owner. The ability to update routers and storage contracts allows for arbitrary changes to the token's economic model. 7.6… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are handled via address-swapping patterns rather than standard proxy patterns. While this allows for logic updates, it lacks transparency and immutability. 7.8 Operations are… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 76.6% |
| **LP Locked** | 76.6% — Null Address |

## Security Findings

_🟠 4 High · 🟡 2 Medium · 🟢 2 Low_

### `CD-02` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _removeLiquidity function fails to check the return value of ERC-20 transfers, which may lead to silent failures in liquidity operations.

**Recommendation:** Always check the boolean return value of ERC-20 transfer calls or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Predictable randomness  *(Severity: High · Status: Unresolved)*

Randomness is derived from on-chain values that can be predicted or influenced. Functions: checkAndResetDailyPrice.

**Recommendation:** Review the flagged functions; the static analyser reported this as `weak-prng`.


### `CP-02` — Privileged Balance Manipulation  *(Severity: High · Status: Unresolved)*

The function externalRemoveLiquidity allows a privileged address to move or burn tokens directly from any user's balance, bypassing standard transfer logic.

**Recommendation:** Remove functions that allow direct modification of user balances by administrative accounts.


### `CP-03` — Centralized Dependency Control  *(Severity: High · Status: Unresolved)*

The owner can change the addresses of the GSC storage and the PancakeRouter, effectively allowing them to redirect all token transfer logic and liquidity interactions.

**Recommendation:** Implement a timelock for administrative changes to critical contract dependencies.


### `CP-05` — Transfer Path Switch  *(Severity: Medium · Status: Unresolved)*

The owner can control the BUY_OPEN_TIME, effectively enabling or disabling trading for all users at will.

**Recommendation:** Consider making trading status immutable after a set period or governed by a DAO.


### `CP-07` — Dynamic Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

The updateDailyPrice function allows the owner to change transfer fees, which directly impacts the economic cost of trading.

**Recommendation:** Set hard caps on fee adjustments to prevent excessive taxation of users.


### `CD-01` — Rounding Loss via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

The functions getBeijing8AmUTC and resetDailyPrice perform division before multiplication, leading to potential precision loss.

**Recommendation:** Perform all multiplications before divisions to maintain precision.


### `CP-08` — Mutable Wallet Limits  *(Severity: Low · Status: Unresolved)*

The owner can change buy limits for specific addresses, allowing for discriminatory access control.

**Recommendation:** Define limits in the contract code or via a transparent governance process.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcfb2...a777`](https://polygonscan.com/address/0xcfb287565201763743a77c556dca44a673d0a777) |
| **Network** | Polygon |
| **Price** | $0.0007012 |
| **24h Volume** | $42.4K |
| **Liquidity** | $1.17M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 6mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 187 buys / 724 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is RISE Token a scam?

Based on automated analysis, RISE Token scores 84/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is RISE Token safe to buy?

Our scanner flagged a risk score of 84/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has RISE Token been audited?

The contract is open-source and verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x55e4151499e9dba3a74cc4ba9c711f8bcc1ef565)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rise-token-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
