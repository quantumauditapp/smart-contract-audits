---
token: Trump
ticker: TRUMP
network: bsc
risk_score: 84
status: high
date: 2026-10-22
---

# Trump (TRUMP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trump-bsc-5dfa)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee logic. While ownership has been renounced, preventing further administrative changes, the contract contains critical logic flaws in its internal swap and liquidity management functions that could lead to unauthorized token movement and trapped funds.

> **Final Recommendation:** The contract should be considered high-risk due to the identified critical and high-severity vulnerabilities. Since ownership is renounced, the current code cannot be updated to fix these issues. Users should exercise extreme caution as the contract's internal liquidity management logic is fundamentally flawed.

It is recommended to migrate to a new, audited contract implementation that follows standard OpenZeppelin patterns for liquidity management and fee handling. The current contract should be deprecated to prevent further interaction with the faulty swap logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns but introduces custom logic for fee handling and liquidity management. 7.1 Architecture is standard, though 7.2 Code Security reveals significant… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are effectively static as the contract ownership is renounced. No further changes can be made to the fee structure or tokenomics via the setTrailblazers function. The… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. 7.8 Operations are limited to standard token transfers. The contract is immutable, which provides certainty but prevents patching the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 97.4% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 2.6% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows the contract to move tokens from any address that has previously approved the contract, potentially leading to unauthorized drainage of user funds.

**Recommendation:** Restrict the _executeSwapAndLiquify function to only interact with tokens owned by the contract itself, rather than arbitrary user addresses.


### `CD-04` — Ignored Transfer Results  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without checking the boolean return value, which can lead to silent failures and inconsistent contract state.

**Recommendation:** Always verify the return value of ERC-20 transfer calls or use the SafeERC20 library to handle transfers safely.


### `CD-03` — Trapped ETH Funds  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH via its receive function but lacks any mechanism to withdraw or utilize these funds, causing them to be permanently locked in the contract.

**Recommendation:** Implement a withdrawal function restricted to a secure address or ensure the contract does not accept ETH if it cannot be utilized.


### `CD-02` — Rounding Errors in Calculations  *(Severity: Low · Status: Unresolved)*

The contract performs division before multiplication in _executeSwapAndLiquify and _transfer, which leads to precision loss and potential inaccuracies in fee calculations.

**Recommendation:** Reorder mathematical operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.3% of supply. Of that, 90.0% burned, 0.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.1% in wallets, 0.0% in other contracts. 16,297 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

16,297 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

97.4% of the pool's LP is burned or time-locked. 97.4% is locked in PinkLock02 until 01 Nov 2026 (9 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 2.6% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $160K (DexScreener, all pools). 24h trading volume $4.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.03% on sell. Market: $160K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x239c...5fa4`](https://bscscan.com/address/0x239c4cfc21484afcec6194123d782fbf10725fa4) |
| **Network** | BNB Chain |
| **Price** | $2.7100 |
| **24h Volume** | $4.48M |
| **Liquidity** | $160.1K |
| **Volume / Liquidity** | 28.0× |
| **Token Age** | 6h |
| **Top-10 Holders** | 90.3% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 7428 buys / 1382 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa0fb1e1d9706e4c634691ff3b5e648588b1a3996)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trump-bsc-5dfa)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
