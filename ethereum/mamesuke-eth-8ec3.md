---
token: MAMESUKE
ticker: MAMESUKE
network: ethereum
risk_score: 29
status: low
date: 2026-11-04
---

# MAMESUKE (MAMESUKE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mamesuke-eth-8ec3)

---

## Audit Summary

The protocol implements a standard ERC-20 token contract. The architecture follows OpenZeppelin standards, ensuring basic compatibility with DeFi ecosystems. However, a critical logic flaw exists in the transfer mechanism that violates the ERC-20 specification regarding return values, which may cause integration failures with automated systems.

> **Final Recommendation:** The primary recommendation is to update the transfer logic to ensure full compliance with the ERC-20 standard. Specifically, ensure that all transfer functions correctly handle and return boolean values as expected by external smart contracts and decentralized exchanges.

Additionally, perform thorough integration testing with common DeFi routers to ensure that the current implementation does not cause transaction reverts in automated liquidity pools.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes standard OpenZeppelin libraries for core ERC-20 functionality. 7.1 Architecture is modular and follows established patterns. 7.2 Code Security is hampered by a non-compliant… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance aspects are not applicable as the contract is a simple, non-upgradable token without minting or burning capabilities. The supply is fixed at deployment. There are no… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward with no administrative overhead. The contract is immutable by design. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `CD-01` — Non-Compliant ERC-20 Return Values  *(Severity: High · Status: Unresolved)*

The transfer and transferFrom functions do not correctly handle return values in accordance with the ERC-20 standard. This can cause external contracts that rely on the boolean return value to fail or revert when interacting with this token.

**Recommendation:** Modify the _transfer logic and ensure that the transfer and transferFrom functions explicitly return the boolean success status as required by the ERC-20 specification.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 24.0% of supply. Of that, 5.5% burned — not holders that can sell, so excluded from the concentration score. What remains: 10.1% in wallets, 8.4% in other contracts. 399 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

399 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $57K (DexScreener, all pools). 24h trading volume $138K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $57K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa6b6...05d2`](https://etherscan.io/address/0xa6b6969a27e99bde132af3eb9777b9b8313f05d2) |
| **Network** | Ethereum |
| **Price** | $0.0003639 |
| **24h Volume** | $138.4K |
| **Liquidity** | $57.1K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 1d |
| **Top-10 Holders** | 24.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 450 buys / 423 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x0bd68c8a7a1b84a9c49426ed9188eb8987280a273c4f4d2333725153dea614e3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mamesuke-eth-8ec3)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
