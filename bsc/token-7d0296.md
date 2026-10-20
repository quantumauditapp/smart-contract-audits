---
token: 超级社区
ticker: 超级社区
network: bsc
risk_score: 4
status: low
date: 2026-10-20
---

# 超级社区 (超级社区) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 4/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-7d0296-bsc)

---

## Audit Summary

SuperCommunity is an ERC-20 token implementation on the Binance Smart Chain featuring automated liquidity provision, marketing fee collection, and a dividend distribution system. The contract includes specialized logic for periodic pool burns and complex fee processing. Ownership of the contract has been renounced, which significantly reduces the risk profile by disabling all administrative functions and locking the protocol's parameters.

> **Final Recommendation:** Users should verify the current on-chain parameters for fees and thresholds, as these are now permanent following the renouncement of ownership. No further development actions are required, but monitoring the automated dividend distribution for gas efficiency is advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture (7.1) follows standard ERC-20 patterns with integrated DeFi features like automated liquidity. Code security (7.2) is generally high, though the complex fee processing logic in… |
| **Governance / Economics** | 10/10 | Low | Economic risks (7.4) are mitigated by the inability of any entity to change fees or limits post-renouncement. Governance (7.5) is static, as no administrative changes can be made to the protocol.… |
| **Upgrades** | 10/10 | Low | The contract is not upgradeable (7.7) and does not use a proxy pattern, ensuring the logic is immutable. The renouncement of ownership further guarantees that no state variables or administrative… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.7% (≈ permanent lock) |
| **LP Locked** | 99.7% — Null Address |

## Security Findings

_🟢 1 Low · ⚪ 9 Informational_

### `CD-01` — Rounding Error in Liquidity Logic  *(Severity: Low · Status: Unresolved)*

In the processLiquidityFee function, the contract performs division before multiplication when calculating the amount of BNB and tokens to add to the liquidity pool. This leads to minor precision loss and small amounts of dust remaining in the contract.

**Recommendation:** Update the mathematical operations to perform all multiplications before divisions to ensure maximum precision.


### `CP-05` — Dormant Fee Processing Toggle  *(Severity: Informational · Status: Unresolved)*

The processFees function utilizes a internal state flag to manage fee swaps during transfers. While this logic remains active, the administrative ability to manipulate the underlying parameters is disabled due to renounced ownership.

**Recommendation:** No action required as the contract is now immutable.


### `CP-07` — Fixed Transaction Fee Rates  *(Severity: Informational · Status: Unresolved)*

The functions setMarketingFee and processRewardFee allow for the configuration of transaction taxes. Because ownership is renounced, these fees are locked and cannot be increased by any party.

**Recommendation:** Users should confirm the current marketingFeeBps value on the blockchain.


### `CP-08` — Permanent Operational Thresholds  *(Severity: Informational · Status: Unresolved)*

Functions such as setThresholds and setGasParameters control the numeric limits for when fees are processed and how much gas is used. These are now permanent settings as the owner role is renounced.

**Recommendation:** Verify that the current dividendThreshold and swapThreshold are suitable for the token's volume.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 20.3% of supply. Of that, 1.3% burned, 5.5% locked, 10.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 1.5% in wallets, 1.2% in other contracts. 2,091 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,091 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.7% of the pool's LP is burned or time-locked. 99.7% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.3% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $85K (DexScreener, all pools). 24h trading volume $323K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2.5% on buy, 2.53% on sell. Market: $85K of DEX liquidity across 1 pools. Launch: 3 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xadf7...52fa`](https://bscscan.com/address/0xadf7bdb651c165d6743d2fc7fdba878f412f52fa) |
| **Network** | BNB Chain |
| **Price** | $134.6500 |
| **24h Volume** | $322.9K |
| **Liquidity** | $85.2K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 3d |
| **Top-10 Holders** | 20.3% of supply |
| **Buy / Sell Tax** | 2.5% / 2.5% |
| **24h Transactions** | 7053 buys / 1956 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xbb8134cfca77d6c7eb5b9402dc214657e006fc35)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-7d0296-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
