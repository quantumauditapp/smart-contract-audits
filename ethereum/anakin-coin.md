---
token: Anakin Coin
ticker: ANAKIN
network: ethereum
risk_score: 48
status: medium
date: 2026-11-03
---

# Anakin Coin (ANAKIN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anakin-coin-eth)

---

## Audit Summary

The ANAKIN token is a standard ERC-20 implementation. The audit identified critical issues regarding return value consistency and insecure authorization patterns that could lead to integration failures or unauthorized rule bypasses. 7.1 Architecture: Standard ERC-20. 7.2 Code Security: High risk due to return value mismatches. 7.3 Access Control: Medium risk due to tx.origin usage. 7.4 Economic: Low. 7.5 Governance: N/A. 7.6 External: Low. 7.7 Upgrades: N/A. 7.8 Operations: Low.

> **Final Recommendation:** Immediate remediation of the return value logic is required to ensure compatibility with standard DeFi protocols and aggregators. The use of tx.origin must be replaced with msg.sender to prevent potential cross-contract impersonation attacks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract follows standard ERC-20 patterns but fails to implement return values correctly in internal transfer logic. The use of tx.origin for authorization in the returnTx function introduces a… |
| **Governance / Economics** | 8/10 | Low | There are no complex economic mechanisms or governance structures present. The token operates as a simple utility asset. No inflationary or deflationary mechanics were identified. |
| **Upgrades** | 8/10 | Low | The contract is not upgradeable and does not utilize proxy patterns. The state is immutable post-deployment. No upgrade-related risks exist. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `CD-01` — Inconsistent Return Values in Transfer Functions  *(Severity: High · Status: Unresolved)*

The _transfer function and associated transfer/transferFrom methods fail to handle return values correctly, which can cause external protocols to incorrectly assume a transaction failed or succeeded.

**Recommendation:** Ensure all transfer functions strictly adhere to the ERC-20 specification by returning a boolean value that accurately reflects the success of the operation.


### `CD-02` — Insecure Authorization via tx.origin  *(Severity: Medium · Status: Unresolved)*

The returnTx function uses tx.origin to determine authorization. This is dangerous because a malicious contract can be used to trick the protocol into executing functions on behalf of the original user.

**Recommendation:** Replace all instances of tx.origin with msg.sender to ensure that only the direct caller is authorized to perform sensitive actions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 45.2% of supply. Of that, 4.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 7.1% in wallets, 33.4% in other contracts. 211 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

211 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $38K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x29da...a297`](https://etherscan.io/address/0x29dad11107e4d18d7e64bff8410ec4640398a297) |
| **Network** | Ethereum |
| **Price** | $0.00002281 |
| **24h Volume** | $37.6K |
| **Liquidity** | $12.1K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 20h |
| **Top-10 Holders** | 45.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 290 buys / 308 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x139b9492615fe9af4fb827da40760a77d7c5663af1f1124408bebe6b85d87a2c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anakin-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
