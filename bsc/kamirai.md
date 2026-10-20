---
token: Kamirai
ticker: $KAMIRAI
network: bsc
risk_score: 52
status: medium
date: 2026-10-04
---

# Kamirai ($KAMIRAI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kamirai-bsc)

---

## Audit Summary

The KamiraiToken contract is an ERC-20 compliant token with additional features for transfer control, including burning and anti-bot mechanisms. Ownership of the contract has been renounced on-chain, meaning that the previously privileged functions (e.g., `setBurningEnabled`, `setAntiBot`, `setTaxExclusion`) can no longer be called by anyone, rendering these controls dormant. Key findings include a high-severity issue related to shadowing state (details not fully provided), a medium-severity issue where received ETH cannot be withdrawn (7.8 Operations), and informational findings regarding the now-dormant administrative controls over transfer rules (7.3 Access Control, 7.4 Economic).

> **Final Recommendation:** It is crucial to address the high-severity 'shadowing state' issue by thoroughly reviewing the contract's inheritance structure and variable declarations to ensure unique naming and prevent unintended behavior. The medium-severity issue of locked ETH should be resolved by either removing the `receive` function if ETH is not intended to be held, or by implementing a secure withdrawal mechanism. While the renounced ownership mitigates risks associated with centralized control over economic parameters, it also means these features cannot be adjusted if future operational needs arise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The KamiraiToken contract implements the ERC-20 standard, including `transfer` and `transferFrom` functions that utilize an internal `_transferWithTax` mechanism (7.1 Architecture). A high-severity… |
| **Governance / Economics** | 7/10 | Low | The contract included several economic control mechanisms, such as `setBurningEnabled` to toggle token burning and `setAntiBot` to manage anti-bot measures with a time limit (`antiBotEndTime`) (7.4… |
| **Upgrades** | 8/10 | Low | The KamiraiToken contract is a standard implementation contract and does not utilize any proxy patterns or upgrade mechanisms (7.7 Upgrades). Therefore, its logic cannot be changed or updated after… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 61.6% — UNCX Locker |
| **Top-1 Unlocked Holder** | 38.4% |
| **Top-3 Unlocked** | 38.4% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 6 Informational_

### `CD-02` — Shadowing State Vulnerability  *(Severity: High · Status: Unresolved)*

The specific details regarding the shadowing state vulnerability are not provided in the audit input. Generally, shadowing state occurs when a variable in a derived contract has the same name as a variable in a base contract, potentially leading to unexpected behavior or incorrect state management, as the compiler might use a different variable than intended during execution.

**Recommendation:** Review the full source code to identify any shadowed state variables. Ensure that all state variables have unique names across the inheritance hierarchy to prevent ambiguity and unintended interactions, which could lead to critical security flaws or incorrect contract logic.


### `CD-01` — Ether Can Be Sent To Contract But Not Withdrawn  *(Severity: Medium · Status: Unresolved)*

The contract has a `receive` function, which allows it to accept Ether (ETH) sent to its address. However, there are no functions implemented in the contract that would allow any address, including the former owner, to withdraw this received ETH. Any ETH sent to this contract will be permanently locked and inaccessible.

**Recommendation:** If the contract is not intended to hold ETH, consider removing the `receive` function to prevent accidental transfers. If ETH is intended to be held, implement a secure withdrawal function, preferably restricted to a trusted address, to manage these funds.


### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

61.6% of the pool's LP is burned or time-locked. 61.6% is held by UNCX Locker, but the lock's end date is not published in the data we can read — its duration is unverified. 38.4% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 62% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-05` — Dormant Control Over Token Burning  *(Severity: Informational · Status: Unresolved)*

The contract includes a `setBurningEnabled` function that, if active, would allow a privileged address to turn on or off the ability for tokens to be burned. This setting directly affects whether certain token transfers or sales would be allowed or refused. However, the contract's ownership has been renounced, meaning no one can call this function anymore. This control is now permanently inactive.

**Recommendation:** No action is required as ownership is renounced, rendering this function permanently inactive. This finding serves as documentation of a past control mechanism.


### `CP-08` — Dormant Control Over Anti-Bot Measures  *(Severity: Informational · Status: Unresolved)*

The contract contains a `setAntiBot` function that, if active, would allow a privileged address to enable or disable anti-bot measures and set their duration (`antiBotEndTime`). These measures could impose limits on transfers or wallet sizes. However, the contract's ownership has been renounced, meaning no one can call this function anymore. This control is now permanently inactive.

**Recommendation:** No action is required as ownership is renounced, rendering this function permanently inactive. This finding serves as documentation of a past control mechanism.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 61.9% of supply. Of that, 46.9% burned, 0.9% locked — not holders that can sell, so excluded from the concentration score. What remains: 3.3% in wallets, 10.8% in other contracts. 16,524 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

16,524 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $58K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 3 pools. Launch: 126 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x12bf...a213`](https://bscscan.com/address/0x12bfe0251eb64c6e26d1a264673593d6164ca213) |
| **Network** | BNB Chain |
| **Price** | $0.00001106 |
| **24h Volume** | $38.4K |
| **Liquidity** | $20.0K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 61.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 194 buys / 173 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x23cddc4e17a12bf61267681004da275be6b87dfa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kamirai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
