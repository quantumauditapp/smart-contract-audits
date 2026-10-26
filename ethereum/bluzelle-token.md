---
token: Bluzelle Token
ticker: BLZ
network: ethereum
risk_score: 51
status: medium
date: 2026-09-05
---

# Bluzelle Token (BLZ) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bluzelle-token-eth)

---

## Audit Summary

The Bluzelle Token contract implements a standard ERC-20 token with additional access control mechanisms and a finalization state. Key features include a two-step ownership transfer, an operational address, and a pre-finalization phase where token transfers are restricted to owner/ops. The contract utilizes a custom SafeMath library for arithmetic operations. While the core ERC-20 functionality is present, the audit identified several areas for improvement, including the use of an outdated Solidity compiler, significant centralization risk before finalization, and standard ERC-20 vulnerabilities like the `approve()` race condition. The contract's design provides robust access control post-finalization but introduces high centralization risk during its initial phase.

> **Final Recommendation:** It is strongly recommended to migrate the contract to a modern Solidity compiler version (e.g., 0.8.x) to benefit from enhanced security features, gas optimizations, and bug fixes. This migration should be accompanied by a thorough re-audit. Address the centralization risk during the pre-finalization phase by clearly communicating this operational model to users and considering multi-signature wallets for owner/ops addresses. Implement `increaseAllowance()` and `decreaseAllowance()` functions to mitigate the `approve()` race condition and enhance user safety.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical implementation (7.2 Code Security) benefits from a custom `Math` library to prevent integer overflows/underflows, which is a strong security practice for arithmetic operations. The… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a high degree of centralization (7.3 Access Control, 7.4 Economic) during its initial, non-finalized phase. Before `finalize()` is called, only the owner or ops address can… |
| **Upgrades** | 7/10 | Low | This contract is not designed as an upgradeable proxy (7.7 Upgrades), so traditional upgrade safety concerns do not apply. However, the `finalized` state acts as a one-way, irreversible state… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 90.5% |
| **Top-3 Unlocked** | ⚠️ 99.1% |

## Security Findings

_🟡 5 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — ERC-20 `approve()` Race Condition Vulnerability  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard ERC-20 `approve()` function is susceptible to a known front-running attack. If a user increases an allowance for a spender, an attacker can front-run the transaction, spend the original allowance, and then the user's new allowance transaction will grant the attacker an additional allowance, effectively doubling the intended allowance. This can lead to unintended token loss if not handled carefully by users.

**Recommendation:** Advise users to always set an allowance to zero before increasing it. Alternatively, implement `increaseAllowance()` and `decreaseAllowance()` functions, which are safer alternatives to directly setting allowances and mitigate this race condition.


### `M-02` — Missing Zero-Address Check in `approve()`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `approve` function allows setting an allowance for `address(0)`. While not directly exploitable for token theft, approving the zero address could lead to tokens being permanently inaccessible by the intended spender if this address is used by mistake, as `address(0)` cannot execute transactions. This could result in a loss of functionality or perceived token loss.

**Recommendation:** Add a `require(_spender != address(0))` check within the `approve` function to prevent accidental approval of the zero address.


### `M-03` — Unprotected Division in `Math.div()`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Math` library's `div` function does not include a check to prevent division by zero. Although this specific `div` function is not directly called in the token's core logic in a way that would immediately cause a critical issue (it's used in `mul` for a check), it represents an incomplete safe math implementation and could lead to runtime errors if used elsewhere or if the `mul` check logic changes.

**Recommendation:** Add a `require(b != 0)` check at the beginning of the `div` function in the `Math` library to ensure robust safe math operations.


### `M-04` — Outdated Solidity Compiler Version  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses Solidity `^0.4.18`, which is an extremely old version. Newer compiler versions (e.g., 0.8.x) include critical bug fixes, security enhancements (like default overflow/underflow checks), and gas optimizations that are absent in older versions. Using an outdated compiler increases the risk of undiscovered vulnerabilities and makes the code harder to maintain and integrate with modern tooling.

**Recommendation:** Upgrade the Solidity compiler version to a recent stable release (e.g., 0.8.x). This will require careful testing and potentially minor code adjustments to ensure compatibility and leverage new features. A full re-audit should be performed after the upgrade.


### `M-05` — Centralized Control Over Transfers Before Finalization  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `validateTransfer` function, active before the `finalize()` function is called, restricts all token transfers such that only the `owner` or `opsAddress` can initiate transfers, unless the recipient is the `owner`. This grants significant centralized control over token movement, posing a high risk if the owner's or ops address's private key is compromised or if the owner acts maliciously. This central point of control could lead to a denial of service for token holders or unauthorized censorship of transfers.

**Recommendation:** Clearly document this centralized control phase and its implications for token holders. Consider implementing a multi-signature wallet for the `owner` and `opsAddress` to distribute control and reduce the risk of a single point of failure. Ensure a robust process for the `finalize()` call to transition to a decentralized transfer state.


### `L-01` — Lack of `increaseAllowance()` and `decreaseAllowance()`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract implements the basic `approve()` function but lacks the safer `increaseAllowance()` and `decreaseAllowance()` functions. These functions are considered best practice in modern ERC-20 implementations as they allow atomic adjustments to allowances, reducing the risk associated with the `approve()` race condition.

**Recommendation:** Consider adding `increaseAllowance()` and `decreaseAllowance()` functions to provide a safer and more user-friendly way to manage token allowances.


### `L-02` — Owner Can Reclaim All Contract-Held Tokens  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `reclaimTokens()` function allows the contract owner to transfer all tokens held by the `BluzelleToken` contract itself to the owner's address. While potentially intended for recovery or specific operational needs, this function could be misused if the contract is ever intended to hold tokens for other purposes (e.g., as part of a liquidity pool or escrow), leading to a loss of funds for those purposes.

**Recommendation:** Ensure that the purpose and implications of the `reclaimTokens` function are clearly documented. If the contract is intended to hold tokens for specific functionalities, consider removing or restricting this function, or implementing a more granular withdrawal mechanism.


### `I-01` — Redundant Check in `cancelOwnershipTransfer()`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `cancelOwnershipTransfer()` function includes an `if (proposedOwner == address(0))` check before setting `proposedOwner = address(0)`. This check is redundant as the variable is set to `address(0)` regardless, adding unnecessary complexity without functional benefit.

**Recommendation:** Remove the `if (proposedOwner == address(0))` condition, as `proposedOwner = address(0)` can be executed unconditionally.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5732...d668`](https://etherscan.io/address/0x5732046a883704404f284ce41ffadd5b007fd668) |
| **Network** | Ethereum |
| **Price** | $0.01234 |
| **24h Volume** | $225.5K |
| **Liquidity** | $208.0K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 6y |
| **Top-10 Holders** | 75.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 411 buys / 409 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x5fa9569b0ed6aa01e234468e6a15b77988b950df)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bluzelle-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-05*
