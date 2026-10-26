---
token: Anthropic
ticker: ANT
network: ethereum
risk_score: 44
status: medium
date: 2026-10-26
---

# Anthropic (ANT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-eth)

---

## Audit Summary

The Token contract is a standard ERC-20 implementation with ownership renounced, meaning privileged functions are now dormant. The architecture is simple, but the code contains critical logic errors regarding return values and potential rounding issues. While the renounced ownership prevents further administrative interference, the existing code flaws impact standard token functionality.

> **Final Recommendation:** The contract should be treated with caution due to the identified logic errors in transfer functions. Since ownership is renounced, the contract cannot be patched or updated; users should verify compatibility with any dApps or exchanges before interacting, as the incorrect return values may cause transaction failures in automated systems.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 logic with 7.1 Architecture and 7.2 Code Security being the primary focus. 7.3 Access Control is effectively disabled due to ownership renouncement. 7.6… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance risks are minimal as ownership has been renounced. No further changes can be made to the contract parameters or economic logic. The token operates as a fixed-supply… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable due to the immutable nature of the renounced contract. No upgrade path exists for the current deployment. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — TeamFinance |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 6 Informational_

### `CD-02` — Incorrect return values in transfer functions  *(Severity: High · Status: Unresolved)*

Functions like transfer and transferFrom do not correctly handle or return the expected boolean values required by the ERC-20 standard, which can cause failures in smart contract integrations.

**Recommendation:** Ensure all transfer functions strictly adhere to the ERC-20 specification by returning the correct boolean status.


### `CD-01` — Rounding loss in division  *(Severity: Low · Status: Unresolved)*

The enableTrading function performs division before multiplication, which can lead to precision loss and unexpected token amounts during calculations.

**Recommendation:** Always perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 0.0% in wallets, 100.0% in other contracts. 1 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked, lock term not visible  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is held by TeamFinance, but the lock's end date is not published in the data we can read — its duration is unverified. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $66K (DexScreener, all pools). 24h trading volume $82K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $66K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd85d...f1f0`](https://etherscan.io/address/0xd85db1599a0ff426e74129139ef936f022a1f1f0) |
| **Network** | Ethereum |
| **Price** | $0.0005037 |
| **24h Volume** | $81.9K |
| **Liquidity** | $66.0K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 4h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 417 buys / 78 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x10a003d1ef403d654f2894fcd358cc389309b27a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
