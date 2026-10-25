---
token: DeepSeek
ticker: DEEPSEEK
network: bsc
risk_score: 81
status: high
date: 2026-10-25
---

# DeepSeek (DEEPSEEK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/deepseek-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee logic. Ownership has been renounced, meaning privileged functions like setExclusionFromFee are now permanently disabled. The contract contains critical logic flaws regarding token transfers and ETH handling that pose significant risks to users and locked funds.

> **Final Recommendation:** The contract should be considered high-risk due to the inability to recover trapped ETH and the presence of critical logic errors in the swap mechanism. Users should exercise extreme caution as the contract cannot be patched or upgraded to fix these issues.

Future deployments should implement robust return value checking for all external calls and ensure that any contract capable of receiving ETH includes a mechanism for authorized withdrawal or distribution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns but introduces flawed internal swap logic. 7.1 Architecture is standard, 7.2 Code Security is compromised by unchecked return values, and 7.3 Access… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are currently static as ownership is renounced. No further changes to fee exclusions or ownership are possible. The economic model is fixed, preventing any future… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to standard token transfers. The contract is immutable. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 97.0% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 3.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom to move tokens from arbitrary addresses, potentially allowing unauthorized depletion of user balances if the spender allowance is manipulated.

**Recommendation:** Restrict the source of transferFrom calls to only the contract's own address or explicitly authorized liquidity pools.


### `CD-04` — Unchecked Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function ignores the boolean return value of ERC-20 transfers, which may fail silently without reverting the transaction.

**Recommendation:** Always check the return value of transfer and transferFrom calls, or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Trapped ETH Funds  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function allowing it to accept ETH, but lacks any function to withdraw or transfer these funds, causing them to be permanently locked.

**Recommendation:** Implement an owner-restricted function to withdraw ETH from the contract balance.


### `CD-02` — Rounding Loss in Fee Calculations  *(Severity: Low · Status: Unresolved)*

The contract performs division before multiplication in _executeSwapAndLiquify and _transfer, leading to precision loss in fee calculations.

**Recommendation:** Perform all multiplications before divisions to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.0% of supply. Of that, 91.6% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.1% in wallets, 0.0% in other contracts. 12,509 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

12,509 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

97.0% of the pool's LP is burned or time-locked. 97.0% is locked in PinkLock02 until 16 Nov 2026 (21 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 3.0% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $387K (DexScreener, all pools). 24h trading volume $26.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4.5% on buy, 4.52% on sell. Market: $387K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2b79...cff9`](https://bscscan.com/address/0x2b79103b19d54274578aa64c3424b10e0fa1cff9) |
| **Network** | BNB Chain |
| **Price** | $11.8300 |
| **24h Volume** | $26.61M |
| **Liquidity** | $386.5K |
| **Volume / Liquidity** | 68.9× |
| **Token Age** | 17h |
| **Top-10 Holders** | 92.0% of supply |
| **Buy / Sell Tax** | 4.5% / 4.5% |
| **24h Transactions** | 4102 buys / 1418 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf609a8ab720d4dc1cedf0c91a5c784f3d4820147)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/deepseek-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
