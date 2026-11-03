---
token: moco
ticker: MOCO
network: bsc
risk_score: 38
status: medium
date: 2026-11-03
---

# moco (MOCO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/moco-bsc)

---

## Audit Summary

The GGGTOKEN contract is a standard ERC-20 token with additional fee-on-transfer, dividend distribution, and anti-bot mechanisms. The contract ownership has been renounced, effectively locking all administrative functions and preventing further modifications to the token's economic parameters or access control lists. The code is functionally stable, and the lack of active administrative control mitigates risks associated with centralized authority.

> **Final Recommendation:** Since ownership has been renounced, the contract is immutable and no further administrative actions are possible. Users should be aware that the current fee structure, dividend distribution logic, and transfer limits are permanent and cannot be adjusted by any party.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a standard ERC-20 implementation with integrated dividend tracking and fee-on-transfer logic. 7.1 Architecture is modular, separating dividend tracking from the main token… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic parameters are fixed due to the renounced ownership. 7.5 Governance is non-existent as the owner role has been permanently removed. The token's economic model is immutable, preventing… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported by this contract. The implementation is fixed and cannot be modified or replaced. 7.8 Operations are limited to standard token transfers and dividend claims. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 9 Informational_

### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $232K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `CP-03` — Immutable Market Address Dependency  *(Severity: Informational · Status: Unresolved)*

The contract relies on an external market address for fee routing. While this address was configurable via setMarketAddr, the renounced ownership means this dependency is now permanently fixed.

**Recommendation:** No action required as the contract is immutable.


### `CP-06` — Permanent Anti-Bot/Blacklist State  *(Severity: Informational · Status: Unresolved)*

The contract contains a blacklist mechanism (setAddressFlag) that can restrict specific addresses from transferring tokens. Because ownership is renounced, the current blacklist state is permanent.

**Recommendation:** No action required; ensure the current blacklist is acceptable for long-term operation.


### `CP-07` — Fixed Transfer Fee Configuration  *(Severity: Informational · Status: Unresolved)*

The gas consumption and fee processing logic (updateGasForProcessing) are now locked. The current fee settings cannot be adjusted to account for network gas price fluctuations.

**Recommendation:** No action required.


### `CP-08` — Immutable Transaction and Wallet Limits  *(Severity: Informational · Status: Unresolved)*

Numeric limits such as max transaction size and wallet holdings (setLaunchTime, setInviterFee) are permanently set. These cannot be updated to reflect changing market conditions.

**Recommendation:** No action required.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 21.6% of supply. Of that, 11.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 7.7% in wallets, 2.2% in other contracts. 14,937 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

14,937 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $9K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x10b3...cc2a`](https://bscscan.com/address/0x10b389eed857fdb84089a64188aab6afbbe2cc2a) |
| **Network** | BNB Chain |
| **Price** | $0. |
| **24h Volume** | $232.3K |
| **Liquidity** | $9.4K |
| **Volume / Liquidity** | 24.7× |
| **Token Age** | 10h |
| **Top-10 Holders** | 21.6% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 3711 buys / 3578 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xc3fa8d53a3312f1eb9ea48a9515c3ad4852434b7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/moco-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
