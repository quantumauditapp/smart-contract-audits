---
token: bibi.ai
ticker: BIBI
network: bsc
risk_score: 82
status: high
date: 2026-10-25
---

# bibi.ai (BIBI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 82/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bibiai-bsc-f9dd)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee logic. Ownership has been renounced, meaning the privileged functions are now permanently disabled. The protocol faces significant risks due to unhandled return values and trapped ETH, though the core token transfer logic remains functional.

> **Final Recommendation:** The contract should be treated with caution due to the identified critical and high-severity issues. Since ownership is renounced, the current vulnerabilities cannot be patched by the original developers.

Users should be aware that ETH sent to the contract address is permanently locked. Future iterations should implement proper return value checking for all ERC-20 interactions and include a withdrawal function for trapped native assets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with additional fee exclusion logic. 7.1 Architecture is straightforward, but 7.2 Code Security is compromised by ignoring return values in swap… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are mitigated by the renounced ownership state. No further changes to fee structures or tokenomics can be made by any party. The economic model is static… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are fixed and immutable. The contract state is permanent, ensuring no malicious logic can be injected via upgrades. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 98.3% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 1.4% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Arbitrary Token Withdrawal  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows the movement of tokens from any address that has granted allowance to the contract, potentially leading to unauthorized token drainage.

**Recommendation:** Restrict the function to only interact with tokens owned by the contract itself.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function fails to check the boolean return value of ERC-20 transfers, which may fail silently and lead to inconsistent contract state.

**Recommendation:** Use OpenZeppelin's SafeERC20 library to ensure all transfers are verified.


### `CD-03` — Trapped Native Assets  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH but lacks any mechanism to withdraw or utilize these funds, causing them to be permanently locked.

**Recommendation:** Implement an owner-only withdrawal function to recover trapped ETH.


### `CD-02` — Rounding Errors in Fee Calculation  *(Severity: Low · Status: Unresolved)*

Division before multiplication in _executeSwapAndLiquify and _transfer causes precision loss, resulting in slightly inaccurate fee calculations.

**Recommendation:** Perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 63.2% of supply. Of that, 62.5% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 0.4% in other contracts. 14,335 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

14,335 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

98.3% of the pool's LP is burned or time-locked. 98.3% is locked in PinkLock02 until 15 Nov 2026 (20 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 1.7% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $867K (DexScreener, all pools). 24h trading volume $8.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3.9% on buy, 3.96% on sell. Market: $867K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5369...b56f`](https://bscscan.com/address/0x53692767c7aff2290636097120b9c750f0ccb56f) |
| **Network** | BNB Chain |
| **Price** | $0.1512 |
| **24h Volume** | $8.35M |
| **Liquidity** | $866.8K |
| **Volume / Liquidity** | 9.6× |
| **Token Age** | 5h |
| **Top-10 Holders** | 63.2% of supply |
| **Buy / Sell Tax** | 3.9% / 4.0% |
| **24h Transactions** | 5814 buys / 2083 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x00b595f8a0e39354b278e63cfa26de4b1b6136c4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bibiai-bsc-f9dd)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
