---
token: You Missed Bitches
ticker: YMB
network: ethereum
risk_score: 31
status: low
date: 2026-10-24
---

# You Missed Bitches (YMB) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 31/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/you-missed-bitches-eth-b9ca)

---

## Audit Summary

The YMB token is a standard ERC-20 implementation with additional tax and trading restriction features. Ownership has been successfully renounced, effectively locking the administrative functions that previously allowed for fee adjustments, blacklisting, and trading control. The code is functional and follows standard patterns for tokens with transfer-based taxation.

> **Final Recommendation:** The contract is currently in a safe, immutable state due to the renounced ownership. Users should note that the token logic includes transfer taxes and potential blacklisting, which are now permanently set to their current values. No further action is required as the administrative surface is fully disabled.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements standard ERC-20 logic with custom transfer hooks for taxation. 7.1 Architecture is straightforward, utilizing a single-contract design. 7.2 Code Security shows minor issues… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance risks are currently non-existent as the contract is immutable. 7.6 External dependencies are limited to the Uniswap V2 router for liquidity management. Since ownership… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable because the contract logic is fixed. No upgrade paths exist, ensuring the current logic remains permanent. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 9 Informational_

### `CD-02` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The contract uses tx.origin in the transfer path, which can be vulnerable to phishing attacks if the contract were to interact with malicious external contracts.

**Recommendation:** Replace tx.origin with msg.sender where possible to ensure secure authorization.


### `CD-01` — Rounding Precision Loss  *(Severity: Low · Status: Unresolved)*

The _transfer function performs division before multiplication, which can lead to minor rounding errors in fee calculations.

**Recommendation:** Reorder arithmetic operations to perform multiplication before division to maintain precision.


### `CP-05` — Disabled Administrative Controls  *(Severity: Informational · Status: Unresolved)*

Functions like enableTrading and removeLimits allow for the modification of transfer rules. Because ownership is renounced, these functions are now inaccessible, preventing any further changes to trading status.

**Recommendation:** No action required; the renouncement ensures these functions cannot be abused.


### `CP-07` — Immutable Transfer Fees  *(Severity: Informational · Status: Unresolved)*

The contract includes functions to update buy and sell fees. These are now permanently locked due to the renouncement of ownership.

**Recommendation:** None; the current fee structure is immutable.


### `CP-08` — Immutable Transaction Limits  *(Severity: Informational · Status: Unresolved)*

Functions controlling max transaction and wallet amounts are now inaccessible, locking the current limits in place.

**Recommendation:** None; the current limits are immutable.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 38.3% of supply. Of that, 27.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.0% in wallets, 1.0% in other contracts. 203 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

203 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $38K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfee1...01e7`](https://etherscan.io/address/0xfee12b6856474a44d871aacb9f934a6d07e301e7) |
| **Network** | Ethereum |
| **Price** | $0.00003318 |
| **24h Volume** | $38.2K |
| **Liquidity** | $18.0K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 8h |
| **Top-10 Holders** | 38.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 326 buys / 290 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x3e8d34fbed949dcd0bf682567e08ab57a4e7f7ec)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/you-missed-bitches-eth-b9ca)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
