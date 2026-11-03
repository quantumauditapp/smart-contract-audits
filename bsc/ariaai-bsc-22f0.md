---
token: ARIA.AI
ticker: ARIA
network: bsc
risk_score: 82
status: high
date: 2026-11-03
---

# ARIA.AI (ARIA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 82/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ariaai-bsc-22f0)

---

## Audit Summary

The contract is a standard ERC-20 token with additional fee-exclusion logic. Ownership has been renounced, meaning privileged functions are now permanently disabled. However, the contract contains critical logic flaws in its internal swap and liquidity management functions that pose significant risks to token holders and contract funds.

> **Final Recommendation:** The contract should be considered unsafe for use due to the critical vulnerability allowing unauthorized token movement. Since ownership is renounced, the current contract cannot be patched; a migration to a new, audited contract is strongly advised.

Users should avoid interacting with the liquidity-related functions, as they are prone to failure and potential loss of funds. Future deployments should implement strict return value checking and ensure all ETH held by the contract can be recovered.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with added fee-exclusion mechanics. Code security is compromised by improper handling of transfer return values and unsafe arithmetic practices. 7.1… |
| **Governance / Economics** | 6/10 | Medium | Governance is effectively nullified as ownership has been renounced. 7.5 Governance is non-existent, and 7.4 Economic risks are limited to the existing contract logic. No further changes can be made… |
| **Upgrades** | 6/10 | Medium | The contract is not upgradeable. 7.7 Upgrades are not applicable as the contract is immutable. No proxy patterns are utilized. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 96.8% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 3.2% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom in a way that allows the contract to pull tokens from any address that has previously approved the contract, potentially draining user balances.

**Recommendation:** Restrict the transferFrom logic to only move tokens owned by the contract itself or implement strict access controls.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without checking the boolean return value, which can lead to silent failures where the contract assumes a transfer succeeded when it actually failed.

**Recommendation:** Always check the return value of ERC-20 transfers or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Locked ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that allows it to accept ETH, but there is no mechanism to withdraw or transfer this ETH out, effectively locking it permanently.

**Recommendation:** Implement a withdrawal function restricted to a trusted address or ensure the contract does not accept ETH.


### `CD-02` — Rounding Errors due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

In _executeSwapAndLiquify and _transfer, the code performs division before multiplication, which causes precision loss and inaccurate fee calculations.

**Recommendation:** Perform all multiplications before divisions to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.2% of supply. Of that, 90.0% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.1% in wallets, 0.0% in other contracts. 18,067 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

18,067 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

96.8% of the pool's LP is burned or time-locked. 96.8% is locked in PinkLock02 until 13 Nov 2026 (9 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 3.2% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $531K (DexScreener, all pools). 24h trading volume $8.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.3% on sell. Market: $531K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7634...846d`](https://bscscan.com/address/0x76347aac4f2bee7469cea69d996e894866e7846d) |
| **Network** | BNB Chain |
| **Price** | $0.2843 |
| **24h Volume** | $8.05M |
| **Liquidity** | $530.6K |
| **Volume / Liquidity** | 15.2× |
| **Token Age** | 5h |
| **Top-10 Holders** | 90.2% of supply |
| **Buy / Sell Tax** | 4.0% / 4.3% |
| **24h Transactions** | 9520 buys / 1171 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x739e28b29eea08d01edfadcbb08d4cb07c78a2bf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ariaai-bsc-22f0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
