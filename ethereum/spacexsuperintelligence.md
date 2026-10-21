---
token: SpaceXSuperIntelligence
ticker: SXSI
network: ethereum
risk_score: 37
status: medium
date: 2026-10-21
---

# SpaceXSuperIntelligence (SXSI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacexsuperintelligence-eth)

---

## Audit Summary

The SXSI contract is a standard ERC-20 token implementation with additional administrative functions. Ownership has been renounced, rendering the privileged functions (removeLimits, recoverStuckEther, transferManualToken) permanently inaccessible. The codebase is simple and follows standard patterns, though a minor issue regarding tx.origin usage was identified.

> **Final Recommendation:** The contract is secure for standard usage given the renounced ownership. Users should be aware that the contract logic is immutable and no further administrative intervention is possible.

While the tx.origin usage is noted, it does not pose an immediate threat in the current context as the ownership is renounced and the function is read-only. No further action is required for the current deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 functionality with robust arithmetic operations using OpenZeppelin's SafeMath. 7.1 Architecture is straightforward, relying on standard inheritance. 7.2 Code… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance aspects are effectively static. Since ownership is renounced, no further changes to tokenomics or administrative parameters can occur. The protocol relies on the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, ensuring no future changes can be introduced to the contract behavior. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CD-01` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The contract uses tx.origin to determine logic within the balanceOf function. Relying on tx.origin is insecure because it refers to the original sender of the transaction, which can be manipulated if a user is tricked into interacting with a malicious contract that calls this token.

**Recommendation:** Replace tx.origin with msg.sender to ensure that the authorization or logic check is tied to the immediate caller, which is the standard and secure practice in Solidity.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $95K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 66.4% of supply. Of that, 51.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.9% in wallets, 0.0% in other contracts. 84 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

84 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x08d2...cb44`](https://etherscan.io/address/0x08d2439829470bdafe3fbcea97402a0242facb44) |
| **Network** | Ethereum |
| **Price** | $0.00000952 |
| **24h Volume** | $95.0K |
| **Liquidity** | $9.7K |
| **Volume / Liquidity** | 9.8× |
| **Token Age** | 6h |
| **Top-10 Holders** | 66.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 384 buys / 443 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x805a46c1c0071a900f92199471ee9d6f4cd558e0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacexsuperintelligence-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
