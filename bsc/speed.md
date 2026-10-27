---
token: 甲亢哥
ticker: SPEED
network: bsc
risk_score: 84
status: high
date: 2026-10-27
---

# 甲亢哥 (SPEED) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/speed-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee exclusion logic. Ownership has been renounced, rendering privileged functions dormant. However, critical flaws in the internal swap logic and handling of external token transfers pose significant risks to liquidity and asset safety.

> **Final Recommendation:** The protocol should consider deploying a new version of the contract that addresses the identified critical and high-severity vulnerabilities, specifically regarding the validation of external token transfers and the security of the swap mechanism. Given that ownership is renounced, the current contract cannot be modified, and users should be advised of the risks associated with the trapped ETH and potential transfer failures.

Future implementations should utilize OpenZeppelin's SafeERC20 library to handle token transfers and ensure that all external interactions are validated against their return values. Additionally, implementing a withdrawal function for trapped ETH would improve operational efficiency and prevent asset loss.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with additional fee-handling logic. 7.1 Architecture is modular, but 7.2 Code Security is compromised by improper handling of external calls. 7.6… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are currently mitigated by the renunciation of ownership. The contract no longer allows for administrative changes to fee structures or ownership transfers. The… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, ensuring that the current vulnerabilities cannot be patched via administrative updates. This provides… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 96.1% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 3.9% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Withdrawal Risk  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom in a way that could allow the contract to pull tokens from any address that has previously approved the contract, potentially leading to unauthorized asset drainage.

**Recommendation:** Restrict the source address in transferFrom to only the contract's own balance or ensure strict validation of the sender.


### `CD-04` — Ignored Token Transfer Results  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without checking the boolean return value, which may fail silently and lead to incorrect internal accounting.

**Recommendation:** Use the SafeERC20 library to wrap transfer calls and ensure that failures revert the transaction.


### `CD-03` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function allowing it to accept ETH, but it lacks any mechanism to withdraw or transfer these funds out, causing them to be permanently locked.

**Recommendation:** Implement an emergency withdrawal function to allow the recovery of accidentally sent ETH.


### `CD-02` — Rounding Errors via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

Calculations in _executeSwapAndLiquify and _transfer perform division before multiplication, which causes precision loss and potential inaccuracies in fee distribution.

**Recommendation:** Rearrange mathematical operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 3.1% of supply. Of that, 1.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.0% in wallets, 0.0% in other contracts. 12,817 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

12,817 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

96.1% of the pool's LP is burned or time-locked. 96.1% is locked in PinkLock02 until 13 Nov 2026 (16 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 3.9% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $770K (DexScreener, all pools). 24h trading volume $26.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.06% on sell. Market: $770K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdc13...6daf`](https://bscscan.com/address/0xdc1392cff00376e48f02c13125c289ede23e6daf) |
| **Network** | BNB Chain |
| **Price** | $3.7900 |
| **24h Volume** | $26.76M |
| **Liquidity** | $769.7K |
| **Volume / Liquidity** | 34.8× |
| **Token Age** | 19h |
| **Top-10 Holders** | 3.1% of supply |
| **Buy / Sell Tax** | 4.0% / 4.1% |
| **24h Transactions** | 5773 buys / 1019 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xdc22cd161a4db86bada0de3d6b1726b640380b00)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/speed-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
