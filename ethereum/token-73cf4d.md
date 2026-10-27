---
token: ███
ticker: ███
network: ethereum
risk_score: 38
status: medium
date: 2026-10-27
---

# ███ (███) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-73cf4d-eth)

---

## Audit Summary

The Blind token is a standard ERC-20 implementation with additional administrative functions for managing transaction limits and fund recovery. Ownership has been renounced, effectively disabling all privileged administrative functions. The codebase is simple and follows standard patterns, though one medium-severity finding regarding authorization logic was identified.

> **Final Recommendation:** Given that ownership has been renounced, the contract is in a permanent state. No further action is required for the current deployment. Future iterations should avoid using tx.origin for authorization logic to prevent potential phishing or contract-based manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 functionality with robust arithmetic operations using SafeMath. 7.1 Architecture is straightforward, relying on standard inheritance. 7.2 Code Security is… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance risks are currently mitigated by the renouncement of ownership. Since the owner can no longer call privileged functions, the protocol is effectively immutable. No… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as this is a standard non-proxy contract. 7.8 Operations are stable due to the renounced ownership status. The contract state is fixed and cannot be modified via… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CD-01` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The contract utilizes tx.origin to determine authorization or rules within the balanceOf function. This is a security risk because an attacker can trick a user into interacting with a malicious contract that then calls the Blind token, potentially bypassing intended security checks.

**Recommendation:** Replace all instances of tx.origin with msg.sender to ensure that the immediate caller is the one being authorized, which is the standard and secure practice for EVM smart contracts.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $8K (DexScreener, all pools). 24h trading volume $46K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 69.6% of supply. Of that, 56.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 13.4% in wallets, 0.0% in other contracts. 186 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

186 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $8K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xeea3...73bd`](https://etherscan.io/address/0xeea344e75363a370ddf71a6d00600bd42dc473bd) |
| **Network** | Ethereum |
| **Price** | $0.00000746 |
| **24h Volume** | $45.6K |
| **Liquidity** | $8.4K |
| **Volume / Liquidity** | 5.4× |
| **Token Age** | 10h |
| **Top-10 Holders** | 69.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 264 buys / 371 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xd2ef8a056de5fa1e89208f600f7ecd4414036dbc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-73cf4d-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
