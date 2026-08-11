---
token: Sapien
ticker: SAPIEN
network: base
risk_score: 33
status: medium
date: 2026-08-11
---

# Sapien (SAPIEN) — Smart Contract Security Analysis | Base

> **Risk Score: 33/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sapien-base)

---

## Audit Summary

The SapienToken contract is a standard ERC-20 token with EIP-2612 Permit functionality, built upon well-audited OpenZeppelin libraries. The contract's technical implementation is robust, demonstrating good security practices against common vulnerabilities like reentrancy and integer overflows. The primary area of concern is the economic model's initial token distribution, where the entire supply is minted to a single treasury address, introducing a centralization risk.

> **Final Recommendation:** Implement robust security measures for the `treasury` address, such as a multi-signature wallet, to mitigate the centralization risk associated with the initial token distribution. Educate users about the inherent front-running risks when utilizing the `permit` function. For future development, consider defining custom errors explicitly for improved gas efficiency and clarity, and align compiler pragmas across all contract files for consistency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1 Architecture) of SapienToken is sound, leveraging battle-tested OpenZeppelin contracts for ERC-20 and ERC-20 Permit functionalities. The code (7.2 Code Security)… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4 Economic) of SapienToken involves minting the entire `MAX_SUPPLY` to a single `treasury` address during deployment. This creates a significant centralization risk (7.3 Access… |
| **Upgrades** | 6/10 | Medium | The SapienToken contract is implemented as a standard, non-upgradable ERC-20 token. It does not utilize any proxy patterns (7.7 Upgrades) or upgradeability mechanisms. This design choice simplifies… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 42.1% |
| **Top-3 Unlocked** | 74.1% |

## Security Findings

_🟡 1 Medium · ⚪ 3 Informational_

### `M-01` — Centralization Risk from Initial Token Distribution  *(Severity: Medium · Status: Unresolved)*

The `SapienToken` contract mints its entire `MAX_SUPPLY` (1,000,000,000 SAPIEN tokens) to a single `treasury` address during deployment. This means 100% of the token supply is controlled by one address. This poses a significant centralization risk (7.4 Economic, 7.3 Access Control). If this `treasury` address is compromised, or if the entity controlling it acts maliciously, the entire token supply could be dumped onto the market, severely impacting liquidity and token price.

**Recommendation:** While this distribution model might be intentional for initial bootstrapping, it's crucial to implement robust security measures for the `treasury` address (e.g., multi-signature wallet, cold storage). Consider a phased distribution or vesting schedule for the tokens to mitigate the immediate impact of a potential compromise or single point of failure.


### `I-01` — Front-Running Risk in ERC-20 Permit Function  *(Severity: Informational · Status: Unresolved)*

The `SapienToken` contract implements the `ERC20Permit` (EIP-2612) standard, which allows users to approve token transfers via a signed message rather than an on-chain transaction. While correctly implemented using OpenZeppelin's robust `ERC20Permit` and `Nonces` (7.2 Code Security), the `permit` function is inherently susceptible to front-running (7.6 External). If a user's signed `permit` message is broadcasted to the mempool, a malicious actor could observe it and submit their own transaction with a higher gas price to execute the `permit` call first, potentially exploiting the approval before the legitimate user's intended transaction.

**Recommendation:** Users should be aware of the front-running risks associated with `permit` signatures. They should only broadcast `permit` signatures when confident in the transaction's execution and consider using privacy-preserving transaction methods if available. The contract itself correctly implements the standard, so no code changes are required.


### `I-02` — Undefined Custom Error `ZeroAddress`  *(Severity: Informational · Status: Unresolved)*

In the `SapienToken` constructor, the contract reverts with `revert ZeroAddress();` if the `treasury` address is `address(0)`. However, the `ZeroAddress` error is not explicitly defined using `error ZeroAddress();` within the contract or an imported interface (7.2 Code Security). While the revert functionality works, defining custom errors is a best practice in Solidity 0.8.x as it provides more gas-efficient and descriptive error messages compared to string reverts.

**Recommendation:** Define `error ZeroAddress();` within the `SapienToken` contract or a dedicated errors interface to ensure proper custom error handling and optimize gas usage for this specific revert condition.


### `I-03` — Inconsistent Compiler Pragmas Across Dependencies  *(Severity: Informational · Status: Unresolved)*

The `SapienToken` contract specifies `pragma solidity 0.8.30;`, while its OpenZeppelin dependencies (e.g., `ERC20.sol`, `ERC20Permit.sol`) use `pragma solidity ^0.8.20;` (7.2 Code Security, 7.8 Operations). While `0.8.30` is compatible with `^0.8.20`, it's generally a best practice to align all pragma versions to the exact compiler version used for deployment. This ensures consistent compilation behavior across all files and reduces potential for unexpected issues with future compiler updates or specific version-dependent optimizations.

**Recommendation:** Consider aligning all `pragma solidity` statements to the specific compiler version intended for deployment (e.g., `pragma solidity 0.8.30;` for all files). This practice enhances build reproducibility and clarity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc729...14e3`](https://basescan.org/address/0xc729777d0470f30612b1564fd96e8dd26f5814e3) |
| **Network** | Base |
| **Price** | $0.08255 |
| **24h Volume** | $111.8K |
| **Liquidity** | $852.0K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 90.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 402 buys / 572 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x80cc08712aa61ce9dc7604f9ce7560a25094b862)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sapien-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
