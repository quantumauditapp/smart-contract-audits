---
token: ShopinX Token
ticker: SPX
network: bsc
risk_score: 66
status: high
date: 2026-09-03
---

# ShopinX Token (SPX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/shopinx-token-bsc)

---

## Audit Summary

The ShopinX Token contract implements an ERC20 token with custom locking and vesting functionalities. The contract utilizes OpenZeppelin's battle-tested libraries and `Ownable2Step` for enhanced ownership management. However, the audit identified a critical vulnerability related to the owner's ability to indefinitely freeze user funds, alongside other medium and low-severity issues concerning permanent owner control and vesting calculation precision. These findings highlight significant centralization risks and potential for fund access issues.

> **Final Recommendation:** It is strongly recommended to address the critical vulnerability allowing indefinite freezing of funds. This could involve implementing a maximum cumulative lock duration or requiring user consent for freezing existing balances. The permanent owner role should also be reconsidered; if decentralization is a future goal, a mechanism for transferring ownership to a multisig or DAO should be explored. Finally, review the vesting calculation for precision and ensure `uint128` casting for vesting amounts cannot lead to unexpected truncations under any foreseeable circumstances.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract is built upon robust OpenZeppelin ERC20 standards, including `ERC20Burnable` and `ERC20Permit`, and uses Solidity 0.8.27, benefiting from checked arithmetic. The `_update` override… |
| **Governance / Economics** | 3/10 | High | The token has a fixed `INITIAL_SUPPLY` and no further minting capabilities, which is a positive economic control (7.4 Economic). The `Ownable2Step` pattern enhances security for ownership transfers… |
| **Upgrades** | 6/10 | Medium | This contract is not designed as an upgradeable proxy. Therefore, traditional upgrade safety concerns (7.7 Upgrades) related to proxy patterns are not applicable. Any changes to the contract's logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 88.3% — TeamFinance |
| **Top-1 Unlocked Holder** | 5.2% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 2 Low_

### `C-01` — Owner Can Indefinitely Freeze User Funds  *(Severity: Critical · Status: Unresolved)*

The `setLock` function, callable by the contract owner, allows freezing an account's tokens for a duration up to `MAX_LOCK_DURATION` (4 years). While a single call is limited, the owner can repeatedly call `setLock` just before the existing lock expires, effectively freezing an account's entire token balance indefinitely. This grants the owner unilateral power to prevent users from accessing their funds, posing a severe centralization risk and potential for denial of service.

**Recommendation:** Implement a mechanism to prevent indefinite freezing. Options include: 1) A global maximum cumulative lock duration for any single account. 2) Requiring explicit consent from the account holder to freeze their existing balance. 3) Limiting `setLock` only to tokens transferred by the owner, not existing user balances. 4) Transitioning ownership to a multi-signature wallet or DAO with strict governance rules for such powerful functions.


### `M-01` — Permanent Owner Role  *(Severity: Medium · Status: Unresolved)*

The `renounceOwnership` function is explicitly overridden to revert, preventing the contract owner from relinquishing their administrative privileges. This design choice establishes a permanent single point of control, increasing the centralization risk. If the owner's private key is compromised or the owner becomes malicious, there is no on-chain mechanism to remove their control over critical functions like `setLock`, `removeLock`, `transferWithLock`, and `transferWithVesting`.

**Recommendation:** Consider allowing ownership to be renounced or transferred to a more decentralized entity, such as a multi-signature wallet or a DAO. If a permanent owner is intended, ensure robust security measures are in place for the owner's private key and consider a time-locked transfer mechanism for ownership changes.


### `L-01` — Vesting Calculation Precision Loss  *(Severity: Low · Status: Unresolved)*

The `vestedAmount` function uses integer division in its calculations, particularly for `vestedFromCurrent`. When `v.totalAmount` or `v.stepPercent` are small, or `PERCENT_BASE * stepSeconds` is large, integer division can truncate fractional results to zero. This may lead to minor precision loss, causing users to receive slightly less than their mathematically precise vested amount, especially for small token values or very granular vesting schedules.

**Recommendation:** While often acceptable for minor discrepancies, consider using a fixed-point math library or adjusting the calculation order to minimize precision loss. For example, multiply before dividing where possible, or ensure intermediate values are large enough to retain precision before final division. Clearly document this behavior if no changes are made.


### `L-02` — Potential Truncation in Vesting `totalAmount`  *(Severity: Low · Status: Unresolved)*

The `totalAmount` field within the `VestingInfo` struct is defined as `uint128`, and the `amount` parameter in `transferWithVesting` is explicitly cast to `uint128`. While the current `INITIAL_SUPPLY` (10^27) fits within `uint128` (max ~3.4 x 10^38), if future vesting amounts were to exceed `type(uint128).max`, the value would be silently truncated without a revert. This could lead to a loss of funds or incorrect vesting schedules if very large amounts are ever intended for vesting.

**Recommendation:** If there's any possibility of vesting amounts exceeding `uint128` maximum, consider changing `VestingInfo.totalAmount` to `uint256` to prevent potential truncation. Alternatively, add a `require(amount <= type(uint128).max, 'Amount too large for vesting')` check in `transferWithVesting` to explicitly prevent such an overflow.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xca56...3827`](https://bscscan.com/address/0xca56094722450016f280c4fd6a333e5c36903827) |
| **Network** | BNB Chain |
| **Price** | $0.05732 |
| **24h Volume** | $985.2K |
| **Liquidity** | $135.5K |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 77.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3720 buys / 3654 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xe2561a789e8d94f3f9b620aaecc627e1e205fe8b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/shopinx-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
