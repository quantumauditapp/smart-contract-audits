---
token: Pi
ticker: PI
network: bsc
risk_score: 82
status: high
date: 2026-10-30
---

# Pi (PI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 82/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pi-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token with additional fee-on-transfer logic. Ownership has been renounced, meaning the privileged functions are now permanently disabled. However, the contract contains critical logic flaws in its internal swap and liquidity mechanisms that pose risks to user funds and token integrity.

> **Final Recommendation:** The contract should be considered high-risk due to the identified logic flaws in the liquidity execution path. Users should exercise extreme caution as the contract cannot be patched or upgraded to fix these issues.

It is recommended to migrate to a standard, audited ERC-20 implementation that does not include custom swap-and-liquify logic, as the current implementation fails to validate transfer results and risks trapping ETH within the contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns but implements custom fee logic. 7.1 Architecture is standard, but 7.2 Code Security is compromised by improper handling of external calls. 7.3… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are effectively neutralized as ownership is renounced. No further changes to fee exclusions or ownership can be made. The economic model relies on the flawed swap… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are static. The contract is immutable by design. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 95.9% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 4.1% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Withdrawal Risk  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom to move tokens from arbitrary addresses. This allows the contract to potentially pull tokens from any user who has previously approved the contract.

**Recommendation:** Restrict the source of tokens in transferFrom to only the contract's own balance or a controlled treasury address.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without checking the boolean return value. If a transfer fails, the contract will proceed as if it succeeded, leading to inconsistent state.

**Recommendation:** Always check the return value of ERC-20 transfers and revert if the transfer returns false.


### `CD-03` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The receive function allows the contract to accept ETH, but there are no functions implemented to withdraw or utilize these funds, effectively trapping them permanently.

**Recommendation:** Implement a withdrawal function restricted to a secure address or remove the receive function if ETH holding is not intended.


### `CD-02` — Rounding Errors due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

In _executeSwapAndLiquify and _transfer, division is performed before multiplication. This causes precision loss, which can lead to incorrect fee calculations.

**Recommendation:** Rearrange arithmetic operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.4% of supply. Of that, 90.0% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.1% in wallets, 0.0% in other contracts. 17,543 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

17,543 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

95.9% of the pool's LP is burned or time-locked. 95.9% is locked in PinkLock02 until 09 Nov 2026 (9 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 4.1% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $80K (DexScreener, all pools). 24h trading volume $6.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4% on sell. Market: $80K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4c4e...e985`](https://bscscan.com/address/0x4c4ed2786f9e4c11978dc3e5f27bb9ca98a4e985) |
| **Network** | BNB Chain |
| **Price** | $0.06076 |
| **24h Volume** | $6.90M |
| **Liquidity** | $79.9K |
| **Volume / Liquidity** | 86.4× |
| **Token Age** | 5h |
| **Top-10 Holders** | 90.4% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 7465 buys / 1148 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x422caf92ded7c1f55fd3ddd21b88c1ae51eecabe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
