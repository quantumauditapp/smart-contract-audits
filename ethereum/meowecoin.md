---
token: Meowecoin
ticker: MEOWE
network: ethereum
risk_score: 25
status: low
date: 2026-10-23
---

# Meowecoin (MEOWE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meowecoin-eth)

---

## Audit Summary

The Meowe token is a standard ERC-20 implementation with additional administrative functions. Ownership has been renounced on-chain, rendering all privileged functions (such as limit removal and fund recovery) permanently inaccessible. The protocol is currently immutable and operates as a trustless asset.

> **Final Recommendation:** The contract is currently in a secure, immutable state due to the renouncement of ownership. No further action is required for the current deployment as the privileged functions are effectively disabled. Users should verify the renouncement status on-chain before interacting with the contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes standard OpenZeppelin-style patterns for ERC-20 compliance. 7.1 Architecture is straightforward, relying on internal transfer logic. 7.2 Code Security is generally robust… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance risks are minimal as the contract is immutable. No further changes can be made to the tokenomics or administrative parameters. The renouncement ensures that no central… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported by the contract architecture. The contract is a standard implementation without proxy patterns. 7.8 Operations are stable as the contract state is locked. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CD-01` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The contract uses tx.origin to determine logic within the balanceOf function. This is a security risk because an intermediate contract can be used to trick the system into identifying the wrong user as the initiator of a transaction.

**Recommendation:** Replace all instances of tx.origin with msg.sender to ensure that the immediate caller is the one being authenticated, which is the standard practice for secure smart contract development.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 44.7% of supply. Of that, 35.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.6% in wallets, 0.0% in other contracts. 203 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

203 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $65K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x63b2...f7f5`](https://etherscan.io/address/0x63b218ca3f5049f670ae7a9466bd2ea8d3f9f7f5) |
| **Network** | Ethereum |
| **Price** | $0.00001248 |
| **24h Volume** | $65.5K |
| **Liquidity** | $11.0K |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 4h |
| **Top-10 Holders** | 44.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 373 buys / 362 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x91e0e2b743075c1eec7c3d90380927307ee6b32f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meowecoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
