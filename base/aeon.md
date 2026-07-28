---
token: aeon
ticker: AEON
network: base
risk_score: 43
status: medium
date: 2026-07-28
---

# aeon (AEON) — Smart Contract Security Analysis | Base

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aeon-base)

---

## Audit Summary

The DERC20 contract implements an ERC20 token with custom vesting and inflation mechanisms. It leverages OpenZeppelin libraries for standard functionalities and access control. Key features include owner-controlled pool locking, inflation minting, and a linear vesting schedule. The contract's ownership is managed by a multisig, which enhances governance security. However, the contract is not upgradeable, posing a long-term risk for bug fixes or feature enhancements. Several denial-of-service vectors were identified.

> **Final Recommendation:** Address the identified denial of service vulnerabilities by refactoring the `mintInflation` function to calculate the total mintable amount in a single step, avoiding the unbounded `while` loop. Implement explicit gas-limiting checks or pagination for array processing in the `releaseVestedTokens` function to prevent block gas limit exhaustion. Consider implementing an upgradeability pattern, such as UUPS, to allow for future bug fixes and feature enhancements without requiring a full redeployment, which is a complex and risky operation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture is based on well-audited OpenZeppelin ERC20, ERC20Votes, ERC20Permit, and Ownable contracts, providing a solid foundation (7.1 Architecture, 7.2 Code Security). Custom… |
| **Governance / Economics** | 4/10 | Medium | The economic model includes a capped yearly inflation rate (2%), which is a transparent mechanism for token supply growth (7.4 Economic). The owner has significant control over core parameters like… |
| **Upgrades** | 7/10 | Low | The DERC20 contract is not designed with an upgradeability pattern (7.7 Upgrades). This means that once deployed, its logic cannot be modified. Any future bug fixes, security patches, or feature… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 63.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Potential Denial of Service in `mintInflation` due to Unbounded Loop  *(Severity: High · Status: Unresolved)*

The `mintInflation` function contains a `while` loop that iterates once for every full year that has passed since `currentYearStart_`. If the function is not called for an extended period (e.g., many years), this loop could iterate hundreds or thousands of times. Each iteration consumes gas, and an excessive number of iterations could cause the transaction to exceed the block gas limit, leading to a denial of service for this critical function. This prevents the owner from minting inflation tokens and updating the `currentYearStart` and `lastMintTimestamp`.

**Recommendation:** Refactor the `mintInflation` function to calculate the total mintable amount and the new `currentYearStart` in a single step, rather than iterating year by year. This can be achieved by calculating the number of full years passed and multiplying the yearly mint by that count, then handling the partial year. For example, `numYears = (block.timestamp - currentYearStart_) / 365 days;`.


### `M-01` — Potential Denial of Service in `releaseVestedTokens` due to Unbounded Array Processing  *(Severity: Medium · Status: Unresolved)*

The `releaseVestedTokens` function takes `recipients_` and `amounts_` arrays as arguments and iterates over them. If a user provides excessively large arrays, the gas cost of processing all elements could exceed the block gas limit. This would lead to a denial of service, preventing legitimate users from releasing their vested tokens if a malicious actor or an honest user accidentally triggers the gas limit with large inputs.

**Recommendation:** Implement a mechanism to limit the number of recipients that can be processed in a single transaction, or introduce pagination. Alternatively, consider a pull-based model where each user claims their own vested tokens individually, or a batching mechanism with a fixed maximum array size.


### `L-01` — Unused `tokenURI` State Variable  *(Severity: Low · Status: Unresolved)*

The `tokenURI` state variable is declared and initialized in the constructor but is not used anywhere else in the contract. There is no public getter function for it, nor does it influence any contract logic. For an ERC20 token, `tokenURI` is not a standard metadata field, typically associated with NFTs (ERC-721/1155). Its presence suggests an unclear or unimplemented purpose.

**Recommendation:** Either remove the `tokenURI` variable if it serves no purpose, or implement a public getter function and define its intended use case (e.g., linking to off-chain metadata for the token itself, if applicable).


### `I-01` — Centralized Control by Owner  *(Severity: Informational · Status: Unresolved)*

The contract utilizes OpenZeppelin's `Ownable` pattern, granting significant control over critical functions to a single address. The owner can `lockPool`, `unlockPool`, `burn` tokens, and `updateMintRate`. While the prefill data indicates the owner is a multisig (3/6 threshold), which mitigates the single point of failure, this centralization of power remains a design consideration.

**Recommendation:** Ensure the owner's private keys (or multisig signers) are secured with robust operational security practices. Regularly review the necessity and scope of owner privileges. Consider implementing a time-lock for critical operations to provide a window for community review or emergency intervention.


### `I-02` — Non-Upgradeability of Contract  *(Severity: Informational · Status: Unresolved)*

The DERC20 contract is deployed as a standard, non-upgradeable contract. This means that its logic is immutable once deployed to the blockchain. Any future bug fixes, security patches, or desired feature enhancements would require deploying an entirely new contract and migrating all existing token holders and associated data, which is a complex, costly, and potentially disruptive process.

**Recommendation:** For long-term projects, consider implementing an upgradeability pattern (e.g., UUPS or Transparent Proxy) during the design phase. This allows for future logic updates without requiring a full redeployment, providing flexibility for maintenance and evolution. If non-upgradeability is an intentional design choice, ensure all code is thoroughly audited and tested to minimize the risk of immutable vulnerabilities.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbf8e...aba3`](https://basescan.org/address/0xbf8e8f0e8866a7052f948c16508644347c57aba3) |
| **Network** | Base |
| **Price** | $0.00000552 |
| **24h Volume** | $152.8K |
| **Liquidity** | $513.5K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 47.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 414 buys / 356 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x4a9b9e13975d26f4e3e17c655593bb82145dd4452aedafb826d856b817c9cfd4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aeon-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-28*
