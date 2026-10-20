---
token: Trump
ticker: TRUMP
network: bsc
risk_score: 83
status: high
date: 2026-10-20
---

# Trump (TRUMP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 83/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trump-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee logic. Ownership has been renounced, meaning the privileged functions for fee management are now permanently disabled. The contract contains critical logic flaws in its internal swap mechanism that could lead to unauthorized token movement and loss of funds.

> **Final Recommendation:** The contract should be redeployed with a corrected swap mechanism that validates all ERC-20 transfer return values and ensures arithmetic safety. The current implementation is unsafe for production use due to the identified critical and high-severity vulnerabilities.

Users should exercise extreme caution as the current contract allows for potential unauthorized token movement and traps ETH within the contract balance without a recovery mechanism.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns but introduces custom swap logic that is poorly implemented. 7.1 Architecture is standard, but 7.2 Code Security is compromised by unchecked return… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance risks are currently static because the contract owner has renounced control. 7.6 External dependencies are limited to standard OpenZeppelin libraries. No further… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as this is a standard non-proxy contract. 7.8 Operations are fixed and immutable. No upgrade path exists for the current implementation. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 94.1% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 5.8% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom to move tokens from arbitrary addresses, potentially allowing unauthorized parties to drain tokens from users who have approved the contract.

**Recommendation:** Restrict the source of funds in _executeSwapAndLiquify to the contract's own balance rather than arbitrary user addresses.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without checking the boolean return value, which can lead to silent failures and inconsistent state.

**Recommendation:** Always check the return value of ERC-20 transfers or use the SafeERC20 library.


### `CD-03` — Locked ETH Funds  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but there is no logic to withdraw or utilize these funds, effectively locking them in the contract forever.

**Recommendation:** Implement a withdrawal function restricted to a secure address or remove the receive function if not required.


### `CD-02` — Rounding Errors due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

Calculations in _executeSwapAndLiquify and _transfer perform division before multiplication, leading to precision loss.

**Recommendation:** Rearrange arithmetic operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 88.0% of supply. Of that, 78.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.0% in wallets, 0.7% in other contracts. 60,336 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

60,336 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

94.1% of the pool's LP is burned or time-locked. 94.1% is locked in PinkLock02 until 05 Nov 2026 (15 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 5.9% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $22.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.01% on sell. Market: $11K of DEX liquidity across 1 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4cfa...573b`](https://bscscan.com/address/0x4cfaccd32b9ec2f1e5680f63bae2ff198c4f573b) |
| **Network** | BNB Chain |
| **Price** | $0.007184 |
| **24h Volume** | $22.44M |
| **Liquidity** | $11.3K |
| **Volume / Liquidity** | 1994.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | 88.0% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 12862 buys / 1779 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa7ae6a2c7cc9104870f764dfea6b74f215c20989)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trump-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
