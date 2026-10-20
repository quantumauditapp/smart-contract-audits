---
token: SPA
ticker: SPA
network: bsc
risk_score: 77
status: high
date: 2026-10-11
---

# SPA (SPA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 77/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spa-bsc)

---

## Audit Summary

This report details the security audit of the SPA token contract. The contract implements standard ERC-20 functionality, with its ownership having been renounced. Several technical issues were identified, including unchecked external token transfers and the inability to withdraw received Ether.

> **Final Recommendation:** Token holders should be aware that the contract's logic is immutable due to renounced ownership and the absence of upgrade mechanisms. It is crucial to understand that any ETH sent to the contract will be permanently locked, and the `distributeDividend` function may not reliably transfer tokens if the underlying ERC-20 `transfer` call fails. Users should exercise caution when interacting with functions that involve external token transfers or sending ETH directly to the contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The `spa` token implements standard ERC-20 functionality, allowing transfers and approvals. However, a critical issue exists where the `distributeDividend` function does not check the return value of… |
| **Governance / Economics** | 6/10 | Medium | The contract's ownership has been renounced on-chain, meaning no single entity can currently control the contract's privileged functions (7.3 Access Control). Functions like `setLPFeefenhong`… |
| **Upgrades** | 6/10 | Medium | The `spa` contract is a standard token implementation and does not utilize any proxy patterns or upgrade mechanisms (7.1 Architecture). This means the contract's logic is immutable once deployed and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 25.9% — PinkLock02 |
| **Top-1 Unlocked Holder** | 39.8% |
| **Top-3 Unlocked** | 56.1% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 5 Informational_

### `CD-02` — Token Transfer Result Not Checked in `distributeDividend`  *(Severity: High · Status: Unresolved)*

The `distributeDividend` function performs external ERC-20 token transfers. However, it does not check the boolean return value of these `transfer` calls. If an external token's `transfer` function fails (e.g., due to reentrancy guards, insufficient balance, or other custom logic), the `distributeDividend` function will proceed as if the transfer was successful, potentially leading to incorrect accounting or a failure to distribute dividends as intended without any error indication.

**Recommendation:** Developers should ensure that all external ERC-20 `transfer` calls are checked for their return value to confirm successful execution. If the return value is `false`, the transaction should revert or handle the failure appropriately.


### `CD-01` — Ether Sent to Contract Cannot Be Withdrawn  *(Severity: Medium · Status: Unresolved)*

The contract has a `receive` function, allowing it to accept Ether (ETH). However, there are no corresponding functions (like `withdrawETH`) that would permit anyone, including the original deployer or any other address, to send this received ETH out of the contract. Any ETH sent to this contract will be permanently locked and inaccessible.

**Recommendation:** Token holders should be advised not to send Ether directly to this contract, as it will be irretrievably lost.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

25.9% of the pool's LP is burned or time-locked. 25.9% is locked in PinkLock02 until 01 Oct 2123 (35418 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 60.7% is held, unlocked, by 9 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-07` — Privileged Addresses Could Change Transfer Fees (Now Dormant)  *(Severity: Informational · Status: Unresolved)*

The `setLPFeefenhong` and `setdistributorGas` functions were designed to allow the contract owner to change the fees applied to token transfers. However, the contract's ownership has been renounced, meaning no one can currently call these functions.

**Recommendation:** No action is required as ownership is renounced, rendering these functions inactive. This is noted for historical context regarding the contract's design.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 58.9% of supply. Of that, 48.8% burned, 0.5% locked, 4.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.2% in wallets, 0.6% in other contracts. 35,814 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

35,814 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $803K (DexScreener, all pools). 24h trading volume $2.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 4% on sell. Market: $803K of DEX liquidity across 2 pools. Launch: 710 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe26a...f22e`](https://bscscan.com/address/0xe26a492ced210bd84e11147e8aec84b23390f22e) |
| **Network** | BNB Chain |
| **Price** | $7.9600 |
| **24h Volume** | $2.68M |
| **Liquidity** | $794.9K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 58.9% of supply |
| **Buy / Sell Tax** | 2.0% / 4.0% |
| **24h Transactions** | 8215 buys / 10214 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x645b56bdd12ea9cbcfd08d187f06fb81029ce854)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spa-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
