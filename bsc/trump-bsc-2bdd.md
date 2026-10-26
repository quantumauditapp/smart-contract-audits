---
token: Trump
ticker: TRUMP
network: bsc
risk_score: 84
status: high
date: 2026-10-26
---

# Trump (TRUMP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trump-bsc-2bdd)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee-exclusion logic. Ownership has been renounced, meaning the privileged functions setTrailblazers, transferOwnership, and renounceOwnership are now dormant and cannot be invoked. The contract contains critical logic flaws regarding token transfers and fund management that persist despite the renounced ownership.

> **Final Recommendation:** The contract is currently in a state where critical vulnerabilities cannot be patched due to renounced ownership. Users should be aware that the contract contains logic that can lead to loss of funds during swap operations and that any ETH sent to the contract is permanently locked.

Future deployments should implement robust return value checking for all ERC-20 interactions and ensure that any contract designed to receive ETH includes a withdrawal mechanism. Given the current state, the contract should be considered high-risk for any integration involving automated liquidity swaps.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns but introduces custom logic in _executeSwapAndLiquify. 7.1 Architecture is standard, while 7.2 Code Security reveals critical flaws in transfer… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are currently neutralized because ownership is renounced. No further changes to fee-exclusion lists or ownership can be made. The economic model is static and… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to standard token transfers. The contract is immutable. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 97.3% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 2.7% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows for the movement of tokens from arbitrary addresses using transferFrom, potentially allowing unauthorized parties to drain tokens if approvals are present.

**Recommendation:** Restrict the caller of the swap function to authorized internal logic or ensure the swap mechanism only interacts with contract-owned tokens.


### `CD-04` — Unchecked Token Transfer Result  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without verifying the boolean return value, which can lead to silent failures in the liquidity swap process.

**Recommendation:** Always check the return value of transfer and transferFrom calls or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Trapped ETH Funds  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH via the receive function but lacks any mechanism to withdraw or utilize these funds, causing them to be permanently locked.

**Recommendation:** Implement a withdrawal function restricted to an owner or a governance contract to recover trapped ETH.


### `CD-02` — Rounding Errors via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

In _executeSwapAndLiquify and _transfer, division is performed before multiplication, which leads to precision loss and incorrect fee calculations.

**Recommendation:** Reorder operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.8% of supply. Of that, 90.0% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.5% in wallets, 0.0% in other contracts. 17,772 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

17,772 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

97.3% of the pool's LP is burned or time-locked. 97.3% is locked in PinkLock02 until 05 Nov 2026 (9 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 2.7% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $62K (DexScreener, all pools). 24h trading volume $4.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.02% on sell. Market: $62K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2120...20ff`](https://bscscan.com/address/0x2120b160887c60801da2361d445847d6f9ec20ff) |
| **Network** | BNB Chain |
| **Price** | $0.4046 |
| **24h Volume** | $4.82M |
| **Liquidity** | $62.1K |
| **Volume / Liquidity** | 77.6× |
| **Token Age** | 9h |
| **Top-10 Holders** | 90.8% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 7727 buys / 1487 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x7c3ee87a90eb4af9539c952f1bb96168e9196e0d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trump-bsc-2bdd)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
