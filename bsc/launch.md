---
token: Launch
ticker: LAUNCH
network: bsc
risk_score: 83
status: high
date: 2026-10-27
---

# Launch (LAUNCH) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 83/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/launch-bsc)

---

## Audit Summary

The contract implements a standard ERC-20 token with custom fee exclusion logic. Ownership has been renounced, meaning privileged functions are now permanently disabled. However, critical logic flaws in the internal swap mechanism and handling of ETH pose significant risks to users and contract integrity.

> **Final Recommendation:** The contract should be considered high-risk due to the inability to recover trapped ETH and the presence of critical flaws in the internal swap logic. Users should exercise extreme caution as the contract cannot be patched or updated to fix these issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract architecture follows standard ERC-20 patterns with added fee exclusion capabilities. 7.1 Architecture is standard, 7.2 Code Security is compromised by unchecked return values, and 7.3… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are effectively static as ownership is renounced. No further changes to fee exclusions or ownership can be made by the deployer. The economic model relies on the… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to standard ERC-20 transfers. The contract is immutable by design due to the renounced ownership. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 98.0% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 1.5% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Withdrawal Risk  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom in a way that could allow the contract to pull tokens from any user who has previously approved the contract, potentially draining user balances.

**Recommendation:** Restrict the scope of transferFrom calls to only interact with authorized liquidity pools or specific contract-owned addresses.


### `CD-04` — Unchecked Token Transfer Results  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function ignores the boolean return value of ERC-20 transfer calls, which may lead to silent failures where tokens are not moved but the contract state updates as if they were.

**Recommendation:** Always check the return value of transfer and transferFrom calls or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but there is no logic implemented to withdraw or utilize these funds, causing them to be permanently locked.

**Recommendation:** Implement a withdrawal function restricted to a multi-sig or DAO, or remove the receive function if ETH handling is not required.


### `CD-02` — Rounding Errors via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

In _executeSwapAndLiquify and _transfer, division is performed before multiplication, which leads to precision loss and potential inaccuracies in fee calculations.

**Recommendation:** Perform all multiplications before divisions to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 75.8% of supply. Of that, 75.0% burned, 0.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 0.3% in other contracts. 18,826 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

18,826 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

98.0% of the pool's LP is burned or time-locked. 98.0% is locked in PinkLock02 until 17 Nov 2026 (20 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 2.0% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $339K (DexScreener, all pools). 24h trading volume $8.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3.9% on buy, 4% on sell. Market: $339K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x08ba...215f`](https://bscscan.com/address/0x08ba863a46f20ff68fd0f54a2603563d21af215f) |
| **Network** | BNB Chain |
| **Price** | $0.03435 |
| **24h Volume** | $7.96M |
| **Liquidity** | $339.0K |
| **Volume / Liquidity** | 23.5× |
| **Token Age** | 8h |
| **Top-10 Holders** | 75.8% of supply |
| **Buy / Sell Tax** | 3.9% / 4.0% |
| **24h Transactions** | 6889 buys / 2342 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc3c5979c5eb9920473adccd0e0829e97b1efc4ff)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/launch-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
