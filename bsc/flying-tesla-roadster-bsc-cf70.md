---
token: Flying Tesla Roadster
ticker: FTR
network: bsc
risk_score: 76
status: high
date: 2026-10-26
---

# Flying Tesla Roadster (FTR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flying-tesla-roadster-bsc-cf70)

---

## Audit Summary

The contract is a standard ERC-20 implementation with custom fee logic. Ownership has been renounced, meaning the privileged functions for fee management are now permanently disabled. The audit identified critical issues regarding token movement and lack of ETH withdrawal mechanisms.

> **Final Recommendation:** Immediate action is required to address the critical token movement vulnerability. Since ownership is renounced, the contract cannot be patched; users should be advised of the risks associated with the current implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with additional fee-on-transfer logic. 7.1 Architecture and 7.2 Code Security are compromised by improper handling of external calls. 7.6 External… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are mitigated by the renounced ownership status. No further changes can be made to fee exclusions or contract parameters. The economic model is static and cannot… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable. 7.8 Operations are limited to standard token transfers. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 95.0% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 4.9% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom to move tokens from arbitrary addresses, potentially allowing unauthorized drainage of user funds.

**Recommendation:** Restrict the source address in transferFrom to only the contract itself or authorized liquidity pools.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The contract ignores the boolean return value of ERC-20 transfers in _executeSwapAndLiquify, which can lead to silent failures where tokens are not moved but the state updates as if they were.

**Recommendation:** Always check the return value of transfer and transferFrom calls using a library like SafeERC20.


### `CD-03` — Locked ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function allowing it to accept ETH, but provides no mechanism for the owner or any other party to withdraw these funds.

**Recommendation:** Implement a withdrawal function to allow the recovery of accidentally sent ETH.


### `CD-02` — Rounding Errors due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

Calculations in _executeSwapAndLiquify and _transfer perform division before multiplication, leading to precision loss.

**Recommendation:** Rearrange arithmetic operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 20.7% of supply. Of that, 19.4% burned, 0.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.7% in wallets, 0.0% in other contracts. 14,571 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

14,571 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

95.0% of the pool's LP is burned or time-locked. 95.0% is locked in PinkLock02 until 28 Nov 2026 (32 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 5.0% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $243K (DexScreener, all pools). 24h trading volume $64.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4.5% on buy, 4.54% on sell. Market: $243K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x23ce...e514`](https://bscscan.com/address/0x23ce28d7d9f642bb544ac0ac521bb441a2b1e514) |
| **Network** | BNB Chain |
| **Price** | $5.9300 |
| **24h Volume** | $64.10M |
| **Liquidity** | $242.9K |
| **Volume / Liquidity** | 263.9× |
| **Token Age** | 22h |
| **Top-10 Holders** | 20.7% of supply |
| **Buy / Sell Tax** | 4.5% / 4.5% |
| **24h Transactions** | 16298 buys / 3669 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x380be47efb656c500bb29c0c8c6f91a8efa19dd8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flying-tesla-roadster-bsc-cf70)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
