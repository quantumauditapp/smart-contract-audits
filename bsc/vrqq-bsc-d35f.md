---
token: VRQQ
ticker: VRQQ
network: bsc
risk_score: 84
status: high
date: 2026-11-02
---

# VRQQ (VRQQ) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vrqq-bsc-d35f)

---

## Audit Summary

The contract is a standard ERC-20 token with additional fee-exclusion logic. Ownership has been renounced, meaning privileged functions are now dormant and cannot be modified. The protocol faces significant risks due to unhandled return values and locked ETH, though the core token transfer logic remains functional.

> **Final Recommendation:** The protocol should acknowledge the permanent loss of any ETH sent to the contract address, as there is no recovery mechanism. Given that ownership is renounced, no further administrative changes can be made to fix the identified logic flaws; users should exercise caution regarding the token's liquidity mechanisms.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with integrated fee-exclusion mechanisms. 7.1 Architecture and 7.2 Code Security are generally sound, though 7.6 External interactions are flawed.… |
| **Governance / Economics** | 6/10 | Medium | 7.5 Governance is effectively neutralized as ownership has been renounced. 7.4 Economic parameters are fixed, preventing further manipulation of fee structures. The lack of an exit strategy for… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, ensuring consistency but preventing future security patches. 7.8 Operations are limited to standard token… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 98.2% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 1.4% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom to move tokens from arbitrary addresses, potentially allowing the contract to drain funds from users who have approved the contract.

**Recommendation:** Restrict the source of tokens in transferFrom to only the contract's own balance or authorized liquidity pools.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without checking the boolean return value, which may lead to silent failures in liquidity operations.

**Recommendation:** Always check the return value of ERC-20 transfers or use SafeERC20 wrappers.


### `CD-03` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but there are no functions implemented to withdraw or transfer this ETH out of the contract.

**Recommendation:** Implement an owner-restricted withdrawal function to recover accidentally sent ETH.


### `CD-02` — Arithmetic Precision Loss  *(Severity: Low · Status: Unresolved)*

The functions _executeSwapAndLiquify and _transfer perform division before multiplication, which can lead to rounding errors and loss of precision in fee calculations.

**Recommendation:** Perform all multiplications before divisions to maintain maximum precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.3% of supply. Of that, 95.2% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 0.0% in other contracts. 19,738 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

19,738 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

98.2% of the pool's LP is burned or time-locked. 98.2% is locked in PinkLock02 until 22 Nov 2026 (19 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 1.8% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $413K (DexScreener, all pools). 24h trading volume $7.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3.9% on buy, 3.97% on sell. Market: $413K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbcad...d20c`](https://bscscan.com/address/0xbcad3fd02604408cb6444b501dd830638121d20c) |
| **Network** | BNB Chain |
| **Price** | $0.00000009 |
| **24h Volume** | $7.68M |
| **Liquidity** | $413.0K |
| **Volume / Liquidity** | 18.6× |
| **Token Age** | 8h |
| **Top-10 Holders** | 95.3% of supply |
| **Buy / Sell Tax** | 3.9% / 4.0% |
| **24h Transactions** | 7833 buys / 1594 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x5b4a489f46f8242ddecc8a26b8db21702cbbaa05)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vrqq-bsc-d35f)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
