---
token: Trump
ticker: TRUMP
network: bsc
risk_score: 82
status: high
date: 2026-10-21
---

# Trump (TRUMP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 82/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trump-bsc-0008)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee logic. Ownership has been renounced, meaning privileged functions are now dormant. However, critical vulnerabilities exist in the internal swap and liquidity management logic that could lead to loss of funds.

> **Final Recommendation:** The protocol should consider deploying a new version of the contract to address the critical and high-severity vulnerabilities identified in the liquidity management functions. The current contract is unsafe for use in automated liquidity pools due to the lack of return value checks and improper fund handling.

Users should be aware that the contract is immutable and no fixes can be applied to the current deployment. Any interaction with liquidity-related functions should be avoided until the underlying logic is corrected.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with additional fee-on-transfer logic. 7.1 Architecture is standard, but 7.2 Code Security is compromised by improper handling of external calls. 7.3… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are effectively neutralized by the renouncement of ownership. No further changes can be made to the fee structure or tokenomics. The protocol operates as a static… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to standard token transfers. The contract is immutable. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 96.5% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 3.5% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CD-01` — Unauthorized Token Withdrawal  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows for the arbitrary movement of tokens via transferFrom, potentially allowing unauthorized parties to drain tokens from addresses that have granted allowances.

**Recommendation:** Restrict the execution of swap and liquidity functions to internal contract logic only and remove the ability for arbitrary address selection.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without checking the boolean return value, which may fail silently and lead to inconsistent state.

**Recommendation:** Always check the return value of ERC-20 transfers or use SafeERC20 wrappers to ensure successful execution.


### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 2.8% of supply. Of that, 0.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.1% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 100.0%. A holder that also controls the contract can sell into its own liquidity. 11,696 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `CD-03` — Locked ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH via receive() and deposit functions but lacks any mechanism to withdraw or utilize these funds, effectively locking them permanently.

**Recommendation:** Implement a withdrawal function restricted to a secure address or ensure the contract does not accept ETH if it cannot be utilized.


### `CD-02` — Rounding Errors via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

Calculations in _executeSwapAndLiquify and _transfer perform division before multiplication, which causes precision loss and inaccurate fee calculations.

**Recommendation:** Reorder operations to perform multiplication before division to maintain precision.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

11,696 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

96.5% of the pool's LP is burned or time-locked. 96.4% is locked in PinkLock02 until 07 Nov 2026 (16 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 3.5% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (DexScreener, all pools). 24h trading volume $24.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.19% on sell. Market: $1.2M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd665...ecc0`](https://bscscan.com/address/0xd665e4ada3557d73a0508ea55d3c489a3c89ecc0) |
| **Network** | BNB Chain |
| **Price** | $33.1000 |
| **24h Volume** | $24.09M |
| **Liquidity** | $1.23M |
| **Volume / Liquidity** | 19.6× |
| **Token Age** | 23h |
| **Top-10 Holders** | 2.8% of supply |
| **Buy / Sell Tax** | 4.0% / 4.2% |
| **24h Transactions** | 5584 buys / 1143 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0c22417ef99aab313efbe441effe9f6c73d7b887)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trump-bsc-0008)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
