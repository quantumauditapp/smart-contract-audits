---
token: SAFU Fund
ticker: SAFU
network: bsc
risk_score: 83
status: high
date: 2026-11-01
---

# SAFU Fund (SAFU) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 83/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/safu-fund-bsc-7240)

---

## Audit Summary

The contract is a standard ERC-20 token with additional fee-on-transfer logic. Ownership has been renounced, meaning the privileged functions for fee management are now permanently disabled. The audit identified critical issues regarding token transfer safety and fund accessibility.

> **Final Recommendation:** The contract should be redeployed with corrected logic for handling external token transfers and proper ETH withdrawal mechanisms. The current implementation poses a high risk of fund loss due to the lack of return value checks and the inability to recover trapped ETH.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with integrated fee-on-transfer mechanics. 7.1 Architecture: The contract uses a standard inheritance model. 7.2 Code Security: The implementation… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic: The contract implements a fee-on-transfer mechanism. 7.5 Governance: Ownership is renounced, meaning no further governance changes are possible. 7.6 External: The contract interacts… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The contract is not upgradeable and uses no proxy patterns. 7.8 Operations: Operational control is permanently disabled due to the renounced ownership status. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 96.6% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 3.4% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Withdrawal  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows the contract to move tokens from any address that has granted an allowance to the contract, potentially leading to unauthorized drainage of user funds.

**Recommendation:** Restrict the scope of the swap function to only interact with tokens owned by the contract itself.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without verifying the boolean return value, which can lead to silent failures in liquidity operations.

**Recommendation:** Always check the return value of ERC-20 transfers or use the SafeERC20 library.


### `CD-03` — Trapped ETH Balance  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but there is no mechanism to withdraw or utilize these funds, causing them to be permanently locked.

**Recommendation:** Implement an emergency withdrawal function to allow the recovery of accidentally sent ETH.


### `CD-02` — Arithmetic Precision Loss  *(Severity: Low · Status: Unresolved)*

The contract performs division before multiplication in fee calculations within _executeSwapAndLiquify and _transfer, leading to rounding errors.

**Recommendation:** Rearrange arithmetic operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.4% of supply. Of that, 90.0% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.1% in wallets, 0.0% in other contracts. 17,173 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

17,173 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

96.6% of the pool's LP is burned or time-locked. 96.6% is locked in PinkLock02 until 11 Nov 2026 (9 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 3.4% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $133K (DexScreener, all pools). 24h trading volume $6.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.03% on sell. Market: $133K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8887...acef`](https://bscscan.com/address/0x888781c1071d432b7778fd07a6ad8225fa99acef) |
| **Network** | BNB Chain |
| **Price** | $0.01782 |
| **24h Volume** | $6.20M |
| **Liquidity** | $133.5K |
| **Volume / Liquidity** | 46.5× |
| **Token Age** | 5h |
| **Top-10 Holders** | 90.4% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 7208 buys / 1182 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0cc18cfc0509c21c1dba636587d056d8a2d9f3ff)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/safu-fund-bsc-7240)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
