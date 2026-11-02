---
token: Peace Coin
ticker: PEACE
network: ethereum
risk_score: 48
status: medium
date: 2026-11-02
---

# Peace Coin (PEACE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/peace-coin-eth)

---

## Audit Summary

The PEACE token is a standard ERC-20 implementation. The audit identified critical issues regarding return value consistency and insecure authorization patterns. The contract lacks administrative control functions, which limits centralization risk but prevents emergency intervention.

> **Final Recommendation:** The development team should immediately refactor the return values in the transfer functions to ensure compatibility with standard ERC-20 interfaces. Additionally, replace all instances of tx.origin with msg.sender to prevent unauthorized access via intermediary contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard ERC-20 patterns with 7.1 Architecture and 7.2 Code Security being generally compliant. However, 7.3 Access Control is flawed due to the use of tx.origin in the… |
| **Governance / Economics** | 8/10 | Low | The contract has no 7.5 Governance mechanisms or 7.4 Economic parameters. 7.8 Operations are fully decentralized as there are no privileged roles. This eliminates rug-pull risks via administrative… |
| **Upgrades** | 8/10 | Low | The contract is not upgradeable (7.7 Upgrades). It is a standard immutable deployment. No proxy patterns are utilized. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `CD-01` — Incorrect Return Values in Transfer Functions  *(Severity: High · Status: Unresolved)*

The _transfer, transfer, and transferFrom functions do not correctly handle return values according to the ERC-20 specification, which can cause integration failures with external DeFi protocols.

**Recommendation:** Ensure all transfer functions return a boolean true value upon successful execution as required by the ERC-20 standard.


### `CD-02` — Insecure Authorization using tx.origin  *(Severity: Medium · Status: Unresolved)*

The returnTx function uses tx.origin for authorization, which allows malicious smart contracts to bypass security checks by acting as an intermediary.

**Recommendation:** Replace tx.origin with msg.sender to ensure that only the direct caller is authorized to execute sensitive functions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 26.1% of supply. What remains: 9.5% in wallets, 16.6% in other contracts. 335 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

335 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $146K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe274...5a50`](https://etherscan.io/address/0xe274df8f2d0b7af808ec97a50c835d6c99245a50) |
| **Network** | Ethereum |
| **Price** | $0.00004369 |
| **24h Volume** | $146.0K |
| **Liquidity** | $17.6K |
| **Volume / Liquidity** | 8.3× |
| **Token Age** | 8h |
| **Top-10 Holders** | 26.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 483 buys / 358 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x21b93cf46c36ed4bc3817aa8a6f69ef2338c77743fc5f7b239375699f7679d8a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/peace-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
