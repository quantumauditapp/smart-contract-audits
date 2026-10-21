---
token: Frankencoin
ticker: ZCHF
network: ethereum
risk_score: 81
status: high
date: 2026-09-05
---

# Frankencoin (ZCHF) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/frankencoin-eth)

---

## Audit Summary

The audit of the Frankencoin protocol identified a critical logic error in the `isMinter` function, which inverts minter validity and prevents core functionality. A high-severity access control flaw in the `initialize` function allows for front-running. Additionally, potential division by zero, reliance on an unaudited external governance contract, and economic design considerations were noted. The protocol's core functionality is significantly impacted by the critical bug.

> **Final Recommendation:** Prioritize immediate resolution of the critical `isMinter` logic error and the `initialize` function's access control vulnerability to ensure the protocol's fundamental operations are secure and functional. Conduct a thorough review of all mathematical operations, especially those involving division, to prevent potential reverts. Furthermore, a comprehensive audit of the `Equity` contract, particularly its `checkQualified` function, is essential to understand and mitigate the risks associated with its governance dependency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The technical architecture is generally sound, leveraging ERC20PermitLight and custom reserve mechanics. However, a critical logic error in the `isMinter` function (7.2 Code Security) inverts minter… |
| **Governance / Economics** | 1/10 | High | The Frankencoin protocol incorporates a reserve mechanism and a system for minter management, including the ability to mint ZCHF to cover losses (7.4 Economic). The `denyMinter` function relies on an… |
| **Upgrades** | 2/10 | High | The Frankencoin contract is not designed with an upgradeability mechanism (7.7 Upgrades). It is deployed as a standard, non-proxy contract, meaning its logic cannot be changed post-deployment. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Inverted Minter Validity Logic  *(Severity: Critical · Status: Unresolved)*

The `isMinter` function, which controls access to critical minter-only functions, uses the condition `block.timestamp >= minters[_minter]`. However, `minters[_minter]` is set to `block.timestamp + _applicationPeriod` in `suggestMinter` (and `block.timestamp` in `initialize`), indicating it stores the *end* timestamp of the validity period. This means a minter is only considered valid *after* their application period has expired, effectively preventing them from performing minter actions during their intended active period. This renders the core minter functionality unusable. (7.2 Code Security)

**Recommendation:** Change the condition in `isMinter` to `block.timestamp < minters[_minter]` to correctly reflect that a minter is valid *during* their application period. Ensure this change is thoroughly tested.


### `H-01` — Centralized Initialization Vulnerability  *(Severity: High · Status: Unresolved)*

The `initialize` function, which sets the initial minter, lacks access control and can be called by any address as long as `totalSupply()` and `reserve.totalSupply()` are zero. This creates a front-running vulnerability where an attacker could call `initialize` before the legitimate deployer, setting themselves as the initial minter and gaining unauthorized control over the protocol's initial state. (7.3 Access Control)

**Recommendation:** Implement an `onlyOwner` or similar access control mechanism for the `initialize` function, ensuring only the intended deployer can call it. Alternatively, consider setting the initial minter directly in the constructor if possible.


### `M-01` — Potential Division by Zero in `calculateFreedAmount`  *(Severity: Medium · Status: Unresolved)*

The `calculateFreedAmount` function includes a division by `(1000000 - adjustedReservePPM)`. If `adjustedReservePPM` were to equal `1000000` (e.g., if `reservePPM` is set to 1,000,000 and `currentReserve >= minterReserve_`), this would result in a division-by-zero error, causing transactions to revert. While PPM (parts per million) typically implies values less than 1,000,000, there's no explicit upper bound check for `reservePPM` or `adjustedReservePPM` to prevent this. (7.2 Code Security)

**Recommendation:** Add a check to ensure `adjustedReservePPM` is strictly less than `1000000` before performing the division, or handle the edge case where it equals `1000000` gracefully (e.g., by reverting with a specific error or returning a maximum value).


### `M-02` — Undefined External Governance Dependency  *(Severity: Medium · Status: Unresolved)*

The `denyMinter` function critically relies on `reserve.checkQualified(msg.sender, _helpers)`. The implementation of `checkQualified` within the `Equity` contract (acting as the reserve) is not provided in the audited code. This creates an opaque dependency on an external contract's logic, specifically its governance or access control mechanisms. The security and decentralization of the `Frankencoin` protocol are thus directly tied to the (unseen) implementation of `Equity.checkQualified`. (7.6 External, 7.5 Governance)

**Recommendation:** Provide the full source code for the `Equity` contract, especially the `checkQualified` function, for a complete security assessment. Clearly document the expected behavior and access control of this external dependency.


### `L-01` — Minter Application Fee in ZCHF  *(Severity: Low · Status: Unresolved)*

The `suggestMinter` function requires applicants to pay an `_applicationFee` in ZCHF, which is transferred to the reserve via `_collectProfits`. This design choice means that prospective minters must first acquire ZCHF to apply, potentially creating a barrier to entry or requiring an initial distribution mechanism for the token. (7.4 Economic)

**Recommendation:** Document this economic design choice clearly. Consider if alternative fee mechanisms (e.g., in a base currency like ETH or stablecoins) might be more suitable for initial bootstrapping or broader accessibility, depending on the project's goals.


### `I-01` — Unlimited Allowance for Privileged Roles  *(Severity: Informational · Status: Unresolved)*

The custom `_allowance` function grants an `INFINITY` allowance to minters, their registered position parents, and the `reserve` contract. While this simplifies operations for these trusted entities by removing the need for repeated approvals, it also means that a compromise of a minter's private key or a vulnerability in the `reserve` contract could lead to unlimited spending of their ZCHF balance. (7.3 Access Control)

**Recommendation:** Acknowledge this design decision and ensure that robust security practices are in place for managing minter keys and the `reserve` contract. Consider if a configurable, high but not infinite, allowance might offer a better balance of convenience and security for minters, or if specific allowances for specific operations could be implemented.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb58e...21cb`](https://etherscan.io/address/0xb58e61c3098d85632df34eecfb899a1ed80921cb) |
| **Network** | Ethereum |
| **Price** | $1.2300 |
| **24h Volume** | $151.5K |
| **Liquidity** | $1.41M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 90.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 144 buys / 88 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x8e4318e2cb1ae291254b187001a59a1f8ac78cef)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/frankencoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-05*
